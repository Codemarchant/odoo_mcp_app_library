# ODOO SUPPORT: THE FINAL TICKET

An absurdly overengineered Odoo-themed zombie FPS built with Three.js. You are the last Odoo developer on support duty. The tickets have become sentient. Defend your desk from hordes of zombie customers, Karens, confused clients, and rogue Odoo animals across 5 maps and 20 waves.

![odoo support gif](odoo_support.gif)

## Features

### Gameplay
- 20 hand-crafted waves across 5 themed maps
- Wave-based progression with increasing difficulty
- Boss battles every 5 waves with unique attack patterns
- Combo system with score multiplier
- Ticket resolution counter
- Infinite post-game waves after wave 20
- Leaderboard endpoint for high scores

### Weapons

| # | Name | Type | Unlocks | Description |
|---|------|------|---------|-------------|
| 1 | Bug Spray | Pistol | Start | Standard issue. Squashes bugs one at a time. |
| 2 | Stack Overflow | Shotgun | Wave 3 | 5 answers at once. Most are wrong. |
| 3 | Git Push --force | RPG | Wave 8 | Obliterates everything. Including production. |
| 4 | The Backlog | Auto | Wave 13 | Infinite tickets. They never end. NEVER. |
| 5 | sudo rm -rf / | Nuke | Wave 17 | The nuclear option. Deletes EVERYTHING. |

### Enemy Types

**The Open Office (Waves 1-5)**
- **Confused Client** - "WHERE IS THE ANY KEY??" Slow but plentiful
- **Karen Manager** - "I NEED TO SPEAK TO YOUR MODULE MANAGER!" Fast, high damage
- **Zombie Accountant** - "THE SPREADSHEET HUNGERS" Balanced stats

**The Server Room (Waves 6-10)**
- **Rogue Odoo Bot** - Fast and deadly, the machines have turned
- **Cable Monster** - Lurks among the server racks

**The Executive Suite (Waves 11-15)**
- **VP Zombie** - Corporate undead with middle-management rage
- **PPTX Golem** - Animated by 47 unread slide decks

**The Scrapyard (Waves 16-19)**
- **Demon Manager** - Hellfire performance reviews
- **Lava Cow** - Odoo mascot gone very, very wrong

**Bosses**
- **The Ticket Golem** (Wave 5) - Mini-boss, office map
- **The Mainframe** (Wave 10) - The server room rebels
- **The Former Employer** (Wave 15) - "YOU WILL NEVER WORK IN THIS INDUSTRY AGAIN!"
- **Rogue Deployment** (Wave 19) - CI/CD pipeline from hell
- **THE MEGA KAREN** (Wave 20) - Final boss. She wants to speak to your SOUL.

### Maps

| Map | Waves | Subtitle |
|-----|-------|----------|
| The Open Office | 1-5 | Welcome to Support Hell |
| The Server Room | 6-10 | Where Data Goes to Die |
| The Executive Suite | 11-15 | Where Careers Come to Die |
| The Scrapyard | 16-19 | Where Old Code Goes to Rust |
| Karen's Domain | 20 | She Wants to Speak to Your SOUL |

### Visual Effects
- Procedural 3D environments with themed lighting and fog
- Projectile trails and explosion particles
- Damage flash overlay and screen shake
- Wave announcement animations
- Kill feed with enemy death quotes
- Emergency light system per map

### Audio
- Procedural Web Audio API soundtrack (no audio files)
- Per-weapon sound effects (pew, boom, rocket, nuke)
- Map-specific background music tracks
- Weapon unlock fanfare

## Controls

- **W / Up** - Move forward
- **A / Left** - Strafe left
- **S / Down** - Move backward
- **D / Right** - Strafe right
- **Mouse** - Aim
- **Click** - Shoot
- **R** - Reload
- **Space** - Jump
- **Scroll / 1-5** - Switch weapons

## File Structure

All code lives in a single MCP WebApp page with 7 component files:

| File | Seq | Purpose |
|------|-----|---------|
| `constants.js` | 1 | Weapons, enemy types, map themes, wave configs |
| `audio.js` | 2 | Web Audio API engine, procedural music + SFX |
| `enemies.js` | 3 | Enemy spawning, AI, 3D model builder |
| `environment.js` | 4 | 5 themed 3D map builders, NPC system |
| `particles.js` | 5 | Projectile system, explosions, hit effects |
| `engine.js` | 6 | Core game engine, Three.js scene, input, physics |
| `engine_update.js` | 7 | Game loop, wave management, collision detection |
| **component_code** | - | Main React component (GamePage), HUD, state |

### Shared Resources

| Resource | Content |
|----------|---------|
| `shared_components` | `TitleScreen`, `GameOverScreen`, `DamageOverlay`, `Crosshair` |
| `shared_styles` | HUD, crosshair, health bar, kill feed, wave announcements, animations |
| `global_state` | Game state: screen, score, wave, health, ammo, combo, etc. |
| `custom_imports` | Three.js via esm.sh CDN |

## Import

1. Download `ODOO_SUPPORT__THE_FINAL_TICKET_20260214_170817_with_assets.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
