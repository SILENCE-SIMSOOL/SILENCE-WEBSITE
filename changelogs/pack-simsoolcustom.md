## v1.6.0 - 2026-03-23

**CIT is available starting from Minecraft 1.21.5, and since it uses vanilla features, no additional mods are required.**

However, there are a few issues.
It seems there is an error with number comparisons in JSON `custom_data` in vanilla.
Because of this, I couldn’t detect enchantments properly, and Chimera also cannot be distinguished.

For now, the detection method has been temporarily changed as follows.
- **Hyperion**: Detect `Chimera` enchant → Detect `Fabled` reforge
- **Terminator**: Detect `Duplex` enchant → Detect `Spiritual` reforge
- **Terminator**: Detect `SoulEater` enchant → Detect `Spiritual` reforge
- **Terminator**: Detect `FatalTempo` enchant → Detect `Hasty` reforge

## v1.6.1 - 2026-03-25
- Fixed the enchantment detection. Now, Chimera recognition for Hyperion and the corresponding textures for each enchantment on the Terminator are correctly applied.

## v1.6.2 - 2026-06-29
- Fixed `Starred Last Breath`
- Fixed `Starred Bonzo Staff`

## v1.6.3 - 2026-06-30
- Fixed `Terminator`

## v1.6.4 - 2026-04-29
- Fixed animation for shooting normal bow.
- Lightweight.

## v1.6.5 - 2026-05-09
- Fixed an issue where custom bows (Last Breath, Starred Last Breath, Terminator variants) displayed incorrect position and rotation when viewed from a third-person or other player's perspective.
- Removed unused resources to reduce pack size.

## v1.6.6 - 2026-06-02
- Fixed `Energy Crystal`.
- Edited left hand slot.

## v1.6.7 - 2026-07-10
- Fixed an issue where Custom Item Textures were not applied due to changes in the Hypixel item structure.

## v1.6.11 - 2026-07-18
- Rounded the corners of the Top Slot and Bottom Slot.