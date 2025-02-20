---
layout: default
title: Bonus
group: navigation
---

## ELEC 327: Digital Systems Laboratory (Spring 2018) Bonus Projects

Bonus projects should be submitted via email, and critically, with a Piazza post containing a
YouTube video demostrating the projet. This way your fellow classmates will see what bonus
projects are being done.

---

### Accelerometer and LED circle board

The EAGLE CAD design files are found in the `Bonus/` directory of the ELEC327 github
repository. Here is a link to the [schematic
](https://raw.githubusercontent.com/ckemere/ELEC327/master/Bonus/Bonus.sch) and one to the
[board](https://raw.githubusercontent.com/ckemere/ELEC327/master/Bonus/Bonus.brd). Note that
the accelerometer is mis-wired - the MISO and MOSI wires are reversed. You can fix this by
cutting these traces and soldering on airwires. 

  1. **[1 point for whoever is first]** - Make all 24 lights light up. Create a youtube video 
  and post to campus. The first timestamped video will be worth 1 bonus point. (Note that 
  there may be a problem with the PCB!)

  1. **[1 - 2 points]** - implement a clock.  The aesthetics of the clock and code will
  determine total scorer. Example questions: is there a second hand that ticks? a separate hour
  and minute hand?  is there some sort of PWM-like intensity modulation? does the device
  calibrate and use the VLO for low power?

  1. **[3 point]** - create a proof-of-concept accelerometer device (requiring the hardware
  airwire fix described above). Get data from the accelerometer and display it somehow with the
  LEDs. (Alternatively, an extra point will be applied for the following bonuses...)

  1. **[2 points]** - implement a tilt sensor in which the LED closest and furthest from the ground
  light up. The button should be used to make the device sleep/wake up. This will require that
  you (a) properly solder the MSP430 and 3 shift register chips to drive the LEDs and (b)
  interface with the accelerometer to read out the gravity vector, and (c) appropriately
  compute its direction.

  2. **[up to 2 points]** - derive optimized integer routines for (1) so that the update speed can be
  fast. Obviously, this also requires doing (1).

  3. **[up to 5 points]** - do something cool that links motion to the LEDs.


---

### Lab 1 Bonus - Color cyle Morse Code

**[0.25 points]** - Make sure that your implementation of [Lab1 (Lab2 in 2021) morse code blinking
project](lab2/) is using one of the Timer interrupts for character timing. Display the Morse
code message on the RGB led of the Launchpad. Using a different timer interrupt, configure the
color of the RGB LED to cycle through the rainbow (at least 16 different colors) while the
message is being flashed. The color cycling should be faster than the character timing.

---

### Lab 1 Bonus - Decode Morse Code

**[2-6 points]** - **MVP (2 points):** after implementing the [Lab1 morse code blinking
project](lab1/), connect an input GPIO pin of a second MSP430 to the LED driving pin on the
first one (you'll presumably also need to connect the ground lines). Track the signal on this
pin to infer dashes, dots, and spaces. Decode these to characters, which can be viewed in
memory in the debugger. **Extra points:** (a) Implement a serial interface to see the translated
characters. (b) Figure out how to synchronize the clock over a large range of frequencies. You
can assume that the message is limited to 3-4 letters and repeats for a long time. (c) Use a
photodiode or other light sensor to get the signal rather than a wire.

---

### Lab 3 Bonus - Create a large digital clock or other fun things with the handout PCB

**[1 point]** - Implement a 2 digit stopwatch. With the display PCB oriented
horizontally, implement a 2-digit display, and have it count hundredths of seconds. Use
the two buttons as a start/stop and reset. When the time is greater than 9.9 seconds,
while running, the display should show only seconds. When stopped, it should scroll the 
full three-digit time.

**[1-2 points]** - Implement a multi-PCB clock. Use the header pins on the sides of the PCB to 
chain 2, 4 or 6 of the display PCBs together. Program them such that the rightmost one controls
the timing of the rest of the PCBs in the chain. Come up with an interesting way to use one pair 
of buttons to control the full display, for example, to set the time, or to change the intensity.

**[0.5-2 points]** - Create some sort of interesting game involving the display and the buttons
button. Optional: implement a _long press_ to send the device into LPM4 (like turning off). 

---

### Lab 4-5 Bonus - Make your own PCB and related ideas

__Note that all of these are PCB-related bonuses. You can create a second PCB for Lab 4
or submit these designs as part of the midterm or final project board runs.
Alternatively, you could have them manufactured yourself. Some of the bonuses are obviously
exclusive (i.e., one PCB couldn't do everything); the rest should be considered additive
(if you make one PCB that satisfies multiple bonuses, you get them all.)__

<div class="alert alert-danger" role="alert">
<b>Keep in mind the lead time for these services can be as much as two weeks!</b>
</div>

**[0.5 points]** - Design and manufacture a PCB that includes nice features in silkscreen
and/or soldermask layers.

<div class="alert alert-info" role="alert">
<b>[1-3 points]</b> - Design, manunfacture, populate, and program a board that uses an MSP430 to do
something interesting. In particular, the PCB design should be in the shape of an Owl. If your design
is chosen by the judges, it will be printed on a t-shirt for the ECE department!
</div>

**[1 point]** - Use the 32-pin QFN package of the MSP430 rather than the 20 pin one provided.
You will have to find or create a proper EAGLE part for this device, which you should add to
the ELEC327 library and generate a pull-request on github. Manufacture, populate, and
program the board.

**[1 point]** - Add a button (or capacitive touch pad!) to the Lab 4 device to be used to go 
into LPM4 as in Lab 2.  You may use a capacitor (and resistor if desired) to debounce, or implement 
some  sort of software debouncing.

**[1-3 points]** - Add the necessary components to use this
[thermistor](https://www.digikey.com/product-detail/en/ametherm/DG103395/570-1177-ND/5967491)
to measure the temperature of a liquid. Note that you'll want to make a resistor divider
circuit, with your ADC sampling the midpoint of the thermistor and a second resistor whos value
you should choose intelligently. Turn your thermodot into a drink temperature alarm, possibly
integrated into a cup. (For example, if the liquid is too hot to drink, display a red color and
flash.) A useful device would probably also have a power button as described above.

---

### Midterm Bonus - Better Simon

**[0.25 - 0.5 points]** - Make nice Youtube video showing your Simon game in action. Make sure that
"Rice" and "ELEC327" are in the tile or otherwise searchable. 
**Your demo video should show you playing through to a win, running the “Game Over - Win”
animation, and then pushing a button to restart and then playing through but making a mistake
to generate the “Game Over - Loss” animation.** More points will be given for higher production
quality, humor, or other aesthetics.


**[0.5 - 1 point each]** - Possible improvements or modifications for Simon:
  - Implement software debouncing. (This requires removing the capacitors. Please reach out ASAP if you want a Simon
    board without capacitors and I will mail it.)
  - Allow the user to select the level of difficulty - the timeout period and/or speed of initial
    sequence playing. You could implement this by which button is used to start the game after
    a reset.
  - Implement the reset functionality by requiring multiple buttons to be pressed
    simultaneously
  - Add double or triple button presses to the pattern
  - Do something interesting with the LEDs (i.e., using the color channels creatively or
    specifying interesting patterns)
  - Track fastest performance (i.e., how fast the entire game goes) and reward the player for
    beating their previous best
  - Use the PCB for something else in addition to Simon (e.g., a different game, a music
    sequencer) that is executed depending on some startup condtion.


---


