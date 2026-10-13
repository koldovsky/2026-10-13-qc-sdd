# Spec Delta

## Purpose

Lets two people on one device play a standard game of tic-tac-toe on a 3×3 board in the browser, with correct turn order and win/draw detection.

## ADDED Requirements

### Requirement: Game board
The home page SHALL display a 3×3 board of nine empty cells when a game starts.

#### Scenario: Fresh game
- **WHEN** a user opens the home page
- **THEN** a 3×3 board is shown with all nine cells empty
- **AND** the status reads that it is X's turn

### Requirement: Turn order
X SHALL make the first move, and players SHALL alternate turns after every valid move.

#### Scenario: Alternating marks
- **WHEN** X places a mark in an empty cell
- **THEN** that cell shows X
- **AND** the status reads that it is O's turn

### Requirement: Occupied cells cannot be changed
A move on a cell that already holds a mark SHALL be ignored and SHALL NOT change the turn.

#### Scenario: Clicking an occupied cell
- **WHEN** a player selects a cell that already holds a mark
- **THEN** the board and the current turn are unchanged

### Requirement: Win detection
The game SHALL declare a winner when one player has three marks in a row horizontally, vertically or diagonally, and SHALL highlight the winning cells.

#### Scenario: Row win
- **WHEN** X holds all three cells of the top row
- **THEN** the status reads that X wins
- **AND** the three winning cells are visually highlighted

#### Scenario: Diagonal win
- **WHEN** O holds the three cells from top-right to bottom-left
- **THEN** the status reads that O wins

### Requirement: Draw detection
The game SHALL declare a draw when all nine cells are filled and no player has three in a row.

#### Scenario: Full board without a winner
- **WHEN** the ninth mark is placed and no line is complete
- **THEN** the status reads that the game is a draw

### Requirement: Game over locks the board
After a win or draw, the game SHALL ignore further moves until a new game is started.

#### Scenario: Move after a win
- **WHEN** a player selects an empty cell after the game has been won
- **THEN** the board is unchanged

### Requirement: New game
The page SHALL provide a "New game" control that clears the board and gives the first move to X.

#### Scenario: Restart mid-game
- **WHEN** a user activates "New game"
- **THEN** all cells are empty and the status reads that it is X's turn

### Requirement: Keyboard and screen reader access
Each cell SHALL be a focusable control operable by keyboard, with an accessible label giving its position and contents, and status changes SHALL be announced to assistive technology.

#### Scenario: Keyboard move
- **WHEN** a keyboard user focuses an empty cell and presses Enter or Space
- **THEN** the current player's mark is placed in that cell
