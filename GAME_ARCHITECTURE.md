# RichMan World V3 Architecture

## Goal
Build an original, extensible cartoon board-game engine inspired by the depth of classic property-trading games without copying protected characters, art, maps, dialogue, UI, music, or branded content.

## Modules now introduced
- `src/game-data.js` — original characters, maps, skills, and card definitions.
- `src/ai.js` — reusable AI decisions for buying property, upgrading, cards, and stocks.
- `src/save-system.js` — browser local save/resume layer.

## Planned engine split
- `src/engine.js` — turn state machine, movement, tile resolution.
- `src/economy.js` — cash, property valuation, rent, bankruptcy.
- `src/cards.js` — card inventory and effects.
- `src/stocks.js` — stock market simulation.
- `src/events.js` — personal/world events.
- `src/ui.js` — rendering and modal/controller layer.

## Art pipeline placeholders
- `assets/characters/{bear,bunny,mimi,dino}/`
- `assets/buildings/`
- `assets/tiles/`
- `assets/ui/`

The current emoji pieces remain temporary placeholders until original transparent character assets are generated.

## V3 milestones
1. Lobby: map selection, player count, human/AI configuration, character selection.
2. Game engine modularization and deterministic state snapshots.
3. Autosave after each completed turn and resume game.
4. AI opponents using the reusable decision module.
5. More original cards and status effects.
6. Art asset replacement and movement/reaction animations.
7. Audio, additional maps, then online multiplayer after the single-player game is stable.
