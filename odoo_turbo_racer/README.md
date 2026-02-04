# Odoo Turbo Racer

An epic Odoo-themed racing game built as an Odoo MCP Studio web application featuring AI opponents, Mario Kart-style powerups, procedurally generated jazz music, and persistent race statistics.

![turbo racer gif](turbo_racer.gif)

## Features

### Gameplay
- Top-down racing with smooth WASD/Arrow key controls
- Camera follows your car around a large scrolling track
- 5-lap races against 4 AI opponents
- Nitro boost system (SPACE/Shift) with rechargeable fuel gauge
- Collision detection between cars with physics-based knockback
- Grass terrain that slows you down - stay on the track!

### AI Opponents
- **OdooBot** - Balanced racer
- **ERPinator** - Aggressive driver
- **ModuleMaster** - Technical precision
- **QueryQueen** - Speed demon
- Rubber-banding system: AI speeds up when behind, slows when ahead
- AI collects and uses powerups strategically

### Mario Kart-Style Powerup System
Position-based powerups reward players who are behind:

| Position | Powerups Available |
|----------|-------------------|
| 1st Place | Weak: Small nitro, mini speed boost |
| 2nd Place | 70% normal, 30% weak items |
| Last Places | 60% OP items, 40% normal |

**Powerup Types:**
- **Odoo Module** - Speed boost (+30-35%)
- **Enterprise License** - Shield protection (no collisions)
- **Turbo Query** - Instant nitro refill
- **Bug Report** - Slows all AI cars
- **Mega Deploy** - Massive speed boost (+50%)
- **Ghost Mode** - Pass through other cars
- **Lightning** - Dramatically slows all AI
- **Git Rebase** - Teleport to next checkpoint!

### Race Track
- Large 4000x2800 world with scrolling camera
- 28-point track with sweeping curves and S-bends
- 8 checkpoints with wide hit areas
- Checkered start/finish line
- Odoo logo landmark in center
- Grass terrain with speed penalty

### Odoo Developer Memes
- 30 Odoo developer memes on billboards around the track
- Includes classics like:
  - "Have you tried upgrading the module?"
  - "It works on my local... *nervous sweating*"
  - "self.env.cr.commit() # YOLO"
  - "Nobody knows why this works. Do not touch."
  - "Temporary fix from 2019"
- Victory meme popup when you win!

### Audio
**4 procedurally generated jazz tracks:**
- **Smooth Swing** - Laid-back jazz with swing timing
- **Fast Bebop** - Uptempo energetic rhythms
- **Slow Blues** - Relaxed mellow pace
- **Cool Ballad** - Smooth and sophisticated

**Sound effects:**
- Collision impacts
- Checkpoint chimes
- Lap completion fanfare
- Powerup collection
- Nitro boost whoosh
- Victory celebration

All audio generated in-browser using Web Audio API (no external files).

### Statistics & Tracking
- Race history saved across sessions
- Stats page with interactive Chart.js graphs:
  - Race time trends (line chart)
  - Position distribution (doughnut chart)
  - Win streak tracking (bar chart)
- Recent races table with dates, positions, times
- Total races, wins, win rate, and best time cards

### Additional Features
- Live position indicator (P1, P2, etc.) in HUD
- Real-time standings showing all racers
- Speed display in km/h
- Lap counter and race timer
- Visual effects: nitro flames, shield rings, boost auras
- Settings page for audio controls
- About page with meme generator

## Pages

1. **Game** - Main racing canvas with full gameplay
2. **Stats** - Interactive charts and race history
3. **Settings** - Audio controls and data management
4. **About** - Feature showcase and meme generator

## Controls

| Key | Action |
|-----|--------|
| W / Arrow Up | Accelerate |
| S / Arrow Down | Brake / Reverse |
| A / Arrow Left | Turn left |
| D / Arrow Right | Turn right |
| SPACE / Shift | Nitro boost |

## Import

1. Download `odoo_turbo_racer.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
