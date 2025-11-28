# Rarity and Relics

## **Gear up, take risks, and uncover legendary treasures in every adventure!**

## Core Features

### Dynamic Item Rarity

- Every weapon, tool, or piece of equipment is automatically assigned a **random rarity tier**.

### Random Buffs & Debuffs

- Items gain **stat modifiers** (buffs & debuffs) when crafted or discovered.

### Loot & Craft Integration

Rarity and effects apply seamlessly to:

- Crafted items
- Chest loot
- Mob drops

### Fully Data-Driven

- Rarities and modifiers are defined in **JSON files**.

### Persistent & Visible Properties

- Item properties are stored in **NBT**.
- Rarity colored names, Item frames, Tooltips and Tooltip Icons.
- Properties persist when items are moved, dropped, or traded.

```Project Structure
📦rarity-and-relics
 ┣ 📂src
 ┃ ┣ 📂client
 ┃ ┃ ┣ 📂java
 ┃ ┃ ┃ ┗ 📂com
 ┃ ┃ ┃ ┃ ┗ 📂mosberg
 ┃ ┃ ┃ ┃ ┃ ┣ 📂client
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ClientTooltipState.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜TooltipOverlayRenderer.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TooltipRenderer.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂mixin
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂client
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ExampleClientMixin.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜RarityAndRelicsClient.java
 ┃ ┃ ┗ 📂resources
 ┃ ┃ ┃ ┗ 📜rarity-and-relics.client.mixins.json
 ┃ ┗ 📂main
 ┃ ┃ ┣ 📂java
 ┃ ┃ ┃ ┗ 📂com
 ┃ ┃ ┃ ┃ ┗ 📂mosberg
 ┃ ┃ ┃ ┃ ┃ ┣ 📂behavior
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜HealOnHitHandler.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂command
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜DebugCommand.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂mixin
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜CraftingScreenHandlerMixin.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜EntityDamageMixin.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜LootTableMixin.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜LootTableHandler.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Modifier.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ModifierApplier.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜RarityAndRelics.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜RarityManager.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜RarityNbt.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜RarityTier.java
 ┃ ┃ ┗ 📂resources
 ┃ ┃ ┃ ┣ 📂assets
 ┃ ┃ ┃ ┃ ┗ 📂rarity-and-relics
 ┃ ┃ ┃ ┃ ┃ ┣ 📂textures
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂gui
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜common_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜common_icon.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜epic_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜epic_icon.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜legendary_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜legendary_icon.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜mythical_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜mythical_icon.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜rare_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜rare_icon.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜relic_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜relic_icon.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜uncommon_frame.png
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜uncommon_icon.png
 ┃ ┃ ┃ ┃ ┃ ┗ 📜icon.png
 ┃ ┃ ┃ ┣ 📂data
 ┃ ┃ ┃ ┃ ┗ 📂rarity-and-relics
 ┃ ┃ ┃ ┃ ┃ ┗ 📜rarities.json
 ┃ ┃ ┃ ┣ 📜fabric.mod.json
 ┃ ┃ ┃ ┗ 📜rarity-and-relics.mixins.json
 ┣ 📜build.gradle
 ┣ 📜gradle.properties
 ┣ 📜gradlew
 ┣ 📜gradlew.bat
 ┣ 📜LICENSE
 ┣ 📜README.md
 ┗ 📜settings.gradle
```

```build.gradle
plugins {
	id 'fabric-loom' version "${loom_version}"
	id 'maven-publish'
}

version = project.mod_version
group = project.maven_group

base {
	archivesName = project.archives_base_name
}

repositories {
	// Add repositories to retrieve artifacts from in here.
	// You should only use this when depending on other mods because
	// Loom adds the essential maven repositories to download Minecraft and libraries from automatically.
	// See https://docs.gradle.org/current/userguide/declaring_repositories.html
	// for more information about repositories.
}

loom {
	splitEnvironmentSourceSets()

	mods {
		"rarity-and-relics" {
			sourceSet sourceSets.main
			sourceSet sourceSets.client
		}
	}

}

dependencies {
	// To change the versions see the gradle.properties file
	minecraft "com.mojang:minecraft:${project.minecraft_version}"
	mappings "net.fabricmc:yarn:${project.yarn_mappings}:v2"
	modImplementation "net.fabricmc:fabric-loader:${project.loader_version}"

	// Fabric API. This is technically optional, but you probably want it anyway.
	modImplementation "net.fabricmc.fabric-api:fabric-api:${project.fabric_version}"
	
}

processResources {
	inputs.property "version", project.version

	filesMatching("fabric.mod.json") {
		expand "version": inputs.properties.version
	}
}

tasks.withType(JavaCompile).configureEach {
	it.options.release = 17
}

java {
	// Loom will automatically attach sourcesJar to a RemapSourcesJar task and to the "build" task
	// if it is present.
	// If you remove this line, sources will not be generated.
	withSourcesJar()

	sourceCompatibility = JavaVersion.VERSION_17
	targetCompatibility = JavaVersion.VERSION_17
}

jar {
	inputs.property "archivesName", project.base.archivesName

	from("LICENSE") {
		rename { "${it}_${inputs.properties.archivesName}"}
	}
}

// configure the maven publication
publishing {
	publications {
		create("mavenJava", MavenPublication) {
			artifactId = project.archives_base_name
			from components.java
		}
	}

	// See https://docs.gradle.org/current/userguide/publishing_maven.html for information on how to set up publishing.
	repositories {
		// Add repositories to publish to here.
		// Notice: This block does NOT have the same function as the block in the top level.
		// The repositories here will be used for publishing your artifact, not for
		// retrieving dependencies.
	}
}
```

```gradle.properties
# Done to increase the memory available to gradle.
org.gradle.jvmargs=-Xmx1G
org.gradle.parallel=true

# IntelliJ IDEA is not yet fully compatible with configuration cache, see: https://github.com/FabricMC/fabric-loom/issues/1349
org.gradle.configuration-cache=false

# Fabric Properties
# check these on https://fabricmc.net/develop
minecraft_version=1.20.4
yarn_mappings=1.20.4+build.3
loader_version=0.18.1
loom_version=1.13-SNAPSHOT

# Mod Properties
mod_version=1.0.0
maven_group=com.mosberg
archives_base_name=rarity-and-relics

# Dependencies
fabric_version=0.97.3+1.20.4
```

```fabric.mod.json
{
	"schemaVersion": 1,
	"id": "rarity-and-relics",
	"version": "${version}",
	"name": "Rarity and Relics",
	"description": "Gear up, take risks, and uncover legendary treasures in every adventure!",
	"authors": [
		"Mosberg"
	],
	"contact": {
		"homepage": "https://fabricmc.net/",
		"sources": "https://github.com/FabricMC/fabric-example-mod"
	},
	"license": "MIT",
	"icon": "assets/rarity-and-relics/icon.png",
	"environment": "*",
	"entrypoints": {
		"main": [
			"com.mosberg.RarityAndRelics"
		],
		"client": [
			"com.mosberg.RarityAndRelicsClient"
		]
	},
	"mixins": [
		"rarity-and-relics.mixins.json",
		{
			"config": "rarity-and-relics.client.mixins.json",
			"environment": "client"
		}
	],
	"depends": {
		"fabricloader": ">=0.18.1",
		"minecraft": "~1.20.4",
		"java": ">=17",
		"fabric-api": "*"
	},
	"suggests": {
		"another-mod": "*"
	}
}
```

```rarity-and-relics.mixins.json
{
	"required": true,
	"package": "com.mosberg.mixin",
	"compatibilityLevel": "JAVA_17",
	"mixins": [
		"CraftingScreenHandlerMixin",
		"EntityDamageMixin",
		"LootTableMixin"
	],
	"injectors": {
		"defaultRequire": 1
	},
	"overwrites": {
		"requireAnnotations": true
	}
}
```

```rarities.json
{
  "tiers": [
    {
      "key": "common",
      "id": "rarity-and-relics:common",
      "display_name": "Common",
      "color_hex": "#AAAAAA",
      "icon_frame": "textures/gui/common_frame.png",
      "tooltip_icon": "textures/gui/common_icon.png",
      "weights": {
        "default": 50,
        "craft": 60,
        "loot_dungeon": 45,
        "loot_boss": 30
      },
      "modifiers": []
    },
    {
      "key": "uncommon",
      "id": "rarity-and-relics:uncommon",
      "display_name": "Uncommon",
      "color_hex": "#00AA00",
      "icon_frame": "textures/gui/uncommon_frame.png",
      "tooltip_icon": "textures/gui/uncommon_icon.png",
      "weights": {
        "default": 30,
        "craft": 35,
        "loot_dungeon": 35,
        "loot_boss": 25
      },
      "modifiers": []
    },
    {
      "key": "rare",
      "id": "rarity-and-relics:rare",
      "display_name": "Rare",
      "color_hex": "#0000AA",
      "icon_frame": "textures/gui/rare_frame.png",
      "tooltip_icon": "textures/gui/rare_icon.png",
      "weights": {
        "default": 12,
        "craft": 15,
        "loot_dungeon": 15,
        "loot_boss": 20
      },
      "modifiers": []
    },
    {
      "key": "epic",
      "id": "rarity-and-relics:epic",
      "display_name": "Epic",
      "color_hex": "#AA00AA",
      "icon_frame": "textures/gui/epic_frame.png",
      "tooltip_icon": "textures/gui/epic_icon.png",
      "weights": {
        "default": 5,
        "craft": 8,
        "loot_dungeon": 8,
        "loot_boss": 12
      },
      "modifiers": []
    },
    {
      "key": "legendary",
      "id": "rarity-and-relics:legendary",
      "display_name": "Legendary",
      "color_hex": "#FFAA00",
      "icon_frame": "textures/gui/legendary_frame.png",
      "tooltip_icon": "textures/gui/legendary_icon.png",
      "weights": {
        "default": 2,
        "craft": 3,
        "loot_dungeon": 3,
        "loot_boss": 6
      },
      "modifiers": []
    },
    {
      "key": "mythical",
      "id": "rarity-and-relics:mythical",
      "display_name": "Mythical",
      "color_hex": "#55FFFF",
      "icon_frame": "textures/gui/mythical_frame.png",
      "tooltip_icon": "textures/gui/mythical_icon.png",
      "weights": {
        "default": 1,
        "craft": 2,
        "loot_dungeon": 2,
        "loot_boss": 4
      },
      "modifiers": []
    },
    {
      "key": "relic",
      "id": "rarity-and-relics:relic",
      "display_name": "Relic",
      "color_hex": "#FF5555",
      "icon_frame": "textures/gui/relic_frame.png",
      "tooltip_icon": "textures/gui/tooltip-icons/relic_icon.png",
      "weights": {
        "default": 0.5,
        "craft": 1,
        "loot_dungeon": 1,
        "loot_boss": 2
      },
      "modifiers": []
    }
  ]
}

```

```RarityAndRelics.java
package com.mosberg;

import net.fabricmc.api.ModInitializer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

/**
 * Main mod initializer. Registers server-side handlers and client registration is done in client initializer.
 */
public class RarityAndRelics implements ModInitializer {
    public static final String MOD_ID = "rarity-and-relics";
    public static final Logger LOGGER = LoggerFactory.getLogger(MOD_ID);

    @Override
    public void onInitialize() {
        LOGGER.info("Rarity and Relics initializing...");

        // Ensure the manager is loaded (reads rarities.json from classpath)
        RarityManager.getInstance();

        // Register loot handler (server-side)
        try {
            LootTableHandler.register();
            LOGGER.info("Registered loot table handler");
        } catch (Throwable t) {
            LOGGER.warn("Failed to register loot handler: {}", t.getMessage());
        }

        // inside onInitialize()
        try {
            com.mosberg.command.DebugCommand.register();
            LOGGER.info("Registered debug command /rarity apply");
        } catch (Throwable t) {
            LOGGER.warn("Failed to register debug command: {}", t.getMessage());
        }

        // Crafting integration is done via mixin ExampleMixin (no runtime registration needed)
        LOGGER.info("Rarity and Relics initialized");
    }
}
```

```LootTableHandler.java
package com.mosberg;

import net.fabricmc.fabric.api.loot.v2.LootTableEvents;
import net.minecraft.loot.LootManager;
import net.minecraft.resource.ResourceManager;
import net.minecraft.util.Identifier;

/**
 * Example loot table post-processing using Fabric's LootTableEvents and a mixin.
 * Register this in your mod initializer.
 */
public class LootTableHandler {
    public static void register() {
        // This uses Fabric API v2 loot events. If your Fabric API version differs,
        // adapt to the available callback (LootTableLoadingCallback or LootTableEvents).
        LootTableEvents.MODIFY.register((resourceManager, lootManager, id, tableBuilder, source) -> {
            // This callback is invoked when a loot table is being built.
            // We will not modify the table itself here; instead we will rely on
            // post-processing via the mixin below.
        });
    }
}
```

```HealOnHitHandler.java
package com.mosberg.behavior;

import com.mosberg.ModifierApplier;
import net.minecraft.entity.LivingEntity;
import net.minecraft.entity.damage.DamageSource;
import net.minecraft.item.ItemStack;

/**
 * Centralized handler for heal-on-hit behavior.
 * Called from a mixin when an entity is damaged.
 */
public class HealOnHitHandler {
    /**
     * Called when attacker hits a target. Heals the attacker based on held item modifiers.
     *
     * @param attacker the entity that dealt damage
     * @param target the entity that was damaged
     * @param source the damage source
     */
    public static void onEntityDamaged(LivingEntity attacker, LivingEntity target, DamageSource source) {
        if (attacker == null) return;
        ItemStack main = attacker.getMainHandStack();
        double heal = ModifierApplier.getHealOnHit(main);
        if (heal > 0.0 && attacker.isAlive()) {
            float newHealth = Math.min(attacker.getMaxHealth(), attacker.getHealth() + (float) heal);
            attacker.setHealth(newHealth);
        }
    }
}
```

```DebugCommand.java
package com.mosberg.command;

import com.mosberg.RarityManager;
import net.fabricmc.fabric.api.command.v2.CommandRegistrationCallback;
import net.minecraft.server.command.CommandManager;
import net.minecraft.server.command.ServerCommandSource;
import net.minecraft.text.Text;

public class DebugCommand {
    public static void register() {
        CommandRegistrationCallback.EVENT.register((dispatcher, registryAccess, environment) -> {
            dispatcher.register(CommandManager.literal("rarity")
                    .then(CommandManager.literal("apply")
                            .executes(ctx -> {
                                ServerCommandSource src = ctx.getSource();
                                var player = src.getPlayer();
                                var stack = player.getMainHandStack();
                                boolean ok = RarityManager.getInstance().applyRandomRarity(stack, "craft");
                                if (ok) {
                                    src.sendFeedback(() -> Text.literal("Applied rarity to held item"), false);
                                } else {
                                    src.sendError(Text.literal("Failed to apply rarity (maybe already has rarity or no tiers)"));
                                }
                                return ok ? 1 : 0;
                            })));
        });
    }
}
```

```LootTableMixin.java
package com.mosberg.mixin;

import com.mosberg.RarityManager;
import net.minecraft.item.ItemStack;
import net.minecraft.loot.LootTable;
import net.minecraft.loot.context.LootContext;
import net.minecraft.loot.context.LootContextParameters;
import org.spongepowered.asm.mixin.Mixin;
import org.spongepowered.asm.mixin.injection.At;
import org.spongepowered.asm.mixin.injection.Inject;
import org.spongepowered.asm.mixin.injection.callback.CallbackInfoReturnable;

import java.util.List;

@Mixin(LootTable.class)
public class LootTableMixin {
    @Inject(method = "generateLoot(Lnet/minecraft/loot/context/LootContext;)Ljava/util/List;", at = @At("RETURN"))
    private void onGenerateLoot(LootContext context, CallbackInfoReturnable<List<ItemStack>> cir) {
        List<ItemStack> stacks = cir.getReturnValue();
        if (stacks == null || stacks.isEmpty()) return;

        // Determine context type (dungeon, boss, etc.) from the LootContext.
        // Note: We can't get the exact table ID here, so approximate based on context parameters.
        String ctx = "default";
        if (context.hasParameter(LootContextParameters.BLOCK_ENTITY)) {
            ctx = "loot_dungeon";  // Likely a chest or dungeon loot
        }
        if (context.hasParameter(LootContextParameters.KILLER_ENTITY) || context.hasParameter(LootContextParameters.THIS_ENTITY)) {
            ctx = "loot_boss";  // Likely boss or entity loot
        }

        for (ItemStack s : stacks) {
            RarityManager.getInstance().applyRandomRarity(s, ctx);
        }
    }
}
```

```EntityDamageMixin.java
package com.mosberg.mixin;

import com.mosberg.behavior.HealOnHitHandler;
import net.minecraft.entity.LivingEntity;
import net.minecraft.entity.damage.DamageSource;
import org.spongepowered.asm.mixin.Mixin;
import org.spongepowered.asm.mixin.injection.At;
import org.spongepowered.asm.mixin.injection.Inject;
import org.spongepowered.asm.mixin.injection.callback.CallbackInfoReturnable;

/**
 * Inject into LivingEntity.damage to trigger heal-on-hit behavior for attackers.
 */
@Mixin(LivingEntity.class)
public class EntityDamageMixin {
    @Inject(method = "damage", at = @At("RETURN"))
    private void onDamage(DamageSource source, float amount, CallbackInfoReturnable<Boolean> cir) {
        // If damage was applied, call heal-on-hit for the attacker (if any)
        if (!cir.getReturnValue()) return;
        if (source == null) return;
        if (source.getAttacker() instanceof LivingEntity attacker && source.getSource() instanceof LivingEntity) {
            // target is the entity this mixin is on; attacker is source.getAttacker()
            LivingEntity target = (LivingEntity) (Object) this;
            HealOnHitHandler.onEntityDamaged(attacker, target, source);
        } else if (source.getAttacker() instanceof LivingEntity attackerOnly) {
            LivingEntity target = (LivingEntity) (Object) this;
            HealOnHitHandler.onEntityDamaged(attackerOnly, target, source);
        }
    }
}
```

```CraftingScreenHandlerMixin.java
package com.mosberg.mixin;

import com.mosberg.RarityManager;
import net.minecraft.entity.player.PlayerEntity;
import net.minecraft.item.ItemStack;
import net.minecraft.screen.CraftingScreenHandler;
import org.spongepowered.asm.mixin.Mixin;
import org.spongepowered.asm.mixin.injection.At;
import org.spongepowered.asm.mixin.injection.Inject;
import org.spongepowered.asm.mixin.injection.callback.CallbackInfo;

@Mixin(CraftingScreenHandler.class)
public class CraftingScreenHandlerMixin {
    @Inject(method = "onTakeOutput(Lnet/minecraft/entity/player/PlayerEntity;Lnet/minecraft/item/ItemStack;)V", at = @At("TAIL"))
    private void onTakeOutput(PlayerEntity player, ItemStack stack, CallbackInfo ci) {
        // Called when a player takes the crafted result. Apply rarity for "craft" context.
        if (player == null || stack == null || stack.isEmpty()) return;
        RarityManager.getInstance().applyRandomRarity(stack, "craft");
    }
}
```

```RarityTier.java
package com.mosberg;

import com.google.gson.annotations.SerializedName;
import net.minecraft.util.Identifier;
import net.minecraft.util.math.MathHelper;

import java.util.List;
import java.util.Map;
import java.util.Optional;

/**
 * Data model for a rarity tier loaded from JSON.
 */
public class RarityTier {
    public String key;
    public String id;
    @SerializedName("display_name")
    public String displayName;
    @SerializedName("color_hex")
    public String colorHex;
    @SerializedName("icon_frame")
    public String iconFrame;
    @SerializedName("tooltip_icon")
    public String tooltipIcon;
    public Map<String, Double> weights;
    public List<Modifier> modifiers;

    public Identifier getIdentifier() {
        return new Identifier(id);
    }

    public double getWeight(String context) {
        if (weights == null) return 0.0;
        Double w = weights.get(context);
        if (w == null) w = weights.get("default");
        return w == null ? 0.0 : w;
    }

    @Override
    public String toString() {
        return "RarityTier{" +
                "key='" + key + '\'' +
                ", id='" + id + '\'' +
                ", displayName='" + displayName + '\'' +
                '}';
    }

    public Optional<Modifier> pickRandomModifier() {
        if (modifiers == null || modifiers.isEmpty()) return Optional.empty();
        int idx = MathHelper.floor(Math.random() * modifiers.size());
        return Optional.of(modifiers.get(MathHelper.clamp(idx, 0, modifiers.size() - 1)));
    }
}
```

```RarityNbt.java
package com.mosberg;

import net.minecraft.item.ItemStack;
import net.minecraft.nbt.NbtCompound;
import net.minecraft.nbt.NbtList;
import net.minecraft.nbt.NbtElement;

import java.util.ArrayList;
import java.util.List;
import java.util.Optional;

/**
 * Helper methods to read/write rarity data to ItemStack NBT.
 *
 * NBT structure:
 * rarity_and_relics: {
 *   tier: "rarity-and-relics:legendary",
 *   modifiers: [ { id, type, value, display_name? }, ... ]
 * }
 */
public class RarityNbt {
    public static final String ROOT = "rarity_and_relics";
    public static final String TIER = "tier";
    public static final String MODIFIERS = "modifiers";

    public static boolean hasRarity(ItemStack stack) {
        if (stack == null || stack.isEmpty()) return false;
        NbtCompound root = stack.getNbt();
        return root != null && root.contains(ROOT);
    }

    public static Optional<String> getTierId(ItemStack stack) {
        if (!hasRarity(stack)) return Optional.empty();
        NbtCompound root = stack.getNbt();
        NbtCompound rar = root.getCompound(ROOT);
        if (!rar.contains(TIER)) return Optional.empty();
        return Optional.of(rar.getString(TIER));
    }

    public static List<Modifier> getModifiers(ItemStack stack) {
        List<Modifier> out = new ArrayList<>();
        if (!hasRarity(stack)) return out;
        NbtCompound root = stack.getNbt();
        NbtCompound rar = root.getCompound(ROOT);
        if (!rar.contains(MODIFIERS)) return out;
        NbtList list = rar.getList(MODIFIERS, NbtElement.COMPOUND_TYPE);
        for (int i = 0; i < list.size(); i++) {
            out.add(Modifier.fromNbt(list.getCompound(i)));
        }
        return out;
    }

    public static void writeRarity(ItemStack stack, RarityTier tier, List<Modifier> modifiers) {
        NbtCompound root = stack.getOrCreateNbt();
        NbtCompound rar = new NbtCompound();
        rar.putString(TIER, tier.id);
        NbtList list = new NbtList();
        if (modifiers != null) {
            for (Modifier m : modifiers) {
                list.add(m.toNbt());
            }
        }
        rar.put(MODIFIERS, list);
        root.put(ROOT, rar);
    }
}
```

```RarityManager.java
package com.mosberg;

import com.google.gson.Gson;
import com.google.gson.JsonObject;
import com.google.gson.reflect.TypeToken;
import net.minecraft.item.ItemStack;
import net.minecraft.nbt.NbtCompound;

import java.io.InputStream;
import java.io.InputStreamReader;
import java.lang.reflect.Type;
import java.util.*;
import java.util.stream.Collectors;

/**
 * Loads rarities.json from the mod resources and provides selection APIs.
 * This implementation reads the packaged resource at /data/rarity-and-relics/rarities.json.
 *
 * If you want hot reload on resource pack changes, register a resource reload listener
 * and call loadFromStream with the new InputStream.
 */
public class RarityManager {
    private static final String RESOURCE_PATH = "/src/main/resources/data/rarity-and-relics/rarities.json";
    private static final Gson GSON = new Gson();

    private final Map<String, RarityTier> tiersByKey = new LinkedHashMap<>();
    private final List<RarityTier> tiers = new ArrayList<>();
    private final Random random = new Random();

    private static final RarityManager INSTANCE = new RarityManager();

    private RarityManager() {
        loadFromClasspath();
    }

    public static RarityManager getInstance() {
        return INSTANCE;
    }

    private void loadFromClasspath() {
        try (InputStream is = RarityManager.class.getResourceAsStream(RESOURCE_PATH)) {
            if (is == null) {
                RarityAndRelics.LOGGER.warn("Could not find rarities.json at {}", RESOURCE_PATH);
                return;
            }
            InputStreamReader reader = new InputStreamReader(is);
            JsonObject root = GSON.fromJson(reader, JsonObject.class);
            Type listType = new TypeToken<List<RarityTier>>() {}.getType();
            List<RarityTier> loaded = GSON.fromJson(root.getAsJsonArray("tiers"), listType);
            reload(loaded);
            RarityAndRelics.LOGGER.info("Loaded {} rarity tiers", loaded.size());
        } catch (Exception e) {
            RarityAndRelics.LOGGER.error("Failed to load rarities.json", e);
        }
    }

    public synchronized void reload(List<RarityTier> newTiers) {
        tiersByKey.clear();
        tiers.clear();
        for (RarityTier t : newTiers) {
            tiers.add(t);
            tiersByKey.put(t.key, t);
        }
    }

    public Optional<RarityTier> getByKey(String key) {
        return Optional.ofNullable(tiersByKey.get(key));
    }

    public List<RarityTier> getAllTiers() {
        return Collections.unmodifiableList(tiers);
    }

    /**
     * Select a tier by weighted random using the provided context key (e.g., "craft", "loot_boss").
     */
    public Optional<RarityTier> pickTier(String context) {
        List<RarityTier> available = tiers.stream()
                .filter(t -> t.getWeight(context) > 0.0)
                .collect(Collectors.toList());
        if (available.isEmpty()) return Optional.empty();

        double total = available.stream().mapToDouble(t -> t.getWeight(context)).sum();
        double r = random.nextDouble() * total;
        double acc = 0.0;
        for (RarityTier t : available) {
            acc += t.getWeight(context);
            if (r <= acc) return Optional.of(t);
        }
        return Optional.of(available.get(available.size() - 1));
    }

    /**
     * Convenience: apply a random rarity to the given ItemStack and return true if applied.
     * This writes NBT via RarityNbt helper.
     */
    public boolean applyRandomRarity(ItemStack stack, String context) {
        if (stack == null || stack.isEmpty()) return false;
        if (RarityNbt.hasRarity(stack)) return false; // don't overwrite existing rarity

        Optional<RarityTier> tierOpt = pickTier(context);
        if (!tierOpt.isPresent()) return false;
        RarityTier tier = tierOpt.get();

        // pick a single random modifier for now (extend as needed)
        List<Modifier> chosen = new ArrayList<>();
        Optional<Modifier> m = tier.pickRandomModifier();
        m.ifPresent(chosen::add);

        // after RarityNbt.writeRarity(stack, tier, chosen);
        RarityNbt.writeRarity(stack, tier, chosen);

        // Apply modifiers (attributes, enchantments, custom NBT)
        ModifierApplier.applyModifiers(stack);

        return true;
    }
}
```

```ModifierApplier.java
package com.mosberg;

import net.minecraft.item.ItemStack;
import net.minecraft.nbt.NbtCompound;

import java.util.List;

/**
 * Applies modifiers to an ItemStack by writing stable NBT entries.
 * Avoids calling mapping-unstable ItemStack methods at compile time.
 */
public class ModifierApplier {
    private static final String CUSTOM_ROOT = "rarity_and_relics_custom";

    public static void applyModifiers(ItemStack stack) {
        if (stack == null || stack.isEmpty()) return;
        List<Modifier> mods = RarityNbt.getModifiers(stack);
        if (mods.isEmpty()) return;

        NbtCompound root = stack.getOrCreateNbt();
        NbtCompound custom = root.contains(CUSTOM_ROOT) ? root.getCompound(CUSTOM_ROOT) : new NbtCompound();

        for (Modifier m : mods) {
            if (m.type == null) continue;
            switch (m.type) {
                case "enchant_sharpness": {
                    // store enchantment intent in custom NBT; runtime code can apply it
                    custom.putDouble("enchant_sharpness_" + m.id, m.value);
                    break;
                }
                case "custom_heal_on_hit": {
                    custom.putDouble("heal_on_hit_" + m.id, m.value);
                    break;
                }
                case "attribute_attack_damage": {
                    custom.putDouble("attr_attack_damage_" + m.id, m.value);
                    break;
                }
                default: {
                    // generic storage
                    custom.putDouble("mod_" + m.id, m.value);
                    break;
                }
            }
        }

        root.put(CUSTOM_ROOT, custom);
    }

    /**
     * Helper to read heal-on-hit value from an ItemStack (if present).
     */
    public static double getHealOnHit(ItemStack stack) {
        if (stack == null || stack.isEmpty()) return 0.0;
        NbtCompound root = stack.getNbt();
        if (root == null) return 0.0;
        if (!root.contains(CUSTOM_ROOT)) return 0.0;
        NbtCompound custom = root.getCompound(CUSTOM_ROOT);
        for (String key : custom.getKeys()) {
            if (key.toLowerCase().contains("heal")) {
                return custom.getDouble(key);
            }
        }
        return 0.0;
    }
}
```

```Modifier.java
package com.mosberg;

import com.google.gson.annotations.SerializedName;
import net.minecraft.nbt.NbtCompound;

/**
 * Simple modifier model. Extend as needed for different modifier types.
 */
public class Modifier {
    public String id;
    public String type;
    public double value;
    @SerializedName("display_name")
    public String displayName;

    public NbtCompound toNbt() {
        NbtCompound t = new NbtCompound();
        t.putString("id", id);
        t.putString("type", type);
        t.putDouble("value", value);
        if (displayName != null) t.putString("display_name", displayName);
        return t;
    }

    public static Modifier fromNbt(NbtCompound t) {
        Modifier m = new Modifier();
        m.id = t.getString("id");
        m.type = t.getString("type");
        m.value = t.getDouble("value");
        if (t.contains("display_name")) m.displayName = t.getString("display_name");
        return m;
    }

    @Override
    public String toString() {
        return "Modifier{" + id + "," + type + "," + value + "}";
    }
}
```

```rarity-and-relics.client.mixins.json
{
	"required": false,
	"package": "com.mosberg.mixin.client",
	"compatibilityLevel": "JAVA_17",
	"client": [
		"ExampleClientMixin"
	],
	"injectors": {
		"defaultRequire": 1
	}
}
```

```ClientTooltipState.java
package com.mosberg.client;

import java.util.concurrent.atomic.AtomicReference;

public class ClientTooltipState {
    public static final class Marker {
        public final String key;
        public final String framePath;
        public final String iconPath;
        public Marker(String key, String framePath, String iconPath) {
            this.key = key;
            this.framePath = framePath;
            this.iconPath = iconPath;
        }
    }

    private static final AtomicReference<Marker> MARKER = new AtomicReference<>(null);

    public static void setMarker(String key, String framePath, String iconPath) {
        MARKER.set(new Marker(key, framePath, iconPath));
    }

    public static Marker getMarker() {
        return MARKER.get();
    }

    public static void clearMarker() {
        MARKER.set(null);
    }
}
```

```TooltipOverlayRenderer.java
package com.mosberg.client;

import net.fabricmc.api.EnvType;
import net.fabricmc.api.Environment;
import net.fabricmc.fabric.api.client.rendering.v1.HudRenderCallback;
import net.minecraft.client.MinecraftClient;
import net.minecraft.client.gui.DrawContext;
import net.minecraft.util.Identifier;

/**
 * Draws rarity frame and icon next to tooltips that include the marker line.
 */
@Environment(EnvType.CLIENT)
public class TooltipOverlayRenderer {
    private static final MinecraftClient CLIENT = MinecraftClient.getInstance();
    private static final int ICON_SIZE = 16;
    private static final int PADDING = 4;

    public static void register() {
        HudRenderCallback.EVENT.register(TooltipOverlayRenderer::onHudRender);
    }

    private static void onHudRender(DrawContext context, float tickDelta) {
        ClientTooltipState.Marker marker = ClientTooltipState.getMarker();
        if (marker == null) return;

        int mouseX = (int) (CLIENT.mouse.getX() * CLIENT.getWindow().getScaledWidth() / (double) CLIENT.getWindow().getWidth());
        int mouseY = (int) (CLIENT.mouse.getY() * CLIENT.getWindow().getScaledHeight() / (double) CLIENT.getWindow().getHeight());

        int drawX = mouseX + PADDING;
        int drawY = mouseY - ICON_SIZE - PADDING;

        Identifier frameId = new Identifier("rarity-and-relics", marker.framePath);
        Identifier iconId = new Identifier("rarity-and-relics", marker.iconPath);

        // Draw frame
        context.drawTexture(frameId, drawX, drawY, 0, 0, ICON_SIZE, ICON_SIZE, ICON_SIZE, ICON_SIZE);

        // Draw icon (slightly smaller, offset)
        context.drawTexture(iconId, drawX + 2, drawY + 2, 0, 0, ICON_SIZE - 4, ICON_SIZE - 4, ICON_SIZE - 4, ICON_SIZE - 4);
    }
}
```

```TooltipRenderer.java
package com.mosberg.client;

import com.mosberg.Modifier;
import com.mosberg.RarityManager;
import com.mosberg.RarityNbt;
import com.mosberg.RarityTier;
import net.fabricmc.api.EnvType;
import net.fabricmc.api.Environment;
import net.fabricmc.fabric.api.client.item.v1.ItemTooltipCallback;
import net.minecraft.text.Text;
import net.minecraft.util.Formatting;

@Environment(EnvType.CLIENT)
public class TooltipRenderer {
    private static final String MARKER_PREFIX = "rarity_icon:";

    public static void register() {
        ItemTooltipCallback.EVENT.register((stack, context, lines) -> {
            if (!RarityNbt.hasRarity(stack)) {
                ClientTooltipState.clearMarker();
                return;
            }
            RarityNbt.getTierId(stack).ifPresent(tid -> {
                String key = tid.contains(":") ? tid.substring(tid.indexOf(':') + 1) : tid;
                RarityManager.getInstance().getByKey(key).ifPresent(tier -> {
                    int color = parseHex(tier.colorHex, 0xFFFFFF);
                    lines.add(1, Text.literal(tier.displayName).styled(s -> s.withColor(color)));
                    for (Modifier m : RarityNbt.getModifiers(stack)) {
                        String name = m.displayName != null ? m.displayName : m.id;
                        lines.add(Text.literal("• " + name + " " + m.value).formatted(Formatting.GRAY));
                    }
                    // set client-side marker so overlay renderer can draw textures
                    ClientTooltipState.setMarker(tier.key, tier.iconFrame, tier.tooltipIcon);
                });
            });
        });

        TooltipOverlayRenderer.register();
    }

    private static int parseHex(String hex, int fallback) {
        try {
            if (hex == null) return fallback;
            if (hex.startsWith("#")) hex = hex.substring(1);
            return Integer.parseInt(hex, 16);
        } catch (Exception e) {
            return fallback;
        }
    }
}
```

```ExampleClientMixin.java
package com.mosberg.mixin.client;

import net.minecraft.client.MinecraftClient;
import org.spongepowered.asm.mixin.Mixin;
import org.spongepowered.asm.mixin.injection.At;
import org.spongepowered.asm.mixin.injection.Inject;
import org.spongepowered.asm.mixin.injection.callback.CallbackInfo;

@Mixin(MinecraftClient.class)
public class ExampleClientMixin {
	@Inject(at = @At("HEAD"), method = "run")
	private void init(CallbackInfo info) {
		// This code is injected into the start of MinecraftClient.run()V
	}
}
```

```RarityAndRelicsClient.java
package com.mosberg;

import com.mosberg.client.TooltipRenderer;
import com.mosberg.client.TooltipOverlayRenderer;
import com.mosberg.client.ClientTooltipState;
import net.fabricmc.api.ClientModInitializer;

/**
 * Client initializer: register tooltip rendering and other client-only features.
 */
public class RarityAndRelicsClient implements ClientModInitializer {
    @Override
    public void onInitializeClient() {
        TooltipRenderer.register();
        TooltipOverlayRenderer.register();
    }
}
```
