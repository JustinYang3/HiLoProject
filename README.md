/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package hiiloproject;

import java.util.Random;
import java.util.Scanner;

public class TwoPlayerGame extends HiLo{
    private final Random generator;
    private int generatedNumber;
    Scanner scan;
    
public TwoPlayerGame(){
    generator = new Random();
    scan = new Scanner(System.in);
}

public void start() {
    boolean wantToPlay = false;
    do {
        System.out.print("Do you want to play a two-player game? Yes / No: ");
        wantToPlay = prompt();
        playTwoPlayerGame();
        
    } while (!wantToPlay);
}


private void playTwoPlayerGame() {
    int count1 = 0, count2 = 0;
    int guess = super.randGenNum();
    boolean player1 = true;
    boolean done = false;
    
    while (!done) {      
        if (player1){
            count1++;

            System.out.println("Player 1, guess the number: ");
            int playerGuess = scan.nextInt();
            scan.nextLine(); // Consume the newline character
            
            if (playerGuess > guess) {
                System.out.println("Too high!");
            } else if (playerGuess < guess) {
                System.out.println("Too low!");
            } else {
                System.out.println("Player 1 guessed the number in " + count1 + 
                        " guesses! Player 1 wins!");
                done = true;
            }
            player1 = false;
            }
        else {
            count2++;
            
            System.out.println("Player 2, guess the number: ");
            int playerGuess = scan.nextInt();
            scan.nextLine(); // Consume the newline character
            
            if (playerGuess > guess) {
                System.out.println("Too high!");
            } else if (playerGuess < guess) {
                System.out.println("Too low!");
            } else {
                System.out.println("Player 2 guessed the number in " + count2 +
                        " guesses! Player 2 wins!");
                done = true;
            }
            player1 = true;
        }
    }
    
    
}

private boolean prompt() {
    while (true) {
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
