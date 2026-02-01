# Kermit's Fly Catcher (Breakout)

A Kermit the Frog themed Breakout game built as an Odoo MCP Studio web application, featuring meme humor, Odoo/Fabien references, explosive bricks, power-ups, and persistent user statistics.

## Features

### Gameplay
- Classic Breakout mechanics with smooth canvas rendering
- Kermit-styled paddle with animated eyes and tongue power-up
- Ball designed as a fly (Kermit's catching flies!)
- Progressive difficulty - faster ball, more rows, reinforced bricks at higher levels
- Combo system with score multipliers

### Special Brick Types
- **Bomb** - Explodes in a radius, destroying nearby bricks
- **TNT** - Larger explosion with chain reactions
- **Diamond** - 3 HP, worth 5x points
- **Mystery** - Always contains a power-up

### Power-Ups (8 types)
- **Multi-Fly** - Splits balls into multiple flies
- **Big Kermit** - Wider paddle
- **Tongue Lash** - Kermit's tongue shoots up to hit bricks
- **Fire Fly** - Ball burns through bricks without bouncing
- **Turtle Time** - Slow motion effect
- **Extra Life** - Gain a life (max 5)
- **Fly Magnet** - Attracts ball toward paddle
- **Rainbow Connection** - Fireball + rainbow paddle combo

### Audio
- 6 meme-inspired background music tracks:
  - RickRoll, All Star (Shrek), Crazy Frog, Mii Channel, He-Man, Bonfire
- Sound effects for paddle hits, brick breaks, explosions, power-ups, and more
- Separate toggles for music and sound effects

### Visual Effects
- 7 alternating interactive backgrounds that change each level:
  - Swamp, Rainbow, Lilypad, Muppet Show, Starfield, Matrix, Fireflies
- Particle effects on brick destruction
- Screen shake on explosions
- Kermit's eyes grow bigger at higher levels

### Kermit + Odoo Humor
- 50+ funny quotes mixing Kermit, memes, and Odoo/Fabien references
- Examples: "It's not easy being open source!", "This is better than SAP! Yaaay!", "git commit -m 'caught another fly'", "No cap, this ERP slaps!"

### Statistics
- Persistent user stats saved per account
- Tracks: high score, games played, max level, best combo, flies caught

### Controls
- Mouse or A/D keys for paddle movement
- Space or P to pause
- Escape for settings
- Touch support for mobile

## Import

1. Download `odoo_breakout_kermit.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
