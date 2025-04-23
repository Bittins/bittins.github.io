---
layout: drum-machine
title: Sequencer
---

Coding is not my strong suit, so I admit that I have received advice on structure and general training from my computer scientist brother. Once I began getting the hang of it, however, I found myself really enjoying embedded programming. It’s very rewarding to program on this low of a level and see your code actually translate to physical signals.  
For this project I decided to use a generic STM32F103 dev board (often dubbed the “blue pill”) due to its cheap price to performance and wide availability.   
For inputs, I designed modular mechanical keyswitch boards which utilize shift registers to allow me to daisy-chain an arbitrary number of boards together. Each key has 8 buttons and 8 LEDs, and communication to the boards is done using something very similar to SPI, the only difference is I use the chip select pin as a shift register latch pin. This simple design lets me use hardware SPI rather than having to bitbang communication or having a more complex addressable communication system on each board.  
To control the drum triggers I again used shift registers. I decided to use the Eurorack standard because of the wide availability of parts for it, and it also gives me the option to use these modules separately from the drum machine.  
Accenting is an important feature in creating a more interesting and expressive sound. An accented beat plays louder than a non-accented beat. The way I have implemented this may be slightly odd but it allows the drum modules to be more widely compatible with other eurorack systems. Instead of modulating the voltage of the trigger itself, we add a separate control voltage input to each module, and the sequencer switches between normal and accented voltages in time with the corresponding trigger output. This also leaves the opportunity in the future to add a DAC per output to allow for even more expressive sequencing.  
