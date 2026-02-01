# Pac-Man Classic

A faithful recreation of the classic Pac-Man arcade game built as an Odoo MCP Studio web application with authentic gameplay, sound effects, and persistent user stat tracking.

## Features

- Classic 28x31 tile maze layout matching the original arcade game
- Four ghosts with authentic AI behaviors:
  - **Blinky** (Red) - Directly chases Pac-Man
  - **Pinky** (Pink) - Targets 4 tiles ahead of Pac-Man
  - **Inky** (Cyan) - Uses Blinky's position for complex targeting
  - **Clyde** (Orange) - Chases when far, scatters when close
- Scatter/Chase mode cycling (ghosts alternate between chasing and retreating to corners)
- Power pellets that make ghosts vulnerable for 7 seconds
- Classic ghost release timing from the ghost house
- Tunnel wraparound on maze sides
- Authentic 8-bit sound effects (waka-waka, power pellet, ghost eaten, death)
- Optional background music (classic Pac-Man theme from Internet Archive)
- Persistent user statistics:
  - High score
  - Games played
  - Total dots eaten
  - Ghosts eaten
  - Levels completed
- Level progression with "READY!" countdown
- Retro arcade styling with "Press Start 2P" font
- Keyboard controls (Arrow keys or WASD)

## Gameplay

- **Dots**: 10 points each
- **Power Pellets**: 50 points, makes ghosts vulnerable
- **Ghosts**: 200, 400, 800, 1600 points (chain bonus)
- **Lives**: 3 per game
- **Frightened Mode**: 7 seconds duration

## Import

1. Download `pac_man_classic.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Import the `.csv` file using the standard Odoo import function

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
