## Approach

- What was your approach to the problem and what is your solution?
- You should also include approaches that did not work.

##Basic approach

Use switches which act as hammar.
LEDs as Moles

The output of the both the score and time will display on a seven segment display.

## Modules

1:A Score counter 
2:A Time counter
3:Binary to BCD converter
4:Output on Seven Segment Display

## Block Diagram

<p align="center">
  <img src="https://lh3.google.com/u/0/d/1TW5dVH_bIU5aARj2I9uMmL4-0ItDH6Xi=w1920-h942-iv1" width="1920" title="hover text">
  
</p>

## Detail Working

Score Count Counting the number of whacks on the mole
Input is basically 16 Switches and we are using system clock here which basically outputs 16 leds
It just randomnly lights up the LED which represents moles, and it also keep records of Score Count
Everytime the led is light up and adjacent switch is fliped the counter goes up by one that keeps record of score.
Time Counter is basically takes one sec clock, Which is fed into timer Count, timer start with 2o goes all the way
to zero.
The Score count and Timer is than fed to Binary to BCD converter Which than fed to mux and than t0 7 segment display.
Whats Gona happen is i have a slow clock here 100Hz, i will use this clock to toggel four seven segment display.
Every 10ms the two bit counter, itilay it set to value of 00 which is fed into mux, the timerones which go pass the mux
goes to BCD 7 seg and 00 is also fed into Decoder, one of seven segment will be on and rest will not and whatever the timer 
one will be Disaplayed on the oned Seven 7 segement display. Again After 10ms bit counter goes to 01 and another 7 segment 
display will on and it will display timer 10s there, Similarly it will display Score count
