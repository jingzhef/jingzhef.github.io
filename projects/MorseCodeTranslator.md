---
layout: project
type: project
image: images/MorseCode.jpg
title: Morse Code Translator
permalink: projects/MorseCodeTranslator
# All dates must be YYYY-MM-DD format!
date: 2021-09-02
labels:
  - C language 
  - Morse Code
  - Translator 
summary: A translator in alphabet for Morse Code.
---

This Morse Code Translator is one of my sofeware programming project i wrote in uhunix server for ICS 212 class, the purpose of it is to translate the morse code word into English alphabet by enter the Morse code symbols into the string.

<img class="ui medium right floated rounded image" src="/images/MorseCodeDefine.jpg">

From this project, I've learned about Morse code this famous method used in telecommunication to encode text characters in World War II. I was in charged of all the coding for this project and improved my C language skill by practice on this project.

The following code is my contribution to this project

/*
 * Morse Code Translator
 * Jingzhe Feng
 * 03/08/2021
 */
#include <stdio.h>

#include <ctype.h>

#include <string.h>

#define SIZE 36

const char *morse[SIZE] = {

    "0 ----- ",
    
    "1 .---- ",
    
    "2 ..--- ",
    
    "3 ...-- ",
    
    "4 ....- ",
    
    "5 ..... ",
    
    "6 -.... ",
    
    "7 --... ",
    
    "8 ---.. ",
    
    "9 ----. ",
    
    "a .- ",
    
    "b -... ",
    
    "c -.-. ",
    
    "d -.. ",
    "e . ",
    "f ..-. ",
    "g --. ",
    "h .... ",
    "i .. ",
    "j .--- ",
    "k -.- ",
    "l .-.. ",
    "m -- ",
    "n -. ",
    "o --- ",
    "p .--. ",
    "q --.- ",
    "r .-. ",
    "s ... ",
    "t - ",
    "u ..- ",
    "v ...- ",
    "w .-- ",
    "x -..- ",
    "y -.-- ",
    "z --.. ", 
};
int main(int argc, char *argv[]){
    int i = 0;
    
    int j = 0;
    
    int length = 0;
    
    //error checking  
    if(argc < 2) { //if the commandline is less than 2 that means nothing has been input
    
        puts("ERROR: You only typed the executable. Enter the Morse Code on the commandline.");
        
        return 0;
    } else {
    
    //loop through the commandline input
    for(i = 0; i < argc; i++ ){
    
    
        length = strlen(argv[i]); //length of the string in 'i' index

        //convert Morse Code to letter
        for (j = 0; j < SIZE; j++) {  
            if(length == (strlen(morse[j]) - 3)) { //take out the length of the space and letter in the string
                if(strncmp(morse[j] + 2, argv[i], length) == 0) { //start compare the similarity of two string
                    // +2 makes the string skiped the first letter and the space
                    printf("%c \n", morse[j][0]); //print out the first letter of the string.
                    } //close if 
                }//close if
            }//close for
        }//close for
     }//close if
    return 0;
} //close main


