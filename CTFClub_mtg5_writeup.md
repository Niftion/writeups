# Writeup for CTF Club Challenge #5
## Title: revpaperscissors

### Flag 1
First, make sure you have Ghidra installed! Once you do, decompile the file. Then, go to the symbol tree such that you may navigate to the main function. From there, you can discover: the moves that the bot plays are hard-coded into the program! This makes winning pretty straightforward: use this as a reference as for what moves to play, then win the game/flag.

*(The one catch for this: the "rock" string was referenced instead of decompiled into a proper string; this makes it appear as 4x chars with a null terminator at the end of them,,, recall that this is just what a string is though! We can, from the null terminator, realize that it is "rock" and proceed to decompiling the program as usual...)*

### Flag 2
For this flag, the initial process is, for the most part, the same as for flag 1: decompile in Ghidra, go to symbol tree, enter main function,,, ah, cool- We can find that the program uses your name to calculate how it will play its moves! While the exposed function's equation *could* be reverse-engineered to determine the bot's play-order for any name, this was concluded by our team to (respectfully) be a waste of time. 

THUS: our group instead opted to use a static name, and to iterate attempts till the correct solution path was determined, and to thereafter win the game/flag (i.e., we brute forced it lol ;P ). But, it was in an offline environment, so imo it was completely within safe bounds to brute force.