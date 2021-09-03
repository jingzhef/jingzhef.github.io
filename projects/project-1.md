---
layout: project
type: project
image: images/PokemonBattle.jpg
title: Pokemon Battle
permalink: projects/PokemonBattle
date: 2021-09-02
labels:
  - Pokemon
  - Gaming
  - C++
summary: My team developed a Pokemon battle game by using the Java programming language in the fall semester of 2020. 

<img class="ui medium right floated rounded image" src="/images/micromouse-robot.png">

In the fall semester of school year 2020, my ICS 211 partner Eva Teresa and I developed a gaming sofeware program that supports two players and generated Pokemons with choosen species and choosen name but random HP value. The program allows you to catch different Pokemons with different characteristics like "Fire", "Water", "Poison", etc and different skills due to species, which may affect the battle outcome depends on the enermy's characteristics.

For this project, Eva and I were in charged for almost every part of it because it was such a important and difficult project at the time to us. We shared opinions from genertating Pokemons, choose species, name the Pokemons, to settle players, the order of which player goes first, and how skill attcks is going to affect enermy's HP, and the game over screen. We both learned a lot of how Java can be running in one program but with many different related files.

The following is my our coding for the Pokemon project in Java 

import java.util.Scanner;
import java.util.Random;
/**
 * A two player game of Pokemon battle.
 * @author JingZhe Feng, Eva Teresa
 * @since 10/22/2020
 */
public class PokemonBattle {

   /**
   * Create a Pokemon object and return it.
   * Prompts the user for input to decide how to create the pokemon.
   * Borrowed from etmp assignment 4
   * @param player The name of the player
   * @return the new Pokemon Object
   */
   public static Pokemon makePokemon(String player) {
      // available species
      String[] species = {
         "Bulbasaur", "Ivysaur", "Venusaur",
         "Charmander", "Charmeleon", "Charizard",
         "Squirtle", "Wartortle", "Blastoise"
      };
      // variables for reading user input
      Scanner pokeScanner = new Scanner(System.in);
      String userInput = new String("");
      String speciesChoice = new String("");
      String name = new String("");
      boolean makingPokemon = true;
      // the pokemon to be returned
      Pokemon p = null;
      
      while (makingPokemon) {
         // prompt for the species
         System.out.println("\nChoose a Pokemon for " + player + ": ");
         for (int i = 0; i < species.length; i++) {
            System.out.println((i + 1) + " " + " for " + species[i]);
         }
         // read input from user and trim whitespace
         userInput = pokeScanner.nextLine();
         speciesChoice = userInput.trim();
         
         switch (speciesChoice) {
            case "1":
               p = new Bulbasaur();
               makingPokemon = false;
               break;
            case "2":
               p = new Ivysaur();
               makingPokemon = false;
               break;
            case "3":
               p = new Venusaur();
               makingPokemon = false;
               break;
            case "4":
               p = new Charmander();
               makingPokemon = false;
               break;
            case "5":
               p = new Charmeleon();
               makingPokemon = false;
               break;
            case "6":
               p = new Charizard();
               makingPokemon = false;
               break;
            case "7":
               p = new Squirtle();
               makingPokemon = false;
               break;
            case "8":
               p = new Wartortle();
               makingPokemon = false;
               break;
            case "9":
               p = new Blastoise();
               makingPokemon = false;
               break;
            default:
               System.out.println("You choose an invalid species!");
               continue;    
         }
         
         // prompt about the name
         boolean gettingName = true;
         while (gettingName) {
            System.out.print("Does the Pokemon have a name (Y/N)?: ");
            userInput = pokeScanner.nextLine();
            userInput = userInput.trim().toUpperCase();
              
            switch (userInput) {
               case "Y":
                  // Prompt for the name and read the input string
                  System.out.print("What is the Pokemon's name?: ");
                  userInput = pokeScanner.nextLine();
                  name = userInput.trim();
                  gettingName = false;
                  break;
               case "N":
                  // The user doesn't care to input a name
                  gettingName = false;
                  break;
               default:
                  System.out.println("Invalid Input: please enter (Y/N)");
                  break;
            }
         }
      }
      // conditional for whether we have a name
      if (!name.equals("")) {
         p.setName(name);
      }
      return p;
   }  
   
   /**
    * Pokemon battle phase 2.
    * @param player1 for first person picking the pokemon
    * @param player2 for the second person picking the pokemon
    */
   public static void battle(Pokemon player1, Pokemon player2) {
      boolean gameOver = false;
      Scanner scan = new Scanner(System.in);
      Random turnGen = new Random();
      String chooseAtk = "";
      String attack = "";
      int opponentIndex = 0;
      // Arrays for storing energy and name of each player
      int[] playerEnergy = {0, 0};
      String[] players = {"Player 1", "Player 2"};
      Pokemon[] playerPokemon = {player1, player2};
      // Choose who goes first randomly
      int playerTurn = turnGen.nextInt(2);
     
      while (!gameOver) {  
         // Get the pokemon for the current playerTurn
         Pokemon current = playerPokemon[playerTurn];
         Pokemon opponent = playerPokemon[(playerTurn + 1) % 2];
         // Print out which player's turn we are on
         System.out.println();
         System.out.println(players[playerTurn] + "'s turn!");       
         System.out.println("-------------------------------------");
         System.out.println("Pokemon HP: " + current.getHP()
             + "\nYour attack energy: " + playerEnergy[playerTurn] 
             + "\nEnemy's HP: " + opponent.getHP());
         System.out.println("\nWhat would you like to do");
         System.out.println("1. FastAttack"
             + "\n2. Special Attack (3 energy)"
             + "\n3. Pass to build energy");
         
         chooseAtk = scan.nextLine();

         switch (chooseAtk) {
            case "1":
               attack = current.performFastAttack(opponent);
               System.out.println(attack);
               break;
            case "2":
               if (playerEnergy[playerTurn] < 3) {
                  System.out.println("\nNot enough energy to perform special attack");
                  System.out.println("Automatic powerup");
                  playerEnergy[playerTurn]++;
                  System.out.println(
                      "Current energy level: " + playerEnergy[playerTurn]
                  );
               } else {
                  System.out.println("\nPerform special attack");
                  attack = current.performSpecialAttack(opponent);
                  playerEnergy[playerTurn] -= 3;
                  System.out.println(attack);
               } // close if 
               break;
            case "3":
               System.out.println("\nStore energy");
               playerEnergy[playerTurn]++;
               System.out.println("Current energy level: " + playerEnergy[playerTurn]);
               break;
            default :
               System.out.println("\nInvalid option");
               break;
         } // close switch
         // check for endgame condition
         opponentIndex = (playerTurn + 1) % 2;
         gameOver = playerPokemon[opponentIndex].getHP() == 0;    
         // change the player turn
         playerTurn = (playerTurn + 1) % 2;   
      } // close while
      System.out.println();
      System.out.println(
          playerPokemon[opponentIndex].getName() + " was knocked out!"
      );
      System.out.println(
          playerPokemon[opponentIndex].getName() + " fainted"
      );
      System.out.println(players[opponentIndex] + " has lost");
   } // close method 
   
   /**
   * Main method of PokemonBattle simulation.
   * @param args The commandline arguments
   */
   public static void main(String[] args) {
      String gameOver = "  _____            __  __  ______    "
          + "____ __      __ ______  _____  \n"
          + " / ____|    /\\    |  \\/  ||  _"
          + "___|  / __ \\\\ \\    / /|  ____||  __ \\ \n"
          + "| |  __    /  \\   | \\  / || |__    | |"
          + "  | |\\ \\  / / | |__   | |__) |\n"
          + "| | |_ |  / /\\ \\  | |\\/| ||  __|   | |"
          + "  | | \\ \\/ /  |  __|  |  _  / \n"
          + "| |__| | / ____ \\ | |  | || |____  | |"
          + "__| |  \\  /   | |____ | | \\ \\ \n"
          + " \\_____|/_/    \\_\\|_|  |_||______|  \\__"
          + "__/    \\/    |______||_|  \\_\\\n";
      // Array for keeping track of players
      String[] players = {"Player 1", "Player 2"};
      // Each player has a pokemon
      Pokemon player1 = null;
      Pokemon player2 = null;
      // Have player 1 choose their pokemon
      player1 = makePokemon("Player 1");
      // Print message
      System.out.println("\nPlayer 1 chose: ");
      System.out.println(player1.toString());
      // Have player 2 choose their pokemon
      player2 = makePokemon("Player 2");
      // Print message
      System.out.println("\nPlayer 2 chose: ");
      System.out.println(player2.toString());
      
      // Game Phase 2
      battle(player1, player2);
      
      // Phase three.
      System.out.println(gameOver);
      if (player1.getHP() == 0) {
         System.out.println("\n Player 2 wins!!! Congratulations!");
         System.out.println(" Try a different strategy next time Player 1.");
         System.out.println(" Next win can be yours ;)");
      } else if (player2.getHP() == 0) {
         System.out.println("\n Player 1 wins!!! Congratulations!");
         System.out.println(" Try a different strategy next time Player 2.");
         System.out.println(" Next win can be yours ;)");
      }    
   }
}




