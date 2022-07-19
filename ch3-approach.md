# Approach

- What was your approach to the problem and what is your solution?
- You should also include approaches that did not work.

## Basic approach

Use switches which act as hammar.
LEDs as Moles

The output of the both the score and time will display on a seven segment display.

## Main Modules

- A Score counter 
- A Time counter
- Binary to BCD converter
- Output on Seven Segment Display

## Block Diagram

<p align="center">
  <img src="https://lh3.google.com/u/0/d/1TW5dVH_bIU5aARj2I9uMmL4-0ItDH6Xi=w1920-h942-iv1" width="1920" title="hover text">
  
</p>

## Detail Working


- Input is basically 16 Switches and we are using system clock here which basically outputs 16 leds
-It just randomnly lights up the LED which represents moles, and it also keep records of Score Count.
- Everytime the led is light up and adjacent switch is fliped the counter goes up by one that keeps record of score.
- Time Counter is basically takes 1 sec clock, Which is fed into timer Count, timer start with 20 goes all the way to 0.
- The Score count and Timer is than fed to Binary to BCD converter Which than fed to mux and than t0 7 segment display.
- We used a slow clock here 100Hz to toggel four seven segment display which is fed to 
2 bit counter.
- After 10ms the two bit counter which is initially it set to value of 00 is fed into mux, the timer-ones which go pass to the mux and from there goes to BCD 7 seg and bit counter 00 is also fed into Decoder and one of seven segment will turn on and rest of them will not turn on and whatever the timer-one will be Disaplayed on the oned Seven 7 segement display.
- Again After 10ms bit counter goes to 01 and another 7 segment display will turn on and it will display timer 10s there.
- Similarly it will display Score count in similar fashion.
