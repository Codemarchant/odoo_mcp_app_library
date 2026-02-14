# Waifu Island: Starfall Beach

A 3D anime dating sim / adventure game built entirely as an **Odoo MCP WebApp** using React 19, Three.js, and the Web Audio API. Explore a mysterious island, meet five magical guardians, complete quests in themed 3D areas, and collect crystals to repair your crashed airship.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [File Structure](#file-structure)
- [Game Flow](#game-flow)
- [Characters](#characters)
- [Technical Details](#technical-details)
- [Deployment](#deployment)

---

## Overview

You crash-land on a starfall island inhabited by five anime guardians, each protecting a magical crystal. Explore the 3D island hub, enter themed areas, complete quests, build relationships through dialogue choices, and collect all five crystals to win.

**Built with:**
- **React 19** - UI state management, screens, dialogue system
- **Three.js** - 3D island map, explorable areas, anime character models, decorations
- **Web Audio API** - Romantic background music, Japanese voice babble, sound effects
- **Odoo MCP WebApp** - Hosting, persistent storage (save/load), no build step required

---

## Features

### 3D Island Hub
- Fully 3D island with animated ocean, organic terrain, cherry blossom trees, and structures
- Orbit camera with drag-to-rotate, scroll-to-zoom controls
- Glowing location markers (depth-test disabled) visible above all terrain
- Falling petal particle effects

### 5 Themed Explorable Areas
Each waifu has a unique 3D area with WASD/arrow key player movement:

| Area | Theme | Quest | Decorations |
|------|-------|-------|-------------|
| Starfall Beach | Sandy coastline with ocean | Collect 5 Magical Shells | Palm trees, rocks, water |
| Cherry Blossom Temple | Pink sakura garden | Light 5 Sacred Lanterns | Cherry trees, torii gate, lanterns |
| Moonlit Tower | Dark enchanted night | Catch 5 Fallen Stars | Tower, bookshelves, crystals |
| Ember's Forge | Volcanic wasteland | Collect 5 Flame Shards | Lava rocks, lava streams |
| Crystal Cavern | Frozen ice cave | Find 5 Ice Flowers | Ice pillars, glowing crystals |

### 3D Anime Character Models
- Procedural Three.js models (no external assets required)
- Per-waifu hair styles, outfits, and accessories
- Animated idle, blink, and talk cycles
- Expression changes (blush, love, angry, scared, etc.)
- Characters face the player in real-time

### Dialogue System
- Branching dialogue trees with player choices
- Choices affect affection levels (+3 to +8 per choice)
- Typewriter text animation with voice babble
- 2D anime portrait renderer with dynamic expressions
- Crystal award scenes triggered by affection thresholds

### Audio Engine
- **Romantic background music** - Am-F-C-G chord progression with arpeggios, melody, and warm pad
- **Japanese voice babble** - Formant synthesis with per-character pitch variation
- **Sound effects** - Dialogue boop, affection hearts, crystal collection, UI clicks

### Persistent Save System
- Automatic save/load via Odoo WebApp storage API
- Tracks: affection per waifu, crystals collected, seen dialogue scenes, quest completion

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    React Component (GamePage)                │
│                                                             │
│  Screens: Title -> Map -> Area -> (Dialogue Overlay) -> Win │
│  State: affs, crys, seen, questsDone, screen, showDlg      │
│  Refs: affsR, crysR, seenR (for Three.js callback access)  │
└──────────────┬──────────────────────────────────────────────┘
               │
    ┌──────────┼──────────────┐
    │          │              │
    ▼          ▼              ▼
┌────────┐ ┌────────────┐ ┌──────────────┐
│ Island │ │ Area World │ │ Portrait +   │
│ Scene  │ │ + Player   │ │ Audio Engine │
│(map)   │ │ (3D area)  │ │ (2D + sound) │
└────────┘ └──────┬─────┘ └──────────────┘
                  │
           ┌──────┼──────┐
           ▼      ▼      ▼
        ┌─────┐ ┌─────┐ ┌───────┐
        │Waifu│ │Deco │ │Quest  │
        │ 3D  │ │Build│ │Items  │
        └─────┘ └─────┘ └───────┘
```

### Stale Closure Pattern
Three.js callbacks are created once and form closures over initial state. The game uses **refs** (`affsR`, `crysR`, `seenR`, `nearWR`, `showDlgR`) synced via `useEffect` to ensure callbacks always access current values. Handler refs (`locH`, `interactH`) are updated on every render.

---

## File Structure

All code lives in a single MCP WebApp page with 5 component files injected in sequence order:

| File | Seq | Purpose | Key Exports |
|------|-----|---------|-------------|
| `game-data.js` | 1 | Character definitions, dialogue trees, location data | `WAIFUS`, `LOCATIONS`, `SCENES`, `getNextScene()`, `getSceneById()` |
| `island-scene.js` | 2 | 3D island hub map with orbit camera | `createIslandWorld(container, onClickLocation)` |
| `portrait-audio.js` | 3 | 2D anime portrait renderer + audio engine | `drawPortrait(canvas, waifuId, expr)`, `createAudio()` |
| `waifu-3d.js` | 4 | 3D anime character builder + player model | `createWaifu3D(waifuId)`, `createPlayerModel()`, `_p()` helper |
| `area-world.js` | 5 | Themed explorable areas with quests + movement | `AREA_DEFS`, `mkDeco()`, `createAreaWorld(container, loc, waifu, cbs)` |
| **component_code** | - | Main React component (GamePage) | Screen management, state, dialogue, save/load |

### Shared Resources

| Resource | Content |
|----------|---------|
| `shared_styles` | Full CSS: title screen, HUD pills, dialogue boxes, portrait frame, animations |
| `shared_components` | `TypingText` (typewriter effect), `StarField` (background stars) |
| `cdn_dependencies` | Three.js v0.168.0 via esm.sh |

---

## Game Flow

```
Title Screen
    │
    ▼ (click "Begin Adventure")
3D Island Map
    │
    ├─► Click waifu location marker
    │       │
    │       ▼
    │   Themed 3D Area
    │       │
    │       ├─► Walk around (WASD/arrows)
    │       ├─► Auto-collect quest items (proximity)
    │       ├─► Approach waifu → "Press E to talk"
    │       │       │
    │       │       ▼
    │       │   Dialogue Overlay (area pauses)
    │       │       ├─► Text lines with voice babble
    │       │       ├─► Player choices (+affection)
    │       │       ├─► Crystal scenes (affection ≥ 20)
    │       │       └─► Returns to area on end
    │       │
    │       ├─► Quest complete → +10 affection (first time)
    │       └─► Back to Map button
    │
    ├─► Click village → flavor text
    ├─► Click airship → check crystal count
    │       │
    │       ▼ (5/5 crystals)
    │   Win Screen
    │       └─► Return to Island
    └─► HUD: crystals, affection per waifu, quest stars
```

---

## Characters

| Character | Title | Location | Personality | Crystal |
|-----------|-------|----------|-------------|---------|
| Sakura | Shrine Maiden of Blossoms | Cherry Blossom Temple | Warm, kind, slightly shy | Crystal of Kindness |
| Luna | Moonlight Sorceress | Moonlit Tower | Tsundere, secretly lonely | Crystal of Wisdom |
| Coral | Spirit of the Tides | Starfall Beach | Energetic, cheerful, playful | Crystal of Joy |
| Ember | Flame Guardian | Ember's Forge | Stoic, strong, emotionally guarded | Crystal of Courage |
| Yuki | Ice Crystal Fairy | Crystal Cavern | Extremely shy, gentle, anxious | Crystal of Serenity |

Each character has:
- **Intro scene** (plays once on first meeting)
- **Chat scenes** (repeatable, unlock at affection thresholds)
- **Crystal scene** (plays once at affection ≥ 20, awards crystal)
- **Unique voice pitch** for the babble system (1.0 - 1.6)

---

## Technical Details

### Three.js Integration
- Three.js loaded via esm.sh CDN (`three@0.168.0`)
- All 3D content is procedurally generated (no external model files)
- `_p(mesh, x, y, z)` helper replaces `Object.assign` for Three.js position setting (position is read-only in modern Three.js)
- Location markers use `depthTest: false` to render above terrain geometry

### Web Audio Formant Synthesis
The voice babble system simulates Japanese anime speech using:
- 5 vowel formant pairs: a(800,1200), i(300,2300), u(350,900), e(500,1800), o(500,800)
- Dual oscillators (sine + triangle harmonic) per syllable
- Per-character pitch multiplier (Sakura: 1.4, Luna: 1.2, Coral: 1.5, Ember: 1.0, Yuki: 1.6)
- 90ms interval between syllables, auto-stop after text finishes typing

### State Management
- React `useState` for UI-reactive state (screen, dialogue, HUD)
- React `useRef` for Three.js callback access (avoids stale closures)
- `useEffect` sync bridges between state and refs
- Handler refs (`locH`, `interactH`) updated every render for latest state access

---

## Deployment

### As Odoo MCP WebApp

The game runs as an MCP WebApp (ID: 71, slug: `waifu-island`):

```
App URL:  /mcp/webapp/waifu-island
Form URL: /odoo/mcp.webapp/71
```

### Recreating from Scratch

Use the `manage_webapp` MCP tool to recreate. The build requires 6 sequential tool calls due to token limits:

1. **Create webapp** + game page (shared_styles, shared_components, CDN deps)
2. **Create file** `game-data.js` (character data, dialogue trees)
3. **Create file** `island-scene.js` (3D island hub)
4. **Create file** `portrait-audio.js` (2D portraits, audio engine)
5. **Create file** `waifu-3d.js` (3D character models)
6. **Create file** `area-world.js` (explorable areas, quests)
7. **Update page** component_code (main game logic)

### Requirements

- Odoo 19 with MCP Studio module installed
- No additional dependencies (Three.js loaded via CDN)
- Works on desktop and mobile (touch controls included)
