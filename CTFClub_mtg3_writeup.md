# Writeup for CTF Club Challenge #3
## Title: super_memory

### Part 1
The gotcha: the map wraps around when we hit the lefthand side due to an overflow.

To get to the flag, then: we go to the top of the map, and parkour to the top of the cloud.

From the top of the cloud, we can jump over and bypass the world barrier on the left. Due to the map's wrap-around, we wrap past the righthand sides' prior boundary-wall and reach the flag.

(this was possible due to the fact that we could overflow the array for our position and make the game think we were on the other side of the map even tho we just did an overflow to get to it)


### Part 2
The letters each correspond to a certain ascii value. We need an exact money value to be able to pass the gate. Overflowing our inventory will turn our letter values into our money amount (it will combine each of their letter values, then output the number as our money amount). We can then use this value to bypass the gate and win the game.

So, with that being said: After you solve the main challenge & unlock all the gates normally:
1) Pick up "d" 3x, till the number $ amount is 100
2) Pick up the c
3) Pick up the a
4) Pick up the b
5) FINALLY, ONLY AT THE END: pick up a singular dollar.
6) You will then have exactly enough money to win!

(note: this works b/c of little endian & d being 1 off from the ascii value of e; picking up the 1 increments our ascii value by 1, making it an e, and thereafter making the money overflow the exact amount we need to win)

Another way to explain this:
The buffer for the wallet can be represented as 0000. 
So:
- for d the buffer went from 0 0 0 0 to 0 0 0 100. 
- c added 0 0 99 100 
- a added 0 97 99 100
- b added 98 97 99 100 
Each column is multiplied by the power of its corresponding index in the buffer. Once these values are calculated (and if performed correctly), the buffer shows as the value needed to pass the final gate and reach the flag.