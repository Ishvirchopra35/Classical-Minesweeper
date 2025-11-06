# Classic Minesweeper Game

A Python implementation of the classic Minesweeper game built with Pygame, featuring Object-Oriented Programming principles and recursive flood-fill algorithm.

## Game Demo

**[Watch Gameplay Demo](https://www.youtube.com/watch?v=GrZwJ1MTJM4)**

![Minesweeper Gameplay](assets/minesweeper-horizontal-banner.jpg)

## Screenshots

<div align="center">

### Game Start
![Game Start](screenshots/game_start.png)
*Fresh game board ready to play*

### Mid-Game
![Mid Game](screenshots/mid_game.png)
*Strategic gameplay with revealed tiles and flags*

### Win Screen
![Win Screen](screenshots/win_screen.png)
*Victory! All non-mine tiles revealed*

### Loss Screen
![Loss Screen](screenshots/loss_screen.png)
*Game over - mine exploded*

</div>

---

## Project Overview

This project recreates the beloved Minesweeper puzzle game where players must clear a board containing hidden mines without detonating any of them. The game uses logical deduction based on number clues that indicate how many mines are adjacent to each revealed square.

## Features

- **Classic Gameplay**: Traditional Minesweeper mechanics with left-click to reveal and right-click to flag
- **Customizable Board**: Easily adjust board size and mine count through settings
- **Recursive Reveal**: Automatic flood-fill algorithm reveals all connected empty tiles
- **Flag System**: Mark suspected mines with flags to track your progress
- **Win/Loss Detection**: Automatic game-over detection with mine reveal
- **Visual Feedback**: 
  - Number tiles (1-8) showing adjacent mine count
  - Flag markers for suspected mines
  - Explosion animation for triggered mines
  - Win screen with auto-flagging remaining tiles
- **Replay Functionality**: Click to start a new game after winning or losing

## Tech Stack

- **Python 3.x**: Core programming language
- **Pygame**: Game development framework for graphics and event handling
- **Object-Oriented Design**: Clean class structure with `Game`, `Board`, and `Tile` classes

## Project Architecture

### Classes

**Game Class**
- Manages game loop and state
- Handles user input (mouse clicks)
- Controls game flow (win/loss conditions)

**Board Class**
- Generates the game board
- Places mines randomly
- Calculates clue numbers
- Implements recursive dig algorithm

**Tile Class**
- Represents individual board squares
- Stores tile state (revealed, flagged, type)
- Handles tile rendering

### Game Logic Flow

```
Initialize Game → Create Board → Place Mines → 
Calculate Clues → Game Loop → Handle Input → 
Check Win/Loss → End Screen → Replay
```

## Default Configuration

- **Board Size**: 15x15 tiles
- **Mine Count**: 30 mines
- **Tile Size**: 32x32 pixels
- **Window Size**: 480x480 pixels
- **FPS**: 60

*All values are customizable in `settings.py`*

## Getting Started

### Prerequisites

```
python --version  # Python 3.6 or higher
pip install pygame
```

### Installation

1. **Clone the repository**
```
git clone https://github.com/Ishvirchopra35/Ishvir-Minesweeper-Game.git
cd Ishvir-Minesweeper-Game
```

2. **Install dependencies**
```
pip install pygame
```

3. **Run the game**
```
python main.py
```

## How to Play

### Controls
- **Left Click**: Reveal a tile
- **Right Click**: Flag/unflag a suspected mine
- **After Game Over**: Click anywhere to start a new game

### Rules
1. Click on tiles to reveal what's underneath
2. Numbers indicate how many mines are adjacent (including diagonals)
3. Flag suspected mines with right-click to avoid accidentally clicking them
4. Reveal all non-mine tiles to win
5. Click on a mine and you lose!

### Strategy Tips
- Start by clicking corners or edges for safer initial moves
- Use the number clues to deduce mine locations
- Flag known mines to avoid mistakes
- Look for patterns (e.g., a "1" with only one unrevealed neighbor)

## Project Structure

```
minesweeper/
│
├── main.py                 # Main game loop and Game class
├── sprites.py              # Board and Tile classes
├── settings.py             # Configuration and constants
├── assets/                 # Game images
│   ├── Tile1.png          # Number tiles (1-8)
│   ├── Tile2.png
│   ├── ...
│   ├── TileEmpty.png      # Empty revealed tile
│   ├── TileExploded.png   # Exploded mine
│   ├── TileFlag.png       # Flag marker
│   ├── TileMine.png       # Mine tile
│   ├── TileUnknown.png    # Unrevealed tile
│   └── TileNotMine.png    # Incorrectly flagged tile
└── README.md
```

## Customization

### Adjust Difficulty

Edit `settings.py` to modify game parameters:

```
# Easy Mode
ROWS = 9
COLS = 9
AMOUNT_MINES = 10

# Medium Mode (Default)
ROWS = 15
COLS = 15
AMOUNT_MINES = 30

# Hard Mode
ROWS = 20
COLS = 20
AMOUNT_MINES = 80

# Expert Mode
ROWS = 30
COLS = 16
AMOUNT_MINES = 99
```

### Change Appearance

```
# Adjust tile size
TILESIZE = 32  # Make tiles bigger or smaller

# Modify colors
BGCOLOR = DARKGREY  # Change background color
```

## 🔬 Key Algorithms

### 1. Random Mine Placement
```
def place_mines(self):
    # Places mines randomly without duplicates
    # Ensures exactly AMOUNT_MINES are placed
```

### 2. Neighbor Counting
```
def check_neighbours(self, x, y):
    # Counts adjacent mines in 8 directions
    # Returns number for clue display
```

### 3. Recursive Flood Fill
```
def dig(self, x, y):
    # Recursively reveals connected empty tiles
    # Stops at numbered clues or board edges
    # Base case: mine, clue, or already revealed
```

## Learning Outcomes

This project demonstrates:
- **Object-Oriented Programming**: Classes, methods, and encapsulation
- **Recursion**: Flood-fill algorithm for auto-revealing tiles
- **Game Development**: Game loop, event handling, and state management
- **Algorithm Design**: Mine placement, neighbor counting, win detection
- **Pygame Framework**: Graphics rendering, event processing, display management
- **Data Structures**: 2D arrays for board representation
- **Modular Design**: Separation of concerns (settings, sprites, main logic)

## Known Issues & Limitations

- No timer functionality (can be added)
- No high score tracking
- First click can be a mine (some versions protect against this)
- No difficulty selection menu (requires manual settings.py edit)

## Future Enhancements

- [ ] Add timer to track completion time
- [ ] Implement first-click safety (never mine on first click)
- [ ] Create main menu with difficulty selection
- [ ] Add high score system with persistent storage
- [ ] Include sound effects and background music
- [ ] Add "?" marker for uncertain tiles
- [ ] Implement hint system for beginners
- [ ] Create custom board shapes (hexagon, triangle)
- [ ] Add multiplayer mode
- [ ] Include achievement system

## Game States

```
NEW GAME → PLAYING → WIN/LOSS → END SCREEN → NEW GAME
```

**Playing State**:
- User can click tiles
- Flags can be toggled
- Win/loss is checked after each action

**Win Condition**:
- All non-mine tiles are revealed
- All mines automatically get flagged

**Loss Condition**:
- Mine is clicked
- All mines are revealed
- Incorrect flags shown as "not mine"

## Performance

- **Initial Load**: Instant (lightweight assets)
- **Frame Rate**: Consistent 60 FPS
- **Memory Usage**: Minimal (< 50MB)
- **Scalability**: Can handle boards up to 50x50 before performance issues

## Asset Credits

- Tile graphics designed for classic Minesweeper aesthetic
- Custom assets created for this project

## Code Highlights

### Elegant Tile Initialization
```
self.board_list = [[Tile(col, row, tile_empty, '.') 
                    for row in range(ROWS)] 
                    for col in range(COLS)]
```

### Smart Neighbor Checking
```
for x_offset in range(-1, 2):
    for y_offset in range(-1, 2):
        # Check all 8 adjacent tiles
```

### Recursive Reveal Logic
```
for row in range(max(0, x-1), min(ROWS-1, x+1) + 1):
    for col in range(max(0, y-1), min(COLS-1, y+1) + 1):
        if (row, col) not in self.dug:
            self.dig(row, col)  # Recursive call
```

## Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

## License

This project is open source and available for educational purposes.

## Acknowledgments

- Original Minesweeper game by Microsoft
- Pygame community for excellent documentation
- Classic Windows Minesweeper for inspiration

## Contact

**Ishvir Singh Chopra**  
Email: ishvir.chopra@gmail.com  
GitHub: [@Ishvirchopra35](https://github.com/Ishvirchopra35)  
YouTube Demo: [Watch Here](https://www.youtube.com/watch?v=GrZwJ1MTJM4)

---

## Quick Start Commands

```
# Clone and run
git clone https://github.com/Ishvirchopra35/Ishvir-Minesweeper-Game.git
cd Ishvir-Minesweeper-Game
pip install pygame
python main.py
```

---

**⭐ If you enjoyed this project, please consider giving it a star on GitHub!**
