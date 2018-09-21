
Created on: Sept 16, 2018 

Last Edited: Sept 20, 2018 

Author: Nick Woodward

The purpose of this code is to turn on an LED on a button press and remain on until a button is pressed again. The boards chosen for this part of the lab was the MSP430G2553 and the MSP432P401R. Below, each variable and function is listed and described based on its purpose within the code:

## Registers: 

WDTCTL = WDTPW | WDTHOLD; //The purpose of this line is to shut off the watchdog timer to prevent unwanted an unwanted processor reset.

## Variables:

#define BUTTON Bit3 //Bit 3 is defined and used in the code as BUTTON.

  P1DIR = 0X40; // Pin 1.7 is set as the output
  
  P1REN = BUTTON; // Pull Up/ Pull Down resistors are enabled on Bit 3
  
  P1OUT = BUTTON; // Pull up resistor is chosen on Bit 3
  
  
 ## Functions:

  if((P1IN & BUTTON) == 0x00) //If the button (BIT3) is pressed, it becomes 0, causing this statement to be true and proceed to the delayed cycles.
  
 
  __delay_cycles(5000); //Delays reading on button to remove the inconsistinces of the button press
  
  if((P1IN & BUTTON) == 0x00) // If the button is still pressed, then it becomes 0 and causes this statement to become true, proceeding to the next step
  
  P1OUT ^= 0X40; //Toggles the LED on or off
  
  while((P1IN & BUTTON) == 0x00); //BUTTON is always 1 due to pull up resistor, so it gets trapped in the while loop until P1IN is pressed (becomes 0)
 
 
 
In order for the above code to work on the MSP432P401R, a few bits must be renamed. Below are a few lines of code that must be changed in order for it to work. In addition to the below code to be changed, the top of the code (#include) must also be altered to the correct board!

#include <msp432p401r.h> //Changed in order to incopreator the correct board's header file.
 
if((P1IN & BUTTON) == 0x00) becomes if((P1IN & BIT1) == 0x00) //BUTTON (Bit 3) becomes Bit 1 to work with the MSP432P401R

P1OUT ^= 0X40 becomes P1OUT ^= 0X01; //Pin 1.0 (Bit 0) becomes the LED toggle bit

P1DIR = 0X01; //Pin 1.0 is set as the output

P1REN = BIT1; //Pull Up/Pull Down resistors are enabled on Bit 1

P1OUT = BIT1; //Pull up resistor is chosen on Bit 1

## Button Blink on MSP430G2553

<iframe src="https://giphy.com/embed/3E3EIWT1DnrnvMoDUp" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/3E3EIWT1DnrnvMoDUp">via GIPHY</a></p>

## Button Blink on MSP432P401R

<iframe src="https://giphy.com/embed/35P0pu0bGKYlY9jTGH" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/35P0pu0bGKYlY9jTGH">via GIPHY</a></p>


 
