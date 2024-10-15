import java.util.Random;
import java.util.Scanner;

public class SymbolixGame {

    // Define an array of symbols to use in the game
    private static final char[] SYMBOLS = {'@', '#', '$', '%', '&', '*', '!', '^', '~', '?'};
    private static final Random random = new Random();
    private static final Scanner scanner = new Scanner(System.in);

    // Method to generate a random symbol from the pool of symbols
    private static char getRandomSymbol() {
        return SYMBOLS[random.nextInt(SYMBOLS.length)];
    }

    // Method to generate a dynamic grid of random symbols
    private static char[][] generateGrid(int size) {
        char[][] grid = new char[size][size];
        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                grid[i][j] = getRandomSymbol();
            }
        }
        return grid;
    }

    // Method to print the grid, hiding symbols if 'show' is false
    private static void printGrid(char[][] grid, int size, boolean show) {
        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                if (show) {
                    System.out.print(grid[i][j] + " ");
                } else {
                    System.out.print("* ");
                }
            }
            System.out.println();
        }
    }

    // Method to check if the player's guess is correct
    private static boolean checkGuess(char[][] grid, int row, int col, char guess) {
        return grid[row][col] == guess;
    }

    public static void main(String[] args) throws InterruptedException {
        int level = 1;
        int gridSize = 2;  // Start with a 2x2 grid

        while (true) {
            // Generate the grid for the current level
            char[][] grid = generateGrid(gridSize);

            // Display the grid to the player
            System.out.println("\nLevel " + level + ": Memorize the grid!");
            printGrid(grid, gridSize, true);

            // Pause for a few seconds based on the level
            int displayTime = Math.max(1, 5 - level);  // Shorten time as the level increases
            Thread.sleep(displayTime * 1000);

            // Clear the screen (using multiple line breaks for simplicity)
            for (int i = 0; i < 50; i++) System.out.println();

            // Ask the player to guess the symbols in the hidden grid
            System.out.println("Now guess the symbols in the hidden grid!");
            printGrid(grid, gridSize, false);

            int correctGuesses = 0;

            // Loop to get the player's guesses
            for (int i = 0; i < gridSize * gridSize; i++) {
                System.out.print("\nEnter row (0-" + (gridSize - 1) + "): ");
                int row = scanner.nextInt();
                System.out.print("Enter column (0-" + (gridSize - 1) + "): ");
                int col = scanner.nextInt();
                System.out.print("Enter your guess (symbol): ");
                char guess = scanner.next().charAt(0);

                if (checkGuess(grid, row, col, guess)) {
                    System.out.println("Correct!");
                    correctGuesses++;
                } else {
                    System.out.println("Wrong! The correct symbol was " + grid[row][col] + ".");
                }
            }

            // Check if the player passed the level
            if (correctGuesses == gridSize * gridSize) {
                System.out.println("\nCongratulations! You passed level " + level + "!");
                level++;  // Increase the level
                gridSize++;  // Increase the grid size
            } else {
                System.out.println("\nGame Over! You reached level " + level + ".");
                break;
            }
        }
    }
}
