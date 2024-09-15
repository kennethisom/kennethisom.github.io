---
layout: default
---

# Breakdown of 6502 Build

## Primary Goals and Objectives

* Build a functional computer with screen, storage, keyboard, extra peripherals capabilities, and perhaps basic networking. 
* Learn how to use various pieces of hardware instead of doing everything in software
* Better understand OS/BIOS fundamentals
* Learn signal processing (SPI/UART/I2C/USB/Network)
* Learn how to manage timing needs of different components
* Learn how to effectively use datasheets
* Have fun learning

## Phase 1 - Build out a replica of Ben Eater's basic 6502 computer

The goal in this initial stage is to get the ball rolling.  Sometimes the best way to tell if you understand a concept is to try to make use of it.  This typically exposes where you have gaps in your knowledge.  I did however decide that I wanted to deviate in a couple of key areas.

First while I understood Ben's reasoning that 16 KB of RAM really should be plenty for this style of computer along with his cost argument, I didn't like the idea of having the memory mapping solution that wasted so much of the memory space.  So after researching alternative options I decided to roll my own memory mapping solution making use of a PLD.

The components for this stage:

* 65C02 Processor
* AT28C256 EEPROM
* 62256 SRAM
* 65C22 VIA
* ATF22V10C (PLD)
* 1 Mhz Active Crystal
* 2x16 LCD Display

To quickly demonstrate that wiring was successful, I planned to make use of one of Ben's programs from his video series.

## Phase 2 - Add in support for RS232 for I/O and get Wozmon working

This stage is intended to be a quick follow on to make sure I have an early means of doing I/O.  I intend to follow Ben's example fairly closely at this point. This will make use of the 65C51 and MAX232 chips for RS232 implementation.  Will make use of Wozmon adapted by Ben eater with a couple small adjustments to fit the adjustments made to the memory mapping from Phase 1.

## Phase 3 - Implement a PS/2 Keyboard Interface to use in place of RS232 for input

Adding PS/2 Keyboard support will be another deviation from Ben's original implementation. I decided to go the route of creating a more robust PS/2 interface using an AT microcontroller.  Originally I wanted to make use of an ATTINY85 combined with a 74HC595, but due to the increased difficulty associated with debugging this style of microcontroller, I opted to start with the ATMEGA328PU instead for the initial implementation.  This microcontroller will be responsible for directly interfacing with the PS/2 keyboard, interpreting character into their ASCII format, managing control codes.  At this time my intention is to interface with the 6502 via the 6522 interface adapter.

I will likely come back to the ATTINY85 solution later on and depending on how the project goes I may even attempt later on to achieve a fully hardware based solution and remove the microcontroller altogether.

## Phase 4 - Implement VGA support

I considered following Ben's example to implement this purely out of hardware also, though with gray scale support initially instead of color.  But I later decided that in the interest of learning how to interface graphics processing with an 8-bit computer that I would instead make use of a Raspberry PI Pico to handle the video processing and display.  Here again I may come back at a later time to explore a non-microcontroller solution, but time will tell.

After some initial research, while it seems like an era-true solution may not really be feasible (other than buying used/salvaged parts), it does seem like a common chip, the TMS9918A, is very well documented.  So my plan is to try and create my microcontroller solution in a way that it will mimic how that chip worked at least from an external interface perspective.

## Phase 5 - Add support for flash/external storage

One aspect to Ben's design that I felt was lacking was a convenient way to introduce new programs into the computer that didn't involve copy/pasting program over a serial connection or by yanking the ROM chip out to program it each time (though I have plans to make use of a ZIF socket to make the latter easier).  I'm planning on attempting to make use of a micro-SD flash connection to facilitate this.  It seems as though others have been able to achieve this though I definitely have a lot to learn before I'll be able to pull it off myself.

## Phase 6 - Build out a basic operating system

At this point, things start to get a little more nebulous.  I don't have exact goals in mind here yet but before moving too much further along, I want to make sure I've spent the time to build out some sort of half-way decent OS even if it's very basic in the beginning.  I have a ways to go before I get to this point, so I'm certain this effort will take better shape before I get to this point.

## Phase 7+ - Begin exploring

I feel that the first 6 phases mark the completion of what will be a fairly decent 8-bit computer.  The question then becomes, what will I do with it.  My hope is to continue to leverage it for the purposes of learning new skills and knowledge.  With that in mind, here are some of the ideas I may pursue at this point in the project:

  * Memory Banking
  * Wider/less-specialized support for various interface protocols (SPI/UART/I2C/USB/Network/Blu tooth)
  * Create a Peripheral System for Easy Expansion (possibly combined with the previous bullet point)
  * Multi Processor and/or trying out the 68C816 Processor
  * Faster clock speed
  * Create a PCB Version
  * ...