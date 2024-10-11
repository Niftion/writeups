# Writeup for CTF Club Challenge #1
## Title: arcade

### Dr. B. Breaker's Barely Bestirring Brick Breaker:
The variables to the website's game were exposed. so, in the JS terminal, simply set score = 1000; this allows the user to win the game upon death beacuse they have (obviously) earned the score of 1000.

### Dr. Ralph Fleur's Baffling Raffle:
So, going to be honest, this one kinda just worked; leaving each of the entries empty and pressing "Spin!" returned the flag. Looking at the code, I believe this was due to the fact that it wasn't expecting, well, *nothing* to compare against lol. Regardless, performing this operation returned the result.