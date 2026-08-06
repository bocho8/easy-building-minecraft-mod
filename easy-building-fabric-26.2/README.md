# easy-building (26.2)

This is a modified version of the original [easy-building-minecraft-mod](https://github.com/marianolarre/easy-building-minecraft-mod), ported and adapted for Minecraft 26.2 (Fabric).

## Changes

- Ported to Minecraft 26.2 and Fabric API `0.156.0+26.2`.
- Updated rendering to the new 26.2 feature rendering API (`submitCustomGeometry`).
- Thicker preview lines (more visible).
- The preview square changes color depending on the target position:
  - **White**: position is free and in range.
  - **Red**: out of range.
  - **Orange**: a block is already there and cannot be replaced.

## License

The original mod is released under the MIT License.
