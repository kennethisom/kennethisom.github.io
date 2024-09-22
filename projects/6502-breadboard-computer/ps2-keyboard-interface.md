---
layout: default
---

# PS/2 Keyboard Interface Controller

While initially I'm making use of an RS232 serial interface for my 6502 breadboard computer, I would eventually like to have direct display/input interfaces.  I decided to go with PS/2 for the keyboard interface since its protocol is relatively simple, and it seemed like a good starting point.

## V1 - 2 Shift Registers and Inverters

My initial intent was to implement a purely hardware solution similar to Ben Eater's PS/2 video using 2 shift registers along with a few inverter gates.  However, I ran into issues getting his solution working.  I believe it was largely a timing issue, but as I contemplated whether to continue with pure hardware vs an alternative approach, I ended up deciding that while I may come back in the future to figure out what was causing my issue, sticking with a hardware solution wasn't necessarily critical for my goals with this project.

My main goal is learning (and having fun since this is a hobby after all) and while I wasn't able to get this first option working, I did feel that I had gained enough knowledge that I felt comfortable that I understood how this solution was supposed to work.  So I decided to move on to an alternate approach for the sake of keeping the project moving along rather than getting bogged down at this point.

## V2 - ATTINY85 and a Shift Register

My next goal while deviating from pure hardware was to still not become too reliant on software to solve this issue.  For that goal I felt like the ATTINY85 was a good compromise.  With only 5-6 pins available for I/O, I needed to be thoughtful and creative in how I created this interface.  My initial challenge here was to gain a deeper understanding of AVR programming including interrupts and timers.  While I felt like I had a solid concept implemented, when I went to test my solution I was not getting the results that I expected.  Unfortunately in order to proceed further some level of runtime debugging was going to be necessary.

Which brings me to the next challenge I encountered.  My choice of a solution that had such limited I/O capabilities also meant debugging was a bit more challenging than with other microcontroller options with more I/O availability.  I think the most promising option here given that I needed all the I/O I had available to implement my solution would have been to enable debugwire on the chip and connect it with a debugger on my computer.  But I began to grow concerned that I would get bogged down with this setup, so I decided to make a temporary pivot again for the sake of getting something working.  Ultimately I plan to return to this solution, but I've decided for the short term as I'm still new with AVR programming that I will focus first on the path of least resistance.

## V1.99 - ATMEGA328P

I was torn at this point between making use of the ATTINY84 which has a few more I/O pins and the ATMEGA328P which has even more I/O.  I quickly landed on the latter since my end goal is to return to the ATTINY85 and this is just a temporary solution to keep moving forward. Going with the ATMEGA would mean I could ditch the shift register entirely and just focus on getting my code working correctly.  This part of the project is still in flight.  More updates will come hopefully in the near future.

## TODOs

* finish the project... obviously
* get all the code for each of these steps bundled up and in Github
* put together schematics and other details to make this part of the project repeatable