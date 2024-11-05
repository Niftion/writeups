# Writeup for CTF Club Challenge #6
## Title: git_forensics

### Level 0
1) ssh into the repo with the starting creds, then cd into `my_repository`
2) `git status` to see a log of everything that's happened; you'll see `creds_level1.txt` in the history!
3) use `git restore creds_level1.txt` to restore the file
4) `cat` the file to reveal the creds for the next level

### Level 1
1) log in w/ the level 1 creds, then use `git status`; the creds will be revealed in the commit message

### Level 2
1) ssh into the new level with the creds from prior
2) cd into `my_repository`, then use `git status` to view commits
3) copy the commit `9e2746de3fab32b8a9c5c1becc905878d8da8b6f` and use `git checkout 9e2746de3fab32b8a9c5c1becc905878d8da8b6f` to switch to the commit
4) the creds will now be present in the directory; cd it to reveal the creds to progress to level 3!

### Level 3
1) ssh into the new level with the creds from prior
2) use `git branch` to view the branches; you will find an extra branch called `dontlookinhere`
3) switch to this branch with `git checkout dontlookinhere`
4) the creds file for the next level will be available in `creds_level2.txt`! (for some reason, this is not called `creds_level4.txt`)

### Level 4
1) ssh into the new level with the creds from prior
2) use git branch to view the branches; you will find an extra branch called `dontlookinhere`
3) switch to this branch with `git checkout dontlookinhere`
4) the creds file for the next level will be available in creds_level2.txt! (for some reason, this is not called `creds_level4.txt`)

### Level 5
1) ssh into the new level with the creds from prior
2) looking at all of the commits with `git blame`, we can see that a lot of them are made by `imacybercriminal`; in order to filter this for just Timmy's creds (or, i.e., to NOT view the cybercriminal's changes), we can use the following command:
`git blame creds_level2.txt | grep -v "imacybercriminal"`- this will reveal both the correct creds and the flag, and allow us to progress to the next flag

### Level 6
1) ssh into the new level with the creds from prior
2) once you're on the branch, cat the `secret_plan.txt` file for a hint
3) `git reflog` to show all previous changes on the whole git repo; this will reveal the hash for the prior commits on the file
4) After viewing the history from `reflog`, you will see that there are certain commits made to `secret_plan.txt` that changed it! Use `git checkout <priorHash>` to switch over to these prior commits & thereafter reveal the flag in the `HEAD` branch!

