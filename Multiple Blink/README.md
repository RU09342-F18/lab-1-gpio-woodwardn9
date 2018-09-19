# Multiple Blink
Now that we have blinked at least 1 LED, what about blinking multiple LEDS at the same time? The minimum that you need to develop is blinking at least two LEDs at two different rates. Although I am not going to give you a speed, you should probably pick a rate which is visible to a standard human. I really hope that you take this further and perform some of the extra work for this part of the lab exercise.


# YOU NEED TO CREATE THE FOLLOWING FOLDERS
* MSP430G2553
* MSP(FILL IN WITH WHAT YOU ARE USING)

## README
Remember to replace this README with your README once you are ready to submit. I would recommend either making a copy of this file or taking a screen shot. There might be a copy of all of these README's in a folder on the top level depending on the exercise.

## Extra Work
When you take a look at the development boards, you are limited to what is built into the platform.

### Even More LEDs
Since up to this point you should have hopefully noticed that you are simply just controlling each pin on your processor. So... what is keeping you from putting an LED on each pin? Can you actually control the speed of each of these LEDs?

### Patterned Lights
If you can control a ton of LEDs, what is keeping you from having a little fun? Why not try and make something like a moving face or other moving object in lights. *CAUTION* I would only do this if you have finished the rest of the lab.

### UART Pattern Control
If you have been using UART, could you set which LEDs are on or off based off some UART command? Would you want to send an Array over UART such as [1 0 1 0] or would you want to send a byte that corresponds to the status? Can you not only say which LEDs are on, but also tell them to blink at a particular rate if they were on (so LED1 Blink every 100ms)?


Created on: Sept 10, 2018
Last Edited: Sept 10, 2018
Author: Nick Woodward

The purpose of this code is to blink two LEDs on two seperate boards. The boards chosen for this part of the lab was the MSP430G2553 and the MSP430F5529LP. Below, each variable and function is listed and described based on its purpose within the code:

Registers:
WDTCTL = WDTPW | WDTHOLD;
//The purpose of this line is to shut off the watchdog timer to prevent unwanted an unwanted processor reset.

P1DIR |= 0X41;    
//The purpose of this line is to set Pin 1 and Pin 0 to be 1 without disturbing or manipulating the values of the other pins. This is achieved by OR'ing P1DIR with 0x41, which is 0b01000001 in binary. 

P1OUT = 0X41; 
//The purpose of this line is to set Pin 1 and Pin 0 to are set to be 1 to start without disturbing or manipulating the values of the other pins. This is achieved by OR'ing P1OUT with 0x41, which is 0b01000001 is binary.


