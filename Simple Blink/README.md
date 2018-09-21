Created on: Sept 16, 2018

Last Edited: Sept 21, 2018

Author: Nick Woodward

The purpose of this code is to blink one LED on two seperate boards. The boards chosen for this part of the lab was the MSP430G2553 and the MSP430FR2311. Below, each variable and function is listed and described based on its purpose within the code:

## Registers:

 WDTCTL = WDTPW | WDTHOLD;// Stop watchdog timer

    P1DIR |= 0X01;    //Pin 1.0 is set as an output

    P1OUT = 0X01; //Pin 1.0 is set as 1 (on) to start


## Variables: 

unsigned int a;

//This variable is created to be incremented by 1 in a for loop.

## Function:

        P1OUT ^= 0X01;
        
        //The LED is either toggled on or off
        
        for (a = 0; a < 10000; a++){}
        
        // This loop increments variable a until it reaches 10000, then, it breaks out of the loop and toggles P1OUT ^= 0x01 (acts as a delay cycle function)

Above is the framework of for the MSP430G2553. In order to use this code successfully on the MSP430FR2311, the following changes below must be made:

PM5CTL0 &= ~LOCKLPM5; 

//This line of code must be added to unlock the GPIO functionality of the MSP430FR2311.

#include <msp430g2553> becomes #include <msp430fr2311.h>

                            
                               
  ## SIngle Blink on MSP430G2553
  
  <iframe src="https://giphy.com/embed/3l6DRgewbpjEjEZg9t" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/3l6DRgewbpjEjEZg9t">via GIPHY</a></p>
  
  ## Single Blink on MSP430F5529LP
  
  <iframe src="https://giphy.com/embed/YiJPjTid1KcOryWnp6" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/YiJPjTid1KcOryWnp6">via GIPHY</a></p>
  
  
