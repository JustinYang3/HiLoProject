# HiLoProject
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */


package hiiloproject;
 
import java.util.Random;
import java.util.Scanner;

public class ComputerPlayer extends HiLo{
    private final Random generator;
    private int generatedNumber;
    private int numberOfAttempts;
    Scanner scan;
    
    public ComputerPlayer()
    {
        generator = new Random();
        scan = new Scanner(System.in);
    }
    
    public void start(){
        boolean wantToPlay = false;
        do{
            if (wantToPlay = super.prompt())
               generatedNumber = super.randGenNum(); 
            playGame();
        } while (wantToPlay);
        
        
        
    }
    
    private void playGame()
    {
        boolean done = false;
        int min = 1;
	int max = 100;
        int count = 0;
        String ans = "";
        
        do
        {
            int guess = min + (int)(Math.random() * (max - min + 1));
            count++;
            
            System.out.println("I guess " + guess);
            
            if (guess > generatedNumber)
                ans = "lower";
            else if (guess < generatedNumber)
                ans = "higher";
            
            if(ans.equals("lower"))
		max = guess - 1;
			
            else if(ans.equals("higher"))
		min = guess + 1;
            else
            {
		System.out.println("Hooray!");
		System.out.println("It took me " + count + " guesses to get it.");
		done = true;
            }
             
        } while(!done); 
    }
}

