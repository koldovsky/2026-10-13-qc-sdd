# Design

## Context

Next.js 16 App Router project (React 19, Tailwind v4, TypeScript), currently only the starter page. No test runner is installed. Per `AGENTS.md`, consult `node_modules/next/dist/docs/` before writing Next.js code, as APIs may differ from older versions.

## Goals / Non-Goals

**Goals:**
- Keep game rules in pure, framework-free functions that are unit tested.
- Keep the UI a thin client component over that logic.

**Non-Goals:**
- Routing changes, server actions, persistence, AI opponent, animations.

## Decisions

- **Pure logic module (`app/tic-tac-toe/game.ts`)**: board as a 9-element array of `"X" | "O" | null`; functions such as `calculateWinner(board)` (returns winner and winning line), `isDraw(board)`, `currentPlayer(board)` and `applyMove(board, index)` (returns the same board when the move is illegal). Deriving the current player and outcome from the board avoids duplicated state. Alternative considered: a `useReducer` holding turn and status separately — rejected as it can drift out of sync with the board.
- **Client component (`app/tic-tac-toe/Board.tsx`, `"use client"`)**: holds only `board` in `useState`; everything else is derived. `app/page.tsx` stays a server component that renders the game.
- **Cells as `<button>`s** in a CSS grid, giving keyboard operation for free; `aria-label` like "Row 1, column 2, X"; status in an `aria-live="polite"` region; winning cells highlighted with a Tailwind class.
- **Vitest** for unit tests of `game.ts` (fast, TS-native, no Next config needed). Alternative: Jest — heavier setup with ESM/TS. Component tests are skipped; UI is verified manually in the browser.

## Risks / Trade-offs

- [No automated UI tests] → logic is fully unit tested; UI behaviour checked manually against the spec scenarios.
- [Next.js 16 conventions differ from training data] → read bundled docs before editing `app/` files.
