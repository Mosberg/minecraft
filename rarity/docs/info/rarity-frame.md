# To render a rarity frame on top of items in the toolbar (hotbar) and all inventories (including chests) in a Minecraft 1.20.4 Fabric mod, you need to hook into the item rendering process on the client and draw a custom overlay (the rarity frame) above the item stack icon

## Approach Overview

- Use Fabric's rendering hooks or mixins to intercept the item rendering method(s) on the client.
- Identify the item's rarity and get the associated frame texture.
- Render the rarity frame texture as an overlay on top of the item icon in both the hotbar and inventories.

### Implementation Steps

#### 1. Setup a Render Layer Injection on Item Rendering

You can mixin or subscribe to client rendering events for item stacks. The typical method to target is `net.minecraft.client.gui.screen.Screen` method `drawSlot` or directly the item renderer's method. Mixin is recommended.

#### 2. Sample Mixin for Rendering Rarity Frame Overlay

```java
@Mixin(Screen.class)
public abstract class ItemFrameRenderMixin {

  // Shadow method to access item renderer (used in Screen)
  @Shadow
  protected abstract void drawTexture(MatrixStack matrices, Identifier texture, int x, int y, int u, int v, int width, int height);

  @Inject(method = "drawSlot", at = @At("TAIL"))
  private void injectRenderRarityFrame(Slot slot, MatrixStack matrices, CallbackInfo ci) {
    ItemStack stack = slot.getStack();
    if (!stack.isEmpty()) {
      // Get rarity id or data from stack (e.g., from NBT or custom properties)
      String rarityId = getRarityId(stack); // Implement this to return rarity like "rarity:3"

      // Get frame texture for rarity
      Identifier frameTexture = RarityFrameTextures.getFrameTexture(rarityId);
      if (frameTexture != null) {
        int x = slot.x;
        int y = slot.y;
        MinecraftClient client = MinecraftClient.getInstance();
        client.getTextureManager().bindTexture(frameTexture);
        drawTexture(matrices, frameTexture, x, y, 0, 0, 16, 16);
      }
    }
  }

  private String getRarityId(ItemStack stack) {
    // Example: extract rarity from NBT or ItemStack tags
    if (stack.hasNbt() && stack.getNbt().contains("rarity_id")) {
      return stack.getNbt().getString("rarity_id");
    }
    return null;
  }
}
```

#### 3. Registering Frame Textures

Maintain a utility class or registry with rarity frame textures loaded once:

```java
public class RarityFrameTextures {
  private static final Map<String, Identifier> FRAMES = new HashMap<>();

  public static void registerFrames() {
    FRAMES.put("rarity:1", new Identifier("modid", "textures/gui/common_frame.png"));
    FRAMES.put("rarity:2", new Identifier("modid", "textures/gui/uncommon_frame.png"));
    // Add all rarities here
  }

  public static Identifier getFrameTexture(String rarityId) {
    return FRAMES.get(rarityId);
  }
}
```

Call `RarityFrameTextures.registerFrames()` during client initialization.

#### 4. Hotbar Rendering

The above mixin to `Screen.drawSlot` covers slot rendering everywhere, including hotbar and all inventories.

---

### Notes and Tips

- Ensure the frame textures have transparency so the item icon remains visible beneath.
- Adjust drawing coordinates or size if necessary to perfectly overlay the item slot.
- For better performance, preload all textures and reuse `Identifier` objects.
- If you have custom rarity data in your mod, sync it properly to the client side for use in rendering.

This solution should give a clean overlay of rarity frames in all item containers and the hotbar. If desired, code for this can be further elaborated or integrated into your current mod setup.
