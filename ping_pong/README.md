# Ping Pong

A classic Ping Pong game with AI opponent, progressive difficulty, dynamic visual stages, sound effects, and persistent stat tracking.

## Features

- Mouse-controlled paddle gameplay against an AI opponent
- Three difficulty levels (Easy, Medium, Hard) that affect speed ramp-up and AI reaction time
- Progressive ball speed that increases on every paddle hit and after every point scored
- Rally bonus acceleration every 4 consecutive hits
- 5 dynamic visual stages that evolve as the round progresses (Calm, Heating Up, Intense, On Fire, Epic Finale)
- Floating background particles, ball trails, paddle glow, and stage transition flashes
- Synthesized sound effects using the Web Audio API (paddle hits, wall bounces, scoring, stage transitions, win/lose)
- Sound toggle button
- Persistent user statistics: wins, losses, win rate, game history
- Statistics page with charts (win/loss doughnut, performance by difficulty, recent score trend) and game history table
- First to 6 points wins

## Pages

- **/** — Game page
- **/stats** — Statistics dashboard with Chart.js visualizations

## Import

1. Download `ping_pong.xlsx` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Import the `.xlsx` file using the standard Odoo import function

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
