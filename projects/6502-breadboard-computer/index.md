---
layout: default
---

# Building a 6502 Breadboard Computer

A while back I came across a fascinating project by a well known Youtuber, Ben Eater, in which he walks through the theory and process involved in building out a simple 8-bit breadboard computer built around the 6502 processor.  You can find this playlist [here](https://www.youtube.com/watch?v=LnzuMJLZRdU&list=PLowKtXNTBypFbtuVMUVXNR0z1mu7dp7eH) or visit his website [here](https://eater.net/6502).  I enjoyed his series quite a bit and set out to build my own 8-bit computer.  In some ways I'm following his design exactly and in others I've chosen to deviate.

## Basic Plan

For this build my objectives were primarily learning and getting my feet wet in the world of electronics at a lower level than is easily doable with other options like Arduino and Raspberry PI.  This project has the added benefit of scratching the nostalgia itch from my fond memories of tinkering with our family Apple IIe as a child. I chose to break this project into several phases to achieve this goal:

* Phase 1 - Build out a replica of Ben Eater's basic 6502 computer (sorta)
* Phase 2 - Add in support for RS232 for I/O and get Wozmon working (also part of Ben Eater's playlist)
* Phase 3 - Implement a PS/2 Keyboard Interface to use in place of RS232 for input
* Phase 4 - Implement VGA support
* Phase 5 - Add support for flash/external storage
* Phase 6 - Build out a basic operating system
* Phase 7+ - Begin exploring
  * Memory Banking
  * Support for various interface protocols (SPI/UART/I2C/USB/Network/Blu tooth)
  * Create a Peripheral System for Easy Expansion
  * Multi Processor
  * Faster clock speed
  * PCB Version
  * And potentially more

For a more detailed outline of what I'm planning on doing click [here](./breakdown.md)

# How it's Going

* [Building a PS/2 Keyboard Interface](./ps2-keyboard-interface.html)
* Using a Raspberry PI Pico as a VGA controller (Same Story)