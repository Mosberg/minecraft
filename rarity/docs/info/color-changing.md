# color-changing

Yes, it is possible to implement color-changing item names and tooltips in Minecraft 1.20.4 Fabric mods, though it requires custom client-side rendering and text component manipulation.

Implementation Approach
Use Minecraft's Text API with MutableText and Style to dynamically change colors on item names and tooltips.

Implement a client-side tick or animation handler to update the text color over time, cycling through your specified color gradients.

Use mixins or Fabric's client events to inject this behavior into item tooltip rendering or name display.

For smooth color transitions (like your Divine and Transcendent gradients), interpolate colors in your code on a periodic basis and update the text style accordingly.

Considerations
This effect is purely visual and must be handled client-side; server-side cannot force color animations.

Performance optimization is important since updating tooltips frequently can be costly.

Minecraft's built-in text components support formatted colors and styles but not native animations, so you manually implement the color cycling logic.

Many existing Fabric mods achieve similar effects by customizing tooltip rendering or using JSON text components with dynamic style updates in the client tick.

If desired, implementation examples and further help on coding this can be provided.

---

Here are implementation examples and guidance for creating color-changing item names and tooltips in a Minecraft 1.20.4 Fabric mod using Java.

## Example 1: Dynamic Color Changing for Item Name

```java
import net.minecraft.client.MinecraftClient;
import net.minecraft.client.util.math.MatrixStack;
import net.minecraft.text.MutableText;
import net.minecraft.text.Text;
import net.minecraft.text.Style;
import net.minecraft.util.Formatting;
import net.minecraft.item.ItemStack;
import net.minecraft.client.gui.screen.Screen;

public class ColorChangingItem {

  // Call this when rendering tooltips, override method or use event hooks
  public static void renderColoredTooltip(MatrixStack matrices, ItemStack stack, int x, int y) {
    String baseName = stack.getName().getString();
    Text coloredName = getColorfulName(baseName);

    // Example: Render the colored name manually (context dependent)
    MinecraftClient.getInstance().textRenderer.draw(matrices, coloredName, (float) x, (float) y, 0xFFFFFF);
  }

  private static Text getColorfulName(String baseName) {
    int tick = MinecraftClient.getInstance().world != null
      ? MinecraftClient.getInstance().world.getTime()
      : 0;
    int length = baseName.length();
    MutableText text = Text.literal("");

    // Cycle colors through a rainbow for each character depending on tick time
    for (int i = 0; i < length; i++) {
      int color = getRainbowColor((tick + i * 5) % 360);
      text.append(Text.literal(String.valueOf(baseName.charAt(i))).setStyle(Style.EMPTY.withColor(color)));
    }

    return text;
  }

  // Utility to generate rainbow color from hue
  private static int getRainbowColor(int hue) {
    float saturation = 1f;
    float brightness = 1f;
    return java.awt.Color.HSBtoRGB(hue / 360f, saturation, brightness);
  }
}
```

## Example 2: Color-Changing Tooltip Lines

In your item class, override the method to append tooltip text and modify colors dynamically:

```java
@Override
public void appendTooltip(ItemStack stack, World world, List<Text> tooltip, TooltipContext context) {
    int tick = MinecraftClient.getInstance().world != null
      ? (int) MinecraftClient.getInstance().world.getTime() : 0;
    tooltip.add(getColorfulText("Blessed by gods, embodying supreme rarity.", tick));
}

private Text getColorfulText(String text, int tick) {
    MutableText colored = Text.literal("");
    for (int i = 0; i < text.length(); i++) {
      int color = ColorChangingItem.getRainbowColor((tick + i * 10) % 360);
      colored.append(Text.literal(String.valueOf(text.charAt(i))).setStyle(Style.EMPTY.withColor(color)));
    }
    return colored;
}
```

### Further Help and Integration Tips

- Inject or call these methods during client-side tooltip rendering events (e.g., using Fabric's `ClientTooltipCallback`).
- Avoid doing heavy calculations on every frame. Cache colors if possible and update only once per tick.
- For gradient color effects like Divine/Transcendent, interpolate RGB colors using time-based parameters instead of a simple rainbow effect.
- Make sure to run all rendering logic only on the client thread and guard against `null` world/client contexts.

If you want, I can help you create a Fabric mixin or event subscriber for hooking into tooltip rendering specifically.
