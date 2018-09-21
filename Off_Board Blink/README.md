

Created on: Sept 16, 2018

Last Edited: Sept 20, 2018

Author: Nick Woodward

The purpose of this code is to take the G2553 processor off of the dev board and to run a blinking light code successfully on a breadboard. In order to properly do this, the processor must be fit to the breadboard and supplied the correct voltage. Next, a RESET was created for the processor using a pull up resistor, a 100 Picofarad capacitor, and a switch. Lastly, pins 1.0 and 1.6 are connected to two LEDs and will blink according to the code below. 

Due to the similarity of the offboardblink and the multi blink utilizing the MSP430G2553, the same code can be utilized to achieve the desired results on the breadboard build. 

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

## MSP430G2553 Offboard Demo

<iframe src="https://giphy.com/embed/1zkHFecuct7DjzUiU9" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/1zkHFecuct7DjzUiU9">via GIPHY</a></p>


