# Aetheria Online - 3D MMO Demo

A 3D open-world MMO-style demo built with Three.js as an Odoo MCP Studio web application, featuring terrain exploration, combat, a climbing tower, dragon battles, and more.

![Aetheria gif](chrome_QFhNRGdBfp.gif)

## Features

### Open World
- Procedurally generated terrain with mountains, forests, beaches, and water
- Dynamic day/night cycle with shifting lighting and fog
- 600 instanced trees, 150 rocks, ambient floating particles
- Explorable castle with courtyard and wandering chicken

### Combat System
- **Sword** - Melee weapon, click to swing and damage nearby enemies
- **Fireball** - Ranged homing projectile, locks onto nearest enemy or raycaster target
- Toggle between weapons with **Q** key
- Target info HUD shows enemy name, class, level, and HP bar

### Enemies
- **Ancient Dragon** (World Boss, Lv.99) - 200 HP, breathes fire, attacks NPCs, roars periodically. Sinks into the ground on death with +5000 Gold reward
- **Ice Giants** (Frost Warriors, Lv.65) - 150 HP, 2.5x scale, patrol beyond the Wall of Frost. +500 Gold reward on kill
- **Wild Bears** (Beasts, Lv.25) - 50 HP, roam forest areas across the map. +50 Gold reward on kill
- All enemies respawn after a cooldown period

### The Wall of Frost
- Massive Game of Thrones-inspired ice wall spanning 160 units with guard towers and battlements
- Translucent ice material with crystal formations at the base
- Frost lighting and "None shall pass" signage
- Ice Giants patrol the frozen north beyond the wall

### Climb to the Top Tower
- "Only Up!" inspired vertical platforming challenge next to the castle
- 40+ spiral platforms with varied sizes and materials
- Rest platforms every 8th level with lights and height markers
- Ledge grab mechanic - auto-grab edges when falling near platforms
- Golden summit beacon with confetti reward on reaching the top
- Summit Keeper NPC and victory credits triggered by sword swing at peak

### The Cave (MeatCanyon Inspired)
- Dark cave entrance with stalactites, glowing green/red lights, and warning sign
- "The Dweller" - grotesque character with oversized head, bulging asymmetric eyes, wide grin with jagged teeth, and twitching animations
- 12 rotating creepy/comedic voice lines displayed as floating 3D text and HUD popup when nearby

### Wildlife
- Deer with antlers roaming grasslands
- Rabbits hopping through meadows
- Chicken pecking around the castle courtyard
- All critters follow terrain and wander naturally

### Player NPCs
- 26 AI-controlled players with randomized names, classes, levels, and colors
- NPCs wander, engage the dragon, and chat in world chat
- Killable with sword (1 damage) or fireball (10 damage), respawn after 8 seconds
- 8 additional NPCs patrol the ice wall area

### Audio
- Procedural Web Audio API soundtrack (no external files)
- Sound effects for sword swings, hits, dragon roars, and fire breath

### UI / HUD
- Player info panel with HP/MP/XP bars
- Target info panel for enemies
- Gold counter and coordinate display
- FPS counter and weapon indicator
- Minimap with player, NPC, enemy, and landmark markers
- Skill bar with 10 ability slots
- World chat with NPC messages and player input
- Height meter for tower climbing
- Ledge grab indicator and summit celebration overlay
- Full victory credits screen

## Controls

- **WASD / Arrows** - Move
- **Mouse** - Look around
- **Shift** - Sprint
- **Space** - Jump / Climb from ledge grab
- **S** (while grabbing) - Drop from ledge
- **Q** - Toggle weapon (Sword / Fireball)
- **Click** - Attack / Fire
- **Scroll** - Zoom camera
- **Enter** - Open chat
- **ESC** - Release cursor

## Import

1. Download `Aetheria_Online_3D_MMO_Demo.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
