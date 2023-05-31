/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package hiiloproject;

import java.util.Scanner;


public class HIiLoProject {


    public static void main(String[] args)  {
        // TODO code application logic here
        Scanner scan = new Scanner(System.in);
        String input;
        
        System.out.println("Do you want to play single player (s), two player (t)"
                + ", or watch the computer (c) play?");
        input = scan.nextLine();
        
        if (input.equals("s")){
            HiLo onePlayer = new HiLo();
            onePlayer.start();
        }
        
        if (input.equals("t")){
            TwoPlayerGame twoPlayer = new TwoPlayerGame();
            twoPlayer.start();
        }
        
        if (input.equals("c")){
            ComputerPlayer comp = new ComputerPlayer();
            comp.start();
        }
        
    }
    
}
