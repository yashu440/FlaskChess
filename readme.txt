================================================================================
                            AI CHESS ENGINE
================================================================================

PROJECT OVERVIEW
--------------------------------------------------------------------------------
This is an interactive web-based chess application featuring an AI opponent 
powered by a custom chess engine. Players can compete against the AI through 
an intuitive browser interface, with the AI using minimax algorithm with 
alpha-beta pruning and iterative deepening to calculate optimal moves.

The application provides:
- Interactive chessboard with drag-and-drop piece movement
- Adjustable AI difficulty (search depth 1-5)
- Move history tracking with PGN notation
- Visual feedback for game status (check, checkmate, draw)
- Take-back functionality to undo moves
- New game reset option


TECHNICAL STACK
--------------------------------------------------------------------------------
Backend:
- Python 3.x
- Flask (web framework)
- python-chess (chess logic and board representation)

Frontend:
- HTML5/CSS3
- JavaScript (ES5+)
- jQuery 3.2.1
- Bootstrap 3.3.7
- chessboard.js 0.3.0 (visual board interface)
- chess.js 0.10.2 (client-side move validation)


PREREQUISITES
--------------------------------------------------------------------------------
Before running this application, ensure you have the following installed:

1. Python 3.6 or higher
2. pip (Python package manager)


INSTALLATION & EXECUTION
--------------------------------------------------------------------------------
Follow these steps to set up and run the application:

1. Install Flask:
   pip install flask

2. Install python-chess library:
   pip install python-chess

3. Navigate to the project directory in your terminal

4. Start the Flask development server:
   python flask_app.py

5. Open your web browser and navigate to:
   http://127.0.0.1:5000/

The application will run in debug mode by default, allowing for automatic 
reloading when code changes are detected.


CORE LOGIC
--------------------------------------------------------------------------------

flask_app.py (Web Server):
- Serves the main web interface at the root route (/)
- Provides API endpoint /move/<depth>/<fen>/ that accepts:
  * depth: AI search depth (1-5 plies)
  * fen: Current board position in FEN notation
- Returns the AI's calculated move in algebraic notation
- Runs on Flask development server with debug mode enabled

chess_engine.py (AI Engine):
- Implements the Engine class with chess AI algorithms
- Uses minimax algorithm with alpha-beta pruning for move calculation
- Features iterative deepening for improved move ordering
- Evaluation functions:
  * Material evaluation: Piece value counting
  * Positional evaluation: Piece-square tables for strategic positioning
- Piece values: Pawn=100, Knight=300, Bishop=310, Rook=500, Queen=900
- Supports configurable search depth (default max: 60 plies)
- Tracks performance metrics (leaves evaluated, calculation time)

board_test.py (Testing):
- Simple test script for validating python-chess library functionality
- Demonstrates basic board operations and move generation


USAGE
--------------------------------------------------------------------------------
Once the server is running and you've opened the application in your browser:

1. MAKING MOVES:
   - Click and drag pieces to make your move (you play as White)
   - Only legal moves are allowed
   - Pieces will snap back if you attempt an illegal move

2. AI DIFFICULTY:
   - Use the "Depth" dropdown menu to select AI strength:
     * Depth 1: Beginner (fastest, ~1 second)
     * Depth 2: Easy (fast, ~2-5 seconds)
     * Depth 3: Medium (moderate, ~10-30 seconds)
     * Depth 4: Hard (slow, ~1-5 minutes)
     * Depth 5: Expert (very slow, ~5-30 minutes)
   - Higher depth = stronger play but longer wait times

3. GAME CONTROLS:
   - "Take Back" button: Undo your last move (and AI's response)
   - "New Game" button: Reset the board to starting position

4. GAME INFORMATION:
   - Status display shows whose turn it is and game state
   - Move table displays complete game history in standard notation
   - Captured pieces are tracked internally

5. GAME END:
   - The game detects checkmate, stalemate, and draw conditions
   - Status message will indicate the game result


PROJECT STRUCTURE
--------------------------------------------------------------------------------
.
├── flask_app.py              # Flask web server and API routes
├── chess_engine.py           # AI chess engine implementation
├── board_test.py             # Testing script
├── README.txt                # This file
├── templates/
│   └── index.html            # Main web interface
├── static/
│   ├── style.css             # Custom styling
│   ├── scripts.js            # Client-side game logic
│   └── libs/
│       └── chessboard/       # Chessboard.js library files
│           ├── css/          # Board styling
│           ├── js/           # Board functionality
│           └── img/          # Chess piece images
└── __pycache__/              # Python bytecode cache


NOTES
--------------------------------------------------------------------------------
- The AI always plays as Black; the human player is White
- Pawn promotion automatically promotes to Queen
- The application uses FEN (Forsyth-Edwards Notation) for board state transfer
- All move calculations are performed server-side for security
- Debug mode is enabled by default (disable for production use)


TROUBLESHOOTING
--------------------------------------------------------------------------------
- If the board doesn't display: Clear browser cache and refresh
- If moves are slow: Reduce the AI depth setting
- If the server won't start: Check that port 5000 is not in use
- If pieces don't move: Ensure JavaScript is enabled in your browser


FUTURE ENHANCEMENTS
--------------------------------------------------------------------------------
- Opening book integration
- Endgame tablebase support
- Move time limits
- Player vs Player mode
- Save/load game functionality
- Advanced evaluation features (mobility, king safety, pawn structure)


================================================================================
                        Enjoy playing against the AI!
================================================================================
