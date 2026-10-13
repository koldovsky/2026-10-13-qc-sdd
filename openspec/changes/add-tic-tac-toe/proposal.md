# Proposal

## Why

The app is still the default Create Next App starter page. We want a small, complete, playable feature to use as the first spec-driven change: a standard tic-tac-toe game.

## What Changes

- Replace the starter home page (`/`) with a playable 3×3 tic-tac-toe game.
- Two players share one device and take turns (X always moves first).
- The game detects a win (three in a row horizontally, vertically or diagonally) and a draw (full board, no winner), then stops accepting moves.
- Show whose turn it is or the result, highlight the winning line, and offer a "New game" button.
- Pure game logic lives in its own module with unit tests; add a test runner (Vitest) to the project.

Assumptions (minor, recorded here rather than asked): local two-player only, no AI opponent, no score history or persistence, no online play.

## Capabilities

### New Capabilities
- `tic-tac-toe`: Rules, turn order, win/draw detection and the player-facing game board on the home page.

### Modified Capabilities
<!-- None -->

## Impact

- `app/page.tsx` replaced; new game component and game-logic module under `app/`.
- New dev dependency: `vitest`; new `test` script in `package.json`.
- No APIs, data storage or server-side changes.
