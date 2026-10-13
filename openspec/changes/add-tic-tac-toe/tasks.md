# Tasks

## 1. Test setup

- [ ] 1.1 Add `vitest` as a dev dependency and a `"test": "vitest run"` script; verify `npm test` runs (with no tests, or a trivial placeholder) without config errors

## 2. Game logic

- [ ] 2.1 Create `app/tic-tac-toe/game.ts` with board type, `currentPlayer`, `calculateWinner` (winner + line), `isDraw` and `applyMove`; verify `npx tsc --noEmit` passes
- [ ] 2.2 Add `app/tic-tac-toe/game.test.ts` covering: empty board → X's turn, alternation, occupied cell ignored, all 8 winning lines, draw board, moves ignored after a win; verify `npm test` passes

## 3. UI

- [ ] 3.1 Read the relevant guides in `node_modules/next/dist/docs/` (client components, pages) before editing `app/`
- [ ] 3.2 Create the `"use client"` `Board.tsx` component: 3×3 grid of buttons, status line in an `aria-live` region, winning-cell highlight, "New game" button; verify `npm run lint` passes
- [ ] 3.3 Replace `app/page.tsx` starter content with the game (update page title/metadata in `layout.tsx`); verify `npm run build` succeeds
- [ ] 3.4 Run `npm run dev` and check every scenario in `specs/tic-tac-toe/spec.md` in the browser, including keyboard play (Tab + Enter/Space) and light/dark mode
- [ ] 3.5 Update `README.md` with what the app is and the `npm test` command; verify the documented commands run as written
