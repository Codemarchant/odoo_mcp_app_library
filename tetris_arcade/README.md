# Tetris Arcade

A full-featured Tetris game built as an Odoo MCP Studio web application with multiple game modes, background music, dynamic backgrounds, and persistent user statistics.

## Features

### Gameplay
- Classic Tetris mechanics with smooth controls
- **Ghost piece** preview showing where pieces will land
- **5-piece preview queue** (modern Tetris Guideline style)
- **7-bag randomizer** for fair piece distribution
- Combo system for consecutive line clears
- Hard drop and soft drop support

### Game Modes
- **Classic** - Traditional Tetris with increasing speed per level
- **Marathon** - Endless endurance mode
- **Sprint** - Race to clear 40 lines as fast as possible
- **Zen** - Relaxing mode with no game over for practice

### Audio
- **6 background music tracks:**
  - Korobeiniki (classic Tetris theme)
  - Synthwave
  - Chiptune
  - Ambient
  - Techno
  - Jazz
- Sound effects for moves, rotations, drops, line clears, and level ups
- Separate toggles for music and sound effects

### Visual Effects
- **10 dynamic backgrounds** that change as you level up:
  - Starfield, Ocean Deep, Neon City, Aurora, Volcanic, Matrix, Cosmic, Ice Cave, Sunset, Ultimate
- Animated particle effects unique to each background theme
- Glowing piece effects and line clear animations

### Statistics
- Persistent user stats saved per account
- Tracks: games played, total lines, total score, max level, high scores per mode
- Detailed statistics page with averages and records

### Controls
- Arrow keys or WASD for movement
- Up/W to rotate
- Down/S for soft drop
- Space for hard drop
- P/Escape to pause

## Import

1. Download `Tetris_Arcade.xlsx` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.xlsx` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
