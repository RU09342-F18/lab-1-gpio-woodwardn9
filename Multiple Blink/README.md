

Created on: Sept 16, 2018

Last Edited: Sept 21, 2018

Author: Nick Woodward

The purpose of this code is to blink two LEDs on two seperate boards. The boards chosen for this part of the lab was the MSP430G2553 and the MSP430F5529LP. Below, each variable and function is listed and described based on its purpose within the code:

## Registers:

WDTCTL = WDTPW | WDTHOLD;
//The purpose of this line is to shut off the watchdog timer to prevent unwanted an unwanted processor reset.

P1DIR |= 0X41; 

//The purpose of this line is to set Pin 1.6 and Pin 1.0 to be 1 without disturbing or manipulating the values of the other pins. This is achieved by OR'ing P1DIR with 0x41, which is 0b01000001 in binary. 


## Variables: 

int timer1 = 0;

int timer2 = 0;

//These two timer variables are created to count up in increments of 1.

## Function:

timer1 = (timer1 + 1) % 200; //Counts up to 500

        if (timer1 == 0) //Divides the timer by modulus 500. If the result is 0, than toggle LED on/off. 
        
        {
        
            P1OUT ^= 0X40; //PIN 1.6 is toggled (Red LED)
            
        }
        
timer2 = (timer2 + 1) % 1200; //Counts up to 1500

        if (timer2 == 0) //Divides timer by modulus 1500. If the result is 0, than toggle LED
        
                {
                
                    P1OUT ^= 0X01;  //PIN 1.0 is toggled (Green LED)
                    
                }

Above is the framework of for the MSP430G2553. In order to use this code successfully on the MSP430F5529LP, the following changes below must be made:

 <msp430g2553.h> is changed to <msp430.h>

  P1OUT ^= 0X40 is changed to  P1OUT ^= 0X01 //This line of code toggles PIN 0 (Red LED)
  
  P1OUT ^= 0X01 is changed to P4OUT ^= BIT7; //Green LED
  
  P1DIR |= 0X41; is changed to P1DIR |= 0X01 and P4DIR |= BIT7;    //Port 1.4 and 1.1 are altered to 1.0 and 4.8 in order for the MSP430F5529LP to work.
                            
                               
  ## Multiblink on MSP430G2553
  
  <iframe src="https://giphy.com/embed/wZCZQX8a9lBWJp63sP" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/wZCZQX8a9lBWJp63sP">via GIPHY</a></p>
  
  ## Multiblink on MSP430F5529LP
  
  <iframe src="https://giphy.com/embed/x49KAJ4CqSOopOSf8t" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/x49KAJ4CqSOopOSf8t">via GIPHY</a></p>
  
  
