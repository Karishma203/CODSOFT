# CODSOFT-NUMBER GAME
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {

    public static void main(String[] args) {
        playGame();
    }

    static void playGame() {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerLimit = 1;
        int upperLimit = 100;
        int maxAttempts = 10;
        int rounds = 0;
        int totalScore = 0;

        System.out.println("Welcome to the Number Guessing Game!");

        while (true) {
            rounds++;
            System.out.printf("\nRound %d\n", rounds);

            int targetNumber = random.nextInt(upperLimit - lowerLimit + 1) + lowerLimit;
            int attempts = 0;

            System.out.printf("Guess the number between %d and %d!%n", lowerLimit, upperLimit);

            while (attempts < maxAttempts) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess == targetNumber) {
                    System.out.printf("Congratulations! You guessed the correct number in %d attempts.%n", attempts);
                    totalScore += maxAttempts - attempts + 1;
                    break;
                } else if (userGuess < targetNumber) {
                    System.out.println("Too low. Try again.");
                } else {
                    System.out.println("Too high. Try again.");
                }
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String playAgain = scanner.next().toLowerCase();

            if (!playAgain.equals("yes")) {
                System.out.printf("%nGame over! You played %d rounds and your total score is %d.%n", rounds, totalScore);
                break;
            }
        }

        scanner.close();
    }
}
