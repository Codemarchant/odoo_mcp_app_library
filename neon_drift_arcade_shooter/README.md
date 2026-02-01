# Neon Drift: Arcade Shooter

A fast-paced vertical arcade shooter built with PIXI.js featuring wave-based gameplay, diverse enemy types, powerful bosses, and an arsenal of power-ups.

## Features

### Gameplay
- Wave-based progression with increasing difficulty
- Boss battles every 5 waves with unique attack patterns
- Lives system with visual heart display
- Score tracking with kill counter

### Enemy Types
- **Drifter** - Basic enemies that float downward
- **Zigzag** - Enemies that weave side to side
- **Charger** - Fast enemies that rush toward the player
- **Bomber** - Explode on death dealing area damage
- **Sniper** - Stationary enemies that shoot accurate projectiles
- **Tank** - High-health enemies that take multiple hits
- **Splitter** - Split into smaller enemies when destroyed

### Boss Types
- **Standard Boss** - Multi-phase attacks with spread shots and aimed fire
- **Spawner Boss** - Summons waves of minion enemies during battle
- **Laser Boss** - Charges and fires devastating laser beams
- Each boss type appears on different wave milestones with increasing health

### Power-ups
- **Speed Boost** - Temporarily increases movement speed
- **Shield** - Absorbs damage and protects from enemy collisions
- **Multi-Shot** - Fire three projectiles in a spread pattern
- **Rapid Fire** - Dramatically increases fire rate
- **Bomb** - Screen-clearing explosion (rare, drops from bosses)

### Wave Events
- **Enemy Clusters** - Large groups spawn in formation
- **Speed Waves** - Fast-moving enemy swarms
- **Elite Squads** - Mixed groups of tough enemy types
- **Boss Waves** - Epic boss encounters every 5 waves

### Visual Effects
- Neon glow aesthetic with particle effects
- Explosion animations and screen shake
- Boss health bar display
- Dynamic star field background

## Controls

- **W / Up Arrow** - Move up
- **A / Left Arrow** - Move left
- **S / Down Arrow** - Move down
- **D / Right Arrow** - Move right
- **Space** - Shoot

## Import

1. Download `Neon_Drift__Arcade_Shooter.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
