# TIC-TAC-ULTIMATE: Enterprise Edition Pro Max Plus

A gloriously over-engineered tic-tac-toe game built as an Odoo MCP Studio web application. Features persistent stat tracking, synthesized audio, procedurally generated background music, dynamic themes, power-ups, achievements, and an absurd amount of unnecessary complexity for a 3x3 grid game.

## Features

### Gameplay
- Classic tic-tac-toe mechanics (it's still just X's and O's)
- AI opponent with "deep contemplation" (1.5 second thinking delay)
- Move history tracking
- Dramatic victory/defeat announcements with confetti

### Difficulty Levels
Six "different" difficulty settings that are essentially identical:
- **EASY** (Still Hard)
- **MEDIUM** (Very Hard)
- **HARD** (Impossible)
- **IMPOSSIBLE** (Same as Easy)
- **NIGHTMARE** (Just Random)
- **ZEN** (AI Lets You Win Sometimes)

### Audio
- **5 procedurally generated background music tracks** using Web Audio API:
  - Epic Battle Symphony (heroic sine wave melody)
  - Chill Lo-Fi Beats (slow, relaxing pattern)
  - Dramatic Movie Score (triangle wave cinema vibes)
  - Elevator Music (classic waiting room feel)
  - 8-Bit Nostalgia (square wave chiptune)
- **Synthesized sound effects:**
  - Click sound on moves
  - Victory fanfare (ascending chord)
  - Sad trombone for defeats (descending sawtooth)
  - Diplomatic handshake sound for draws
  - Power-up activation zap

### Visual Themes
- **5 dynamic backgrounds:**
  - Corporate Synergy (professional gradient)
  - Synthwave Dreams (80s aesthetic)
  - Nature Zen (calming greens)
  - Chaos Mode (animated rainbow)
  - Matrix (green-tinted hacker vibes)
- Animated floating elements and pulsing effects
- Winning cells with rainbow animation
- Confetti explosion on victories

### Statistics
- Persistent user stats saved per account
- Tracks: wins, losses, draws, current streak, best streak, total moves, games played
- Calculated "Tic-Tac-Toe IQ" score
- Player ranking system (Beginner to Grandmaster)
- Visual bar chart on stats page

### Power-Ups
- **Undo** - Take back your last move (and the AI's response)
- **Hint** - Receive premium strategic advice ("Try placing your X in an empty square!")

### Achievements
Unlockable badges including:
- First Blood, Serial Winner, Tic-Tac-Legend
- Hot Streak, Unstoppable, Diplomat
- Persistent (lose 10 times but keep going)
- Dedicated (play 50 games)

### Extra Features
- Motivational quotes from historical figures (fake)
- Dramatic loading screens with humorous progress messages
- Fake premium features page ($49.99 for "AI That Actually Loses")
- Session ID generation for that enterprise feel
- Compact music toggle in header for quick access

## Pages

- **Game** - Main gameplay with board, stats panel, and audio controls
- **Stats** - Comprehensive statistics dashboard with achievements
- **Settings** - Difficulty, audio, and theme configuration with sound test buttons
- **About** - Explains why this exists and lists unnecessary statistics

## Import

1. Download `TIC-TAC-ULTIMATE__Enterprise_Edition_Pro_Max_Plus.csv` from this folder
2. In Odoo, go to **MCP Server > Web Apps** list view
3. Click the **gear icon** (Actions) and select **Import records**
4. Upload the `.csv` file and follow the import wizard

## Requirements

- [Odoo MCP Studio](https://apps.odoo.com/apps/modules/19.0/odoo_remote_mcp)
