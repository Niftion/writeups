# Writeup for CTF Club Challenge #2:
## Title: elevator

### Floor (start):
Use SSH to login with the given credentials. After logging in, use `cat creds_level1.txt` to return `creds` & `pass`.

*(Note: for all subsequent floors, assume you are SSHing into the next floor with the prior floor's returned creds. Additionally, assume we're using `cat` to read the `creds` & `pass` unless specified otherwise).*

### Floor 1:
This one is pretty straightforward: use `find ./ -name "*creds*"` to find the `creds` & `pass` files (it will return the location of the file that contains both).

### Floor 2:
Use `grep` to filter the Bible ~~(?! lmao)~~ to find where the `creds` & `pass` are stored within it. (Here is the command I ran: `grep "next user:" creds_level3.txt && grep "password:" creds_level3.txt`)

### Floor 3:
Use `chmod -x <filename>` to make the file executable. Execute to return `creds` & `pass`.

### Floor 4:
Use `ls -la` to search for hidden things in your current directory. After running this command... you will find a hidden directory! Enter this hidden directory, & `cat` its (also hidden) file to reveal the `creds` & `pass` for this floor.

### Floor 5:
`cat` the file as usual, but, hold on,, a caveat!:
<br><br>
\~weird formatting!\~ o.O
<br><br>
But, who wants to deal with that, amirite? So: `tab` to have the terminal return the correct formatting (the file requires (imo) elaborate escape sequences to properly be parsed. However, if you disagree & would like to *manually* type these escape sequences out, by all means please be my guest.. do you also use Arch?)

### Floor 6:
You are in Vim ~~(my condolences)~~. Type `:q!` (or an equivalent cmd, if you are a ProGamer:tm: Vim user). This command will allow you to exit Vim (~~Horray, you are free from the confines of that malbogian hell!)~~. Afterward, `cat` the flag as usual.

### Floor 7:
Run `cat ./flag.txt` (obtained from the hint in README) to return the flag & \~win\~!.
<br>
*(Note: I initially just copied the instructions from the README & called it a day, however upon writing this, I wasn't quite satisfied with this conclusion.. I was curious as to \~why\~ this worked. Looking at level 7's system more, I noticed that it was possible due to the fact that its root directory was exposed(?!) for my login creds. Prooobably not good for their system's security, but (lucky for me) this system's security is not my problem >:) )*

## Final Thoughts
GGs, this was a fun challenge. I really liked the 'floors'/'levels'~~/privilege escalation(?!)~~ format of it a lot. Definitely a step up in complexity from mtg1's, looking forward to next week's :P
<br>
Main takeaway was getting better at using the `grep` cmd; it's practical for a buncha other applications too, and I haven't known how to use it that well for them but NOW I do!! So: W.
<br>
Additionally..: this challenge has reminded me of how bad I am at Vim! xD
<br>
So: I'm going to resume my masochistic routine of learning it, too..! yayy..!
