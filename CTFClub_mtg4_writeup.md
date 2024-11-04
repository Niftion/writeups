# Writeup for CTF Club Challenge #4
## Title: scriptkid

### Flag 1
To solve, pull the plaintext strings out of the document using the command `strings -e l .\not_malware.dll`; this will reveal the base 64 string from the file. Once you have it, decode it from base64 to reveal the flag alongside the creds required to progress to the next flag!

### Flag 2
Log into the sftp server with the prior given credentials with the command `sftp -P 1304 realitysurf@scriptkid.ctf-league.osusec.org`. From here, cd to the ftp folder, then use the sftp command `get flag.txt Downloads` to download flag.txt. From here, `cat` the flag & you're good to go.
### Flag 3
The process for this flag is pretty straightforward:
1) Open Wireshark to start scanning for traffic
2) Run the robux generator exe file
3) Interact with the exe file and enter in your username & pass (or, probably a fake version of them lol)
4) After submitting the creds, go back to Wireshark & filter for http requests; you will find the creds being sent from your computer to a specific server...
5) Also, inside this Wireshark trace will be the flag!

### Flag 4
That trace from before seemed pretty significant... recall that our goal was to save Timmy, too! But, aha, wait: the database storing Timmy's creds was revealed in the http request being sent to the server from our computer! Recall from the PowerPoint slides that we can send requests to servers using the `curl` command... rebuilding the reference from the slides/restructuring it for our purposes, we get: `curl -X "DELETE"  http://scriptkidrev.ctf-league.osusec.org/credentials OK`! Entering this command into our terminal will send the "DELETE" request to the server, which will wipe all the data from it & save Timmy... horray!