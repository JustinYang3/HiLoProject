/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */


 package HiLoProject;
 
 import java.util.Scanner;
 
 public class ComputerPlayer extends HiLo{
     private int generatedNumber;
     private Scanner scan;
     
     public ComputerPlayer()
     {
         scan = new Scanner(System.in);
         generatedNumber = 0;
     }
     
     public void start(){
     boolean wantToPlay = false;
     boolean firstTime = true;
     do{
         // Prompt the user if they want the computer to keep guessing
         if (wantToPlay = prompt())
         {
             // Generate a random number for the computer to guess
             generatedNumber = super.randGenNum();
             if (firstTime){
                 // Describe the rules of the game
                 describeRules();
                 firstTime = false;
             }
             
             // Start the game
             playGame();
         } 
     } while (wantToPlay);
     
     System.out.println("\nThanks for playing the game. Hope you loved it!");
 }
 
     private void playGame()
     {
         boolean done = false;
         int min = 1;
         int max = 100;
         int count = 0;
 
         while(!done)
         {
             // Generate a random guess within the range
             int guess = min + (int)(Math.random() * (max - min + 1));
             count++;
 
             System.out.println("I guess " + guess);
 
             if (guess > generatedNumber) {
                 System.out.println("Too high");
                 max = guess - 1;
             } else if (guess < generatedNumber) {
                 System.out.println("Too low");
                 min = guess + 1;
             } else {
                 System.out.println("I guessed the right number in " + count + " guesses.\n");
                 done = true;
             }
 
         }   
         
 
     }
     
     private void describeRules(){
             System.out.println("\nHere are the rules: \n"
                     + "You let the computer guess and do all the work.");
             System.out.println("Grab some popcorn and have fun watching"
                     + " the computer play!\n");
         }

     private boolean prompt()
     {
         boolean answer = false;
         boolean inputOk = false;
         while (!inputOk) {
             // Prompt the user for their choice
             System.out.println("Do you want the computer to guess: Yes / No: ");
             String input = scan.nextLine();
             if (input.equalsIgnoreCase("y") || input.equalsIgnoreCase("yes")) {
                 inputOk = true;
                 answer = true;
             } else if (input.equalsIgnoreCase("n")|| input.equalsIgnoreCase("no")) {
                 inputOk = true;
                 answer = false;
             } else {
                 System.out.println(
                         "Please enter 'Yes' or 'No': ");
             }
         }
         return answer;
     }
 }
 
