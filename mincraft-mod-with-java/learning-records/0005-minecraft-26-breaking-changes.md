# Learning Record: Minecraft 26 Breaking Changes (Fabric Registry)

**Issue:**
The user pointed out that the Fabric API and Minecraft codebase introduced major breaking changes in Minecraft 26. The previous lesson taught item registration using `net.minecraft.registry.Registry` and `new Identifier()`, which is now completely obsolete.

**Key API Changes:**
1. **Packages**: Modifiers moved from `net.minecraft.item.Item` to `net.minecraft.world.item.Item`. `Registry` moved to `net.minecraft.core.Registry`.
2. **BuiltInRegistries**: Replaces `Registries.ITEM`. The new path is `net.minecraft.core.registries.BuiltInRegistries`.
3. **ResourceKey**: Registration now requires pre-creating a `ResourceKey<Item>` and explicitly binding it to the item's `Properties` via `.setId()`.
4. **Identifier**: Replaced `new Identifier("namespace", "path")` with the static factory method `Identifier.parse("namespace:path")`.
5. **Data-Driven Item Models**: In Minecraft 26 (1.21.4+), the item model logic was completely decoupled. You now MUST create an **Item Model Definition** at `assets/<namespace>/items/<item_name>.json`. This definition points to the actual model file in `models/item/<model_name>.json`, which in turn points to the `textures/item/<texture_name>.png`.

**Action Taken:**
- Overhauled Lesson 0004 to reflect this exact new registration pattern.
- Updated `NOTES.md` to establish **Minecraft 26** as the permanent baseline for all future code generation and lessons in this workspace.

**Future Implication:**
Whenever generating code for Blocks, Entities, or any other registry-based object, I must strictly follow the `ResourceKey` + `BuiltInRegistries` pattern and NEVER use the old `new Identifier()` syntax. Furthermore, for ANY custom items, I must ALWAYS scaffold the three-tier asset system: `items/*.json` (Definition) -> `models/item/*.json` (Geometry) -> `textures/item/*.png` (Texture).
