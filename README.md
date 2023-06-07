/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package HiLoProject;

import java.util.Scanner;

public class TwoPlayerGame extends HiLo{
    private int generatedNumber;
    Scanner scan;
    
        public TwoPlayerGame(){
            scan = new Scanner(System.in);
            generatedNumber = 0;
        }

        public void start() {
            boolean wantToPlay = false;
            boolean firstTime = true;
            do {
                if (wantToPlay = prompt())
                {
                    // Generate a random number for the computer to guess
                    generatedNumber = super.randGenNum();
                    if (firstTime){
                        // Describe the rules of the game
                        describeRules();
                        firstTime = false;
                     }

                    playTwoPlayerGame();
                }
            } while (wantToPlay);
            
            System.out.println("\nThanks for playing the game. Hope you loved it!");
        }

        private void describeRules(){
                    System.out.println("\nHere are the rules: \n"
                            + "Choose who is player 1 and who is player 2.");
                    System.out.println("Player 1 guesses first, then player 2.");
                    System.out.println("Whoever guesses the right number first wins.\n");
                }

        private void playTwoPlayerGame() {
            int count1 = 0, count2 = 0;

            boolean player1 = true;
            boolean done = false;

            while (!done) {      
                if (player1){
                    count1++;

                    System.out.println("Player 1, guess the number: ");
                    int playerGuess = scan.nextInt();
                    scan.nextLine(); // Consume the newline character

                    if (playerGuess > generatedNumber) {
                        System.out.println("Too high!");
                    } else if (playerGuess < generatedNumber) {
                        System.out.println("Too low!");
                    } else {
                        System.out.println("Player 1 guessed the number in " + count1 + 
                                " guesses! Player 1 wins!\n");
                        done = true;
                    }
                    player1 = false;
                    }
                else {
                    count2++;

                    System.out.println("Player 2, guess the number: ");
                    int playerGuess = scan.nextInt();
                    scan.nextLine(); // Consume the newline character

                    if (playerGuess > generatedNumber) {
                        System.out.println("Too high!");
                    } else if (playerGuess < generatedNumber) {
                        System.out.println("Too low!");
                    } else {
                        System.out.println("Player 2 guessed the number in " + count2 +
                                " guesses! Player 2 wins!\n");
                        done = true;
                    }
                    player1 = true;
                }
            }


        }

        private boolean prompt() {
            while (true) {
                System.out.print("Do you want to play a two-player game? Yes / No: ");
                String input = scan.nextLine();
                if (input.equalsIgnoreCase("y") || input.equalsIgnoreCase("yes")) {
                    return true;
                } else if (input.equalsIgnoreCase("n") || input.equalsIgnoreCase("no")) {
                    return false;
                } else {
                    System.out.print("Please enter 'Yes' or 'No': ");
                }
            }
        }
}
