---
layout: project
type: project
image: images/PokemonBall.png
title: Pokemon Battle
permalink: projects/PokemonBattle
date: 2021-09-02
labels:
  - Pokemon
  - Gaming
  - C++
summary: My team developed a Pokemon battle game by using the Java programming language in the fall semester of 2020. 
---

<img class="ui medium right floated rounded image" src="/images/PokemonBattle.png">

In the fall semester of school year 2020, my ICS 211 partner Eva Teresa and I developed a gaming sofeware program that supports two players and generated Pokemons with choosen species and choosen name but random HP value. The program allows you to catch different Pokemons with different characteristics like "Fire", "Water", "Poison", etc and different skills due to species, which may affect the battle outcome depends on the enermy's characteristics.

<img class="ui medium right floated rounded image" src="/images/TypeAttackEffectivenessChart.jpg">

For this project, Eva and I were in charged for almost every part of it because it was such a important and difficult project at the time to us. We shared opinions from genertating Pokemons, choose species, name the Pokemons, to settle players, the order of which player goes first, and how skill attcks is going to affect enermy's HP, and the game over screen. We both learned a lot of how Java can be running in one program but with many different related files.

The following code is partial of my coding for the Pokemon project in Java  
      
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
