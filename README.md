/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package HiLoProject;

import java.util.Scanner;


public class HiLoProject {


    public static void main(String[] args)  {
        Scanner scan = new Scanner(System.in);
        String input;
        
        System.out.println("Do you want to play single player (s), two player (t)"
                + ", or watch the computer (c) play?");
        input = scan.nextLine();
        
        if (input.equalsIgnoreCase("s")){
            HiLo onePlayer = new HiLo();
            onePlayer.start();
        }
        
        if (input.equalsIgnoreCase("t")){
            TwoPlayerGame twoPlayer = new TwoPlayerGame();
            twoPlayer.start();
        }
        
        if (input.equalsIgnoreCase("c")){
            ComputerPlayer comp = new ComputerPlayer();
            comp.start();
        }
        
    }
    
}
