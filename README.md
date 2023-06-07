package HiLoProject;


import java.util.Scanner;
import java.util.Random;

public class HiLo {

  private final Random generator;
  private int generatedNumber;
  Scanner scan;

  public HiLo() {
    generator = new Random();
    scan = new Scanner(System.in);
    generatedNumber = 0;
  }

  public void start() {

    boolean wantToPlay = false;
    boolean firstTime = true;

    do {
      System.out.println("Want to play the game of Hi and Lo?");

      if (wantToPlay = prompt()) {
        generatedNumber = randGenNum();
        if (firstTime) {
          describeRules();
          firstTime = false;
        }
        playGame();
      }

    } while (wantToPlay);

    System.out.println("\nThanks for playing the game. Hope you loved it!");
  }

  private void describeRules() {

    System.out.println("\nOnly 2 Rules:");
    System.out.println("Guess the secret number.");
    System.out.println("The secret number is an integer between 1 and 100, inclusive.\n");
  }

  protected int randGenNum() {
    return (generator.nextInt(100) + 1);
  }

  private void playGame() {
      boolean done = false;
      int count = 0;
      
      while (!done) {

      int guess = getNextGuess();
      count++;

      if (guess > generatedNumber) {
        System.out.println("Too high");
      } else if (guess < generatedNumber) {
        System.out.println("Too low");
      } else {
        System.out.println("You guessed the right number in " + count + " guesses! Congratulations!\n");
        done = true;
      }
      
    }

  }

  private boolean prompt() {

    boolean answer = false;

    boolean inputOk = false;
    while (!inputOk) {
        System.out.print("Yes / No : ");
        String input = scan.nextLine();
        if (input.equalsIgnoreCase("y") || input.equalsIgnoreCase("yes")) {
            inputOk = true;
            answer = true;
        } else if (input.equalsIgnoreCase("n")|| input.equalsIgnoreCase("no")) {
            inputOk = true;
            answer = false;
        } else {
            System.out.println(
                    "Please enter 'Yes' or 'No':");
        }
    }
    return answer;
  }

  private int getNextGuess() {

    boolean inputOk = false;
    int number = 0;
    String input = null;
    while (!inputOk) {
      try {
        System.out.print("Please guess the secret number: ");
        input = scan.nextLine();
        number = Integer.parseInt(input);
        if (number >= 1 && number <= 100) {
          inputOk = true;
        } else {
          System.out.println(
              "Really? You didn't read the rules boy. Your number is not between 1 and 100 ("
                  + number + ").");
        }
      } catch (NumberFormatException e) {
        System.out.println("Invalid input (" + input + ")");
      }
    }

    return number;
  }
}
