# nesdev
Some NES stuff: simple gamedev and emulator hacking.

*Yes yes. I know. It's all been done to death before.*

# Goals
A slightly-informed, ordered list of tasks:
1. **Basic NES gamedev** gets me familiar with low-level 6502esque programming, concepts and hardware.
2. **CHIP8 emulation** seems to be the `Helloworld` of emulator projects.
3. **PACMAN game**, because I can't think of a simple game, that's just complicated enough to be challenging.
4. **6502 emulation** should be doable. Opcodes are limited, and the NES gamedev/hardware familiarity will help.
5. **NES emulation** -- this is the final goal. Doesn't need to be cycle-perfect -- just loading and running homebrew roms is enough.
6. **Multiplayer PACMAN**, to flex my average emulation skills.

# Notes
Important stuff, for reference.

## NES
CPU addresses from `$2000-$6000` are for MMIO.

The CPU doesn't have direct access to PPU memory. Use CPU address `$2006` (aka `PPUADDR`) to select a PPU memory address and CPU `$2007` (aka `PPUDATA`) to write to the selected address. By default, writing a byte to `PPUDATA` will increment storing address by `1` for the next write.

Info about PPU can be read from `$2002`, aka `PPUSTATUS`. Reading `PPUSTATUS` -- `LDX $2002` -- will reset the `PPUADDR`.

CPU `$2001`, aka `PPUMASK`, gives the actual drawing instruction, along with color-palete related data.
