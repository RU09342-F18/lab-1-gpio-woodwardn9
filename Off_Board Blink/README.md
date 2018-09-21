# Off Board Blink
Now that we have the whole blinking LED out of the way, why don't we try making things a little more convenient by taking the G2553 off the development board and into a breadboard. In addition to the software, your README needs to also contain a picture of your circuit with at least 2 LEDs blinking all on a breadboard and without a development board. This means that you will need:
* Proper power being supplied to the processor
* Proper Reset Circuitry
* Proper Bypass and Bulk Capacitors as needed

Please be advised that you can easily damage or destroy one of the pins on the MSP430 by applying the wrong voltage or attempting to draw too much current from it. Really check your design before you power up to ensure you do not need request another processor.

## "Do I need to use a power supply to power this thing?"
In the beginning part of the exercise, I would say that you can use the 5V/3.3V rails built into the development board by running wires. However, I would recommend looking into how to supply the processor from something like a battery or the power supply. You might want to look into different types of regulators. For example, your circuits may be powered off of a battery that is only 1.8V, or on a system that can only supply you with 13V.

## "What about the buttons and resistors and LEDS?"
You remember those parts bins in the back of the teaching labs? They contain most everything you will need to do this portion of the lab. You should really make a effort to try and replicate what is on those development boards on the breadboard so you can begin to see what is needed to design with a microcontroller. Mess around with different color LEDS and see if they behave the same as the simple Red LEDs.

# YOU NEED TO CREATE THE FOLLOWING FOLDER
* MSP430G2553

## Extra Work
Once you get to this point, you are pretty much set in terms of GPIO mastery getting the LEDs to blink, but there are some more exploratory tasks that you can do.

### Off-Board Programming
Do we need to keep re-inserting the MSP into the development board to program it, or is there some way to keep the chip in the circuit? For starters, try to connect the header which connects the debugger and emulator (that parts that is really dense in parts) to your chip on your board. You will need to look at the datasheets for the MSP430G2553 and the Launchpad itself to see where and how to connect to the programmer. Next, you should really look at using the JTAG connector that is also available on your board.

### UART/Button Control
Remember that stuff you did a few parts ago? Can you actually get all of that working again off of the development board? Can you control which lights are on, the speed they blink at, etc.


Created on: Sept 16, 2018

Last Edited: Sept 20, 2018

Author: Nick Woodward

The purpose of this code is to take the G2553 processor off of the dev board and to run a blinking light code successfully on a breadboard. In order to properly do this, the processor must be fit to the breadboard and supplied the correct voltage. Next, a RESET was created for the processor using a pull up resistor, a 100 Picofarad capacitor, and a switch. Lastly, pins 1.0 and 1.6 are connected to two LEDs and will blink according to the code below. 

Due to the similarity of the offboardblink and the multi blink utilizing the MSP430G2553, the same code can be utilized to achieve the desired results on the breadboard build. 

## Registers

WDTCTL = WDTPW | WDTHOLD; //The purpose of this line is to shut off the watchdog timer to prevent unwanted an unwanted processor reset.

P1DIR |= 0X41;
//The purpose of this line is to set Pin 1.0 and Pin 1.6 to be 1 without disturbing or manipulating the values of the other pins. This is achieved by OR'ing P1DIR with 0x41, which is 0b01000001 in binary.

P1OUT = 0X41; //The purpose of this line is to set Pin 1.0 and Pin 1.6 to be 1 to start without disturbing or manipulating the values of the other pins. This is achieved by OR'ing P1OUT with 0x41, which is 0b01000001 is binary.

## Variables

int timer1 = 0; int timer2 = 0;

//These two variables are created as timers that count up in increments of 1.

## Function

timer1 = (timer1 + 1) % 200; //Counts up to 500 if (timer1 == 0) //Divides timer by modulus 500. If the result is 0, than toggle LED on/off. { P1OUT ^= 0X40; //PIN 1.6 is toggled (Red LED) }


