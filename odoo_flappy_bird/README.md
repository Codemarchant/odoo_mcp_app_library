# Odoo Flappy Bird

A Flappy Bird clone built as an Odoo MCP Studio web application with Odoo theming, sound effects, and persistent user statistics.

![Flappy gif](odoo_mcp_app_library/odoo_flappy_bird.gif)

## Features

### Gameplay
- Classic Flappy Bird mechanics with smooth 60fps canvas rendering
- Tap/click or press Space to flap and navigate through pipes
- Responsive collision detection for pipes, ground, and ceiling
- Scrolling background with animated clouds and ground

### Odoo Theming
- Bird designed with Odoo's signature purple colors (#714B67, #875A7B)
- Gradient pipes matching Odoo's brand palette
- Custom Odoo logo on menu screen
- Purple-themed UI throughout

### Audio
- **Flap sound** - Rising pitch tone when jumping
- **Score sound** - Celebratory ascending notes when passing pipes
- **Game over sound** - Descending sawtooth wave on collision
- All sounds generated via Web Audio API (no external files needed)

### Statistics
- Persistent user stats saved per account
- Tracks: high score, games played, total pipes passed
- Calculates and displays average score
- New high score celebration animation

### Controls
- Space bar or Up arrow to flap
- Click/tap on canvas to flap
- Works on both desktop and mobile

## Import

1. Download `odoo_flappy_bird.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
