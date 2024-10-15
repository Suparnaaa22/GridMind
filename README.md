# **Symbolix**

### A dynamic memory-based challenge game where players must recall symbols in an increasingly difficult grid.

## **Overview**
**Symbolix** is a terminal-based memory game developed in Java. Players must memorize a grid filled with random symbols before recalling them in their correct positions. As players advance through levels, the grid size increases, and the time allowed for memorization decreases, adding to the challenge.

## **Features**
- **Dynamic Grid Sizes**: The game starts with a 2x2 grid and expands as levels increase.
- **Random Symbols**: The game uses a variety of symbols (`@`, `#`, `$`, etc.) for a visually challenging experience.
- **Increasing Difficulty**: Each level has a shorter memorization time.
- **Terminal-based Gameplay**: Lightweight and easily portable.

## **Gameplay**
1. Players start at level 1 with a 2x2 grid.
2. The grid is shown for a few seconds to memorize.
3. After hiding the grid, players guess the symbols in the correct positions.
4. Correct guesses allow advancement to the next level.
5. The game ends when a player guesses incorrectly.

## **How to Play**
1. **Compile the game**: 
    ```bash
    javac SymbolixGame.java
    ```
2. **Run the game**:
    ```bash
    java SymbolixGame
    ```
3. Memorize the displayed grid.
4. After it’s hidden, enter your guesses for the symbols at specific positions.
5. Try to progress through as many levels as possible before making a mistake!

## **Customization Options**
You can modify the game in several ways to tailor the experience:
- **Difficulty Adjustments**: Change the starting size of the grid, modify the number of levels, or tweak the memory time for each level.
- **Scoring and Leaderboard**: Implement a scoring system to track points earned based on the number of correct guesses or create a leaderboard to store the highest scores.
- **Symbol Pool Modifications**: Modify the `getRandomSymbol()` method to introduce different symbol pools, allowing for unique themes or complexity.
