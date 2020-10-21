---
permalink: /hackmd-day1/
---

# October CodeRefinery HackMD, day 1

## Links

- Course page: https://coderefinery.github.io/2020-10-20-online/
- Schedule: https://coderefinery.github.io/2020-10-20-online/#schedule


## Icebreaker

What's the most important thing you'd like to learn this week?
- To be more structured in my Code repositories
- How to properly use and understand git in its full potential +1
- I want to incorporate version control into my workflow, rather than just know what it is and how to use it +3
- I want to know what version control is and how to use it :) 
- Deeper knowledge about GIT. "Cherry picking and whatnot..." +1
- 
- How to make my "disorganized scripts" somewhat more organized (as adverised) - maybe this means documentation but maybe something else? +1
- Automated testing, branching/merging
- Testing and documentation +4
- VC and How to write modular code
- Documentation
- I want to be a good helper and try to combat my morning sleepiness. +2
- Good collaborative workflows.
- How to teach advanced concepts like modular code and sustainable development [name=x]
- How to collaborate in coding projects and have a structured coding workflow
 +4
 - Learn more about how to actually use git and not just know about that I should use it.
- 
- Merge Brain. Ascend. +1


## Introduction
https://github.com/coderefinery/workshop-intro/blob/master/README.md

- Is there a way to tell Zoom to inactivate the "yes" status after a while?
    - Instructors can remove it.... which somehow it's not working for me.
- Are we tagging questions with our names? 
    - You can, we recommend not because it's a public document.  We remove names before archiving it on the webpage.
- What green button? :)
    - In Zoom participant list (findable from bottom of screen)
    - Are we talking about Zoom-window?
    - yes
- What is the smartest way to structure code/notes/exercises for CodeRefinery? Should we make our own GitHub repo, or is this explained later?
    - Hm, you will end up with lots of small repos, for each lesson.  I'd make one directory and put all the various repos in there.
        - Thank you <3
    - How do you create a directory on github to put all repos in, please?
        - Ah.  I mean directory on local computer, on Github all repos are only under your own user, no other organization
        - Thank you.
    - Whenever it's an exercise on GitHub, we will be very explicit about what to do. On the computer I recommend to create a folder for the workshop and different sessions can be subfolders.
    - Another question regarding the directories. Do you recommend that the main folder is like "CodeRefinery", and then "Day 1", "Day 2", etc. etc?
- Might be worth surveying what kind of screen aspects people are using? That affects how the shared screen (and hence font size) gets seen under zoom.
    - :+1:


## git-intro
https://coderefinery.github.io/git-intro/

- What is the best way to use git with latex? My problem is that any change will be detected for the entire paragraph (because it is all on the same line). I.e. adding a comma will mark the entire paragraph as changed. (Could write a sentence on each line, but that seems rather inconvenient...)?
  - Very important here to wrap long lines. Editors can do that automatically and I auto-wrap long lines into shorter ones so that the "diffs" are more localized. (on vim: visual block, then gq)
  - 
  - But it's good to autowrap when writing. One needs to be a bit careful to not always autowrap text of others otherwise it may introduce changes you did not intend to do.
  - `git diff --word-diff` will show differences per word. Then you can keep paragraphs on a single line.
  - Someone once told me the interesting idea, "make a new line after every sentence."  I stil prefer the first suggestion, though.
    - good tip!
- What is the advantage of using git over github?
    - Git is a format and tool that can be used locally.  GitHub is a web-based system for git.  Github is always used with git, git can be used alone or with other systems.
    - If you have very sensitive code, you can use git locally with your team, without sending the code to github/gitlab/etc.
- Might mention things like Gitea which also let you selfhost github style service without other people's computers.
    - Good point
- why are there three "modified readme" commits in a row? Do you commit after each minor change? Why not combine the changes into one commit?
  - we will discuss this later but it's good to not put unrelated changes into one commit. this makes it easier to undo something without undoing something unrelated.
  - if you have heard of `git cherry-pick`, somebody told me a good advice: "a good size of a commit is that it should be cherry-pickable" (don't worry if this sentence does not make sense yet)
  - Strictly speaking, those commit messages are not very well chosen; but we're all guilty of that.
- On github, aren't they all "main" now (unless the name is overridden to "master")?
    - Correct, github and other platforms are switching to "main" as default branch name. (we need to update our materials for that, in progress). More info at https://github.com/github/renaming
        - :+1: 
    - But not default for local repos, and stuff not force-changed yet.  There will be a long, confusing transition period...
- 
- Can you later show how to find out how to work with different repos in parallel? If I work on different projects, I am unsure how to change the repo. I think it has something to do with the origin, but I am not sure.
    - Yes, this will be covered (TL;DR: each repo has its own folder)
    - We will introduce it tomorrow and really clarify this on Thursday.
- What is the difference between branches and forks?
  - branches are development lines within the same repository
  - forks are copies of entire repositories, each carrying their own branches (we will really introduce forks on Thursday)
  - you can use branches to organize independent lines of development within one project

- What is typically the ratio between people being true contributors and people using fork?
    - Depends on the project, of course most online projects have more users than contributors 
- Is there a s there a what is this writing in mid air devil magick?
    - It's something he made, light board thing.  maybe we can demo more at the end. - :+1:
    - Please do!
    - wizardry at its finest!
- How can I share the link to a specific change/commit in a file?
    - A assume this is about Github, or some web serice
    - yes
    - We'll see more examples later.  In general, navigate to the right page you want to share, and you can also get links to certain line numbers.
    - Okay, thank you.
- How does one use git/version control in a project which has text but also stuff in maybe strange binary formats (think data, figures, etc?) 
    - There is Git LFS for large files. Effectively the binary file is taken outside source control, and your repository only contains a hash of the larger file.
    - If files are small and binary, I would usually commit directly.
    - What counts as "small" here?
        - < 50 MB per file, Github will complain if you add larger files
    - For me, small enough I don't care if repository size permanently increases by that much.  anywhere from 1-10MB.  If file won't be modified, maybe larger.  Only disadvantage is that history is permanent.
- How do you define the moment when your software has reached a new version number (v1.1, v1.2, v2.0...)?
    - great question, also curious.
    - In some sense it's up to you, but here is a common scheme: https://semver.org/
        - This is what people will be expecting when they use your software.
- Is it possible to migrate an SVN repository into github and keep the history? 
  - Yes using git-svn you can convert svn history to git, preserving all changes. I have used this tool also to use Git locally with colleagues or projects that insisted on svn.
  - you can convent most other VCS history to git (I've done it several times)

### git-intro: Basics
https://coderefinery.github.io/git-intro/02-basics/
In this section, we make our own repository and start making commits.

*We are watching this hackMD, but we will reply every now and then so that you can focus on the speaker.*

- Is 'git push' an extra step (for github for example)?
    - yes; committing creates a snapshot, pushing sends it to a remote
    - today we will not use `git push`, in other words everything we do today with Git stays on our computers. `git push` is used to share changes with repositories "in the cloud" or on other computers
- Why do I have to do twice git add? I edit the file and then I have to do again git add? Would not git know already that it has to watch file A?
  - if the file is already tracked (has been added to the repository), git is watching it and I can always check what changed since last addition/commit. In this case we have used `git add` to *stage* (prepare) for a subsequent commit. We recommend to do this in two steps so that you can inspect changes before committing them.

- What should we use if we are using windows in case of terminal?
  - git bash is probably the best for this (+1)
    - https://coderefinery.github.io/installation/git/#specific-windows-installation-instructions
  - but the exercises probably can be also done in an Anaconda Prompt
-   in order to organize things, are we going to crate many repositories in our computers during the course? Should we organize directories in a specific way?
    - It's up to you, one directory for CodeRefinery with everything under works well.
    - Whenever it's an exercise on GitHub, we will be very explicit about what to do. On the computer I recommend to create a folder for the workshop and different sessions can be subfolders. I created a folder "course" and under that created one called "git-intro"
- is there a way to see all initialised git repos? (if you have initialised several of them)
  - to find all git repositories on the computer? is this on Linux?
  - mac os. let say i have initialised a repo for my project and now I am initialising another repo for the course. is there a way to find out that there're two repos on my system and where they're located (which folders were initialised as repos)? thanks!
    - I would do it like this: `find $HOME -type d -name ".git"` (locate all folders that are named ".git")
    - great, thank you!

- macOS finder cannot see this repository in some way right?
    - You should be able to navigate to it and find it
-  In case of having more than one git username (e.g. one gitlab and the othe github), how can we switch to one an other username easily for working? In other words, now my git config is my gitlab account, how can i change it easily to be able to come back to my gitlab? -:+1:
    -  (we'll see later) 
- What is the link to the google doc with Sabry's code history?
    - Top of this page for reference
    - https://docs.google.com/document/d/1VQ4lUr1hrrKQwOAYa2z0h-0xltBm1PEuQLY8VksWk7c
- What is the name to use for sublime editor? "subl -n -v"?
    - I think `subl -n -w`.  Search "sublime git editor"

- When I use git add, I get the following message: "warning: LF will be replaced by CRLF in ingredients.txt.
  The file will have its original line endings in your working directory"
    - Nothing to worry about. Line-endings are encoded differently in Windows and Linux/Mac: this says, git will automatically convert them for you.
    - There is a configuration option to get rid of this warning. Looking for it ... found this: `git config --global core.autocrlf true` hopefully this fixes it.
- what is a working tree?
    - The current directory you are working in.  This is git terminology.
- what is an insertion?
    - Line that has been added.  Each change has X lines added, Y lines removed.
- If Sabry would now modify ingredients.txt again and not do a git add ingredients.txt, what would happen? Would git not know there were changes done?
    - Correct, git only tracks when you tell it to.  So yes, there would be no new commits or anything.
        - But he could still do a commit, but git would only know the first version still?
- What is a good annotation like? How do I learn not to just write "improved some stuff"?
    - We'll talk about this later.
- If you don't pass a message to your commit it takes you to a file, what do you do there? Write a message somewhere?
  - it opens up the editor which you have configured. then you can type the commit message there. if it opens up an unfamiliar editor, you should configure your editor, see https://coderefinery.github.io/installation/git/#configuring-git
  - It does open the file, and there's some instructional text there (commented out). Do you just leave that there and type your commit message plainly in the file?
    - yes, once you are done, you save and close the editor and this will then record the commit with that message. you can leave all the commented instructions and the commit message is written above that. the commented instructions will not end up as part of the commit log, they are only there for you.
    - And the saved file will also not end up in my folder?
      - right
          - thanks!
  - how do I exit the editor?
    - is this an editor you did not choose? is it vi? (probably). if this is the vi(m) editor, please type [escape key] followed by typing ":wq"
    - please reconfigure git to your favourite editor
- Sabry had some "alias.graph"  in the git config. It looked smart but I did not manage to record it. What was it?
    - In the "quick reference" at top of lesson page you can find it.  We'll go over it in class soon!

- will git store multiple copies of all file as they are updated inside the .git folder?
    - It stores complete history, but is very good with the compression.

- what was the analogy with the tape? 
    - The word "HEAD" used in git as the "HEAD" component in tape recorders. *"As we start recording audio, the tape moves past the head and it records on to it. When we press stop, the place where the record head is, is where it will start recording when we press start again."* (https://medium.com/@sinetheta/understanding-head-in-git-cde38617404c)
- 
- Is it possible to reverse from the hash to the author and date?
  - meaning that if you know the hash to find out what the date and who the author was? if this was the question that i am unsure whether this can be done this way but it works the other way: author and date meta information is used to compute the checksum. so if you see two commits with the same checksum, the probability is overwhelming that both have the same author, same date, and same history.

- What is sha1sum?
  - it's a program to compute a "checksum" of a file. the instructor used this to demonstrate who git hashes look this way. a checksum is a way to detect whether something changed. it can be useful to compare two files whether they are exactly alike or not.

- once added, Is it possible to remove a file from git completely, like when we add rubish by mistake or a large data file that is not usefull anymore.
    - That requires rewriting history, it's possible

- git difftool is not working here.
    - We can check later. After 12:00/13:00 we can stay around and debug this using screensharing.


### Exercise: record changes
https://coderefinery.github.io/git-intro/02-basics/#exercise-record-changes
You should be able to do most of the basic things, you can try to demonstrate optional ones, too.
15 minutes, ends at xx:55.

Breakout room status:
- Room 1: we good. some did the optional excercises
- Room 2: We did alright - all made it through the main exercise.
- Room 5: Almost done with exercise, got stuck on specific issue. Perhaps took too much time on introductions.
- Room 12: all good! We did the whole exercise. We checked also the first optional exercise.
- Room 3: We did the main exercise, all good here
- Room 16: We did the main exercise, + first optional
- Room 17: All good
- Room 18: we covered the main exercise, all good
- Room 13: Good. An optional exercise covered.


### Break

:::danger
10 minute break until xx:07.  Don't forget to get up and walk around!
:::

- My commit hashes are very long, like 902e7b00c3d49d92df63bb2872ab079137aa26d0. Is this normal?
  - yes, they are 40 character long. you can refer to them by their first characters. so sometimes you see only 7 of them (e.g. on github) but this means these are the first 7 characters.
  - so the one line hash is just the first 7 characters of the full hash?
  - yes, git abbreviates to something short enough but still unique.

- I installed meld succesfully but and executed `git difftool --tool=meld`. When I try to compare commits by `git diff <hash1> <hash2>`, meld does not open. I'm working on Ubuntu Linux.
    - I guess we need to configure it, we can check after the workshop.  Installation instructions say what to do to configure the difftool.
    - is `git difftool <hash1> <hash2>` opening meld? I guess the diff subcommand is not changed to open the difftool by default.
        - Using `git difftool <hash1> <hash2>` works for me! Thanks
        - For me this works (Windows 10 machine).
    - I have the exact same problem but trying to use difftool on mac. I can difftool two different filenames, but "git diff" does not use the specified difftool in the global settings. (using explicitly "git difftool hash1 hash2" works fine)
    - In my case, it only opens when something has been changed in the file
- When I do git status, it shows my full home directory as files not added. I was earlier trying git, and I may have added my complete home directory for tracking. I am trying to fix this, but could you help perhaps after the workshop ? 
    - Yeah, we can look after workshop.  If you do a new `git init` in a subdirectory, it should detect that instead
    - I would then delete the `.git` directory from your home, then it goes away
    - Ah thanks ! let me try this !
    - Thanks it worked ! :)

- One attendee integrated Atom as git editor but is not saving the message, not sure what to do there, any ideas? BR8
    - `git config --global core.editor "atom --wait"` according to https://stackoverflow.com/a/31389989
    - if this did not solve it, we can have a look after the lesson today
    - it did solve it, thanks

- Do you know a similar software to Opendiff for Mac? For Opendiff XCode is required and it seems to be a big efford to install the comeplete 12 GB software suite for a small comparison program.
    - https://www.sublimetext.com/ u can try this
    - It looks like there may be a macOS port (of meld) at https://github.com/yousseb/meld/releases/

- I have meld installed, but running git difftool --tool=meld gives me nothing.
    - We can check configuration after the workshop.

- Did you enable the timer function for the breakout rooms? 
    - Is this a built in Zoom feature?
    - Yes, this can be selected in the settings I believe, or when you create the breakout rooms.
    - Nice, we'll take a look!
    - I think you can just set the Countdown timer to the total duration of the breakout session.

- If I delete '.git' directory from my folder, it keeps my local directory or last committed version?
    - All git history and all other branches than your last one you were on go away, but local directory stays exactly as-is.
    - Okay.


### Continuing
https://coderefinery.github.io/git-intro/02-basics/#writing-useful-commit-messages

- How to stage a deletion?
    - `git rm` tells git to stop tracking a file (and also deletes it from directory) 
    - if you accidentally removed with `rm` and not `git rm`, then you can stage the deletion with `git add` (yeah it's a bit weird then)
- where should I put the .gitgnore file? anywhere? Is it a folder by folder thing?
  - typically it's in the topmost folder of the git repository. it takes effect on all subfolders. this means that you can have them in subfolders of the git repository and you could have several in the same repository but most often there is only one.
- what happens if I gitignore a file that is already under version control?
  - it will continue being tracked until you `git rm` it
  - if you do the opposite: if you try to `git add` a file which is in `.gitignore`, Git will complain and tell you about it

- Can I put a whole subfolder in .gitignore? Can I basically ignore folders?
  - yes, sometimes you want to ignore entire folders (example: build folder, generated folder). the way to do this is the same as files. you can use regular expressions (wildcards)

- how do I stop tracking something if I realize it's something that shouldn't be tracked, but need to keep the file?
  - `git rm file/path`: this will stop it from tracking but not remove it from the history
  - I'm confused, above it says that git rm will also remove the file from the directory?
    - yes it will remove it from the directory, but not from the git history. so if you later realize that the deletion was a mistake, you can bring back the file from a past version of the repository
- Sorry, I missed what is git mv filename.txt do?
  - you can use this to rename tracked files or to move them between folders
      - And what is the difference in comparison to the normal mv command? git mv is a combination and git will know what is going in?
      - Exactly, `git mv` does the normal move, then tells git about it.  Otherwise you have to tell git about it separately.

### Staging area
https://coderefinery.github.io/git-intro/04-staging-area/

- what is a "hunk"?
  - a "change" or portion of a modification. (personally I think the name is not great since I did not know either)
- So I use git add only when I want to add files, right? once i added a file for next commits in the same file i just use git commit?
  - you use it to add files to be tracked but later you can use it to stage changes so it has two meanings
  - after it has been added once, you could only use `git commit somefile` but I personally always use `git add somefile` to first stage the file because it allows me to inspect the whole change with `git status` first which helps me to create well defined commits.
- I am bit confused with staging concept
  - it's like a preparation area for a commit
  - it is ok to not use it when starting with git and use it later. it can be useful to prepare a commit consisting of several files.

- From the previous exercise, when I executed `git status` I read: `HEAD detached from <hash>`. How can or should I get rid of this?
    - `git checkout master` or some branch name.
    - what that really means is that HEAD is not pointing to a branch but to a commit directly, more about this when we talk about branches
- In case we use pycharm or VS, is this git add happening automatically? since we can always see the diff from repository version without adding.
    - Some editors will automatically add.  Not sure about those, but if it's what you see then I guess so.
    - But also in the terminal I can see changes with `git diff` so I am not sure they are auto-staged.
    - VS Code does not automatically stage the changes, but it will notify you when files have been changed in your working directory

- what is the order: you make the changes to your file and then git add or first git add and then make the changes ?
    - Change first
    - and what would happen if I add the file, but then before commit I make more changes to the file. so it would give me error ?
    - `git add` snapshots it then.  You'll just have some extra, non-staged changes waiting to be added later.  `commit` only does the staged changes.
    - clear. thanks !

- So what does commit -p do? Didn't seem to have done anything for me.
   - how did git status look before the command? i think it showed perhaps nothing was staged?
       - It said something was staged, then after the commit it said nothing is staged. It's exactly like I just ran commit (without -p).
         - did the change contain several modifications or only one modification in one portion of the recipe? i am asking this because -p is useful if you want to commit only part of several unrelated changes.
            - yeah it was exactly like in the example (I added "\* top" and "\* bottom" at the top and bottom). I can also see this with git diff --staged.
              - aha, now I see. it seems both changes were already staged so the `-p` part of `git commit` had no effect. it would have had an effect if the changes were unstaged (I had to try this locally, I was unsure about this myself)
                    - wait so I commit before staging?
                      - no, either stage+commit or only commit directly (in this case git add -p followed by git commit, or only git commit -p)
                      - ah ok, got it. Works that way. So -p is to skip staging?
                        - no, the `-p` means "by patches" if you do `git commit` without staging, it bypasses staging.
                        - ah k
                
- How to get back ignored file?
   - Edit the .gitignore file
   - use git add with the specific filename you ignored

- If you made a mistake X commits ago, how do you remove/undo this change or modify it? While keeping history..
  - this will be discused now. safest way, keeping history is `git revert`: this creates a new commit, applying the opposite of the "reverted" commit

- checkout allows to restore the staged version (or the last commited version) and delete all the changes in between the staging (commit) and the checkout, right?
    - yes, checkout removes all unstaged/uncommitted changes: `git checkout myfile`
    - (we'll see later than `git checkout` can do other things too)
    - ok, thanks!

- How do you split a large commit with many features (A,B,C) into smaller commits with features A,B,C in the right way? (maybe beause we wanted to later revert feature B). Is it an issue if we pushed this feature to origin?
  - there are many ways but this is what I would do if this was the last commit and I wanted to split it up: I would `git reset --soft somehash` to the hash right before `somehash`: the effect will be that the last commit (all commits after `somehash`) will be gone but all changes since will be staged. Then I can unstage the things I want to commit later and commit the changes selectively.


### Undoing
https://coderefinery.github.io/git-intro/05-undoing/

- if i make a commit but i realize it's wrong, and i still didn't push in repository how can i delete my commit? 
    - We'll go over it in this lesson!

- Can you also revert a commit other than the latest?
    - Yes, it makes a new commit with the opposite changes.  But some other options only apply to last commit
- how to go out of revert window? ctrl x dont work
    - Is it an editor for commit message? its git bash, yes editor
    - I found it, it is :q 
    - and if this is an unfamiliar editor, please configure your git to use your favourite editor (see install instructions for git)
- can you undo a git reset --hard?
    - Uncommitted changes are permanently gone.  You can recover commits or added stuff, but it's not as straightforward.  

- about git-stash
    - See this optional lesson: https://coderefinery.github.io/git-intro/11-interrupted/
    - Maybe we'll have time to do it tomorrow.

- Is my conclusion correct that git revert makes a new commit but git reset (soft) or git checkout doesn't make a new commit but just change the head point to the one you want?
  - yes, this is correct. `git revert` does not modify the past, it creates a new commit. `git reset` "moves" the "recorder" HEAD and can modify/replace past commits. `git checkout` does not modify the past but moves the "recorder" HEAD to some other place, after which you can move back.

- does anyone actually remember all these commands? or is it normal to have to look them up?
    - git status, git add , git commit -m , git merge are the important ones. Also git status displays a lot of commands you could use next. The rest I google. I maintain software professionally. 
        - Thanks!
- 
- So if you stash you can open those changes at home later? I mean, does the stash get pushed? 
    - Stash is local to each repository, they are not pushed.
        - So the "friday afternoon" example is only if you'll continue working again on Monday? 

- Follow-up on stash, is it fixed to a branch?
    - It's not fixed to the branch.

- If you revert some arbitrary commit in history, how can all the other commits after that react to it? They might have written in a file that was originally added in the reverted phase. 
    - The intermediate commits aren't modified, it makes a new one.  So you can still see the un-adjusted history in between.

- I have some issues with opendiff. On my Mac, opendiff textfile1 textfile2 works, but how do I get it to work with git as well?

- How did Sarby do the thing with the white marker?

### Please give us feedback about today

One thing that you particularly enjoyed, one thing we should improve/change. Thank you!
Th
- Bit more time in the breakout rooms would be nice
- the HackMD doc is not hugely intuitive as a tool for tracking conversations/threads. However, I also don't have a better solution. I liked the light board visualizations, made the processes easier to understand. could even be used more.
    - For this maybe Slack?.
    - I like hackMD because it's anonymous, I wouldn't ask some questions otherwise :) +2
- I thought it was good mostly, but it's difficult to incorporate the new information and remember what things are used for without using these things daily (which is the hump i can't seem to get over) +4
- Good work, I appreciate that you took time and walked through the basics. Also really liked the white
-  Good work! I liked how Sabry managed the lesson! it was very intuitive and easy to follow. Good pace too (I am a beginner)
-  
-  - Good timemanagement! Questions also in person via voice are nice. Not all via hackmd, because you might miss these... 
-  
- Good work, but more practice would be useful for consolidating the concepts.

- Thank you for the lesson. It was easy to follow for the most part. Small suggestion could be: some small exercises (which are not mandatory) just if someone wants to try. and be hands on for the same day's lesson or next day's lesson as well.  

- Demos are useful, but perhaps you can give us a bit more time to actually code along with the instructor. I think that coding along is a good way of remembering the material. The word doc that records all terminal commands is helpful for keeping track. +3
    - Yes, I find myself zoning out pretty easily if I'm just trying to listen and watch, some more "now try for yourself" would have been great

- I liked Sabry's presentation style, the explanations. I liked the split screen, seeing terminal and website. He was a bit fast in the end. +2
- Sometimes I did not find the lesson material fast enough and got confused.
- Sometimes it was hard to quickly see things in Sarby's terminal, as there are no colours.

- I would like a bit more explanation about the steps that ar going to be taken, before jumping into the commands in the terminal. It's hard to follow when the explanation and the terminal is used at the same time. 

- I am impressed how quickly HackMD questions are answered. Sometimes so fast, I decided to listen to more to Sarby then checkout what is going on on HackMD. Great work!
- Thanks for today. It will be nice if more examples are given where you should use specific commands
- The incorporation of questions with HackMD and the lecture itself was very smooth and my questions got answered clearly and quickly

- I think staging could definitely be postponed until later on. 

- I think in general it was nice and very good regarding information density. Though I felt the last part (starting from revert) was a bit quick and harder to follow. This can be improved I think.


- The introduction lecture on motivation was a bit long and tried to cover many things. Perhaps cut this down or split into smaller sessions?
    - Agreed, since everyone attending this lecture likely already has some idea why reproducible research, version management etc. is good. Preaching to the choir, you might say.

- I don't know if this is already scheduled, but it would be nice to have a few words on how to manage projects with large input/output files. Is is worth adding them to git? In case of binary in/output files, is git a good options?
  - hopefully we get the chance to comment on that. otherwise I would use git-annex or git LFS or https://dvc.org/ where the git repository tracks metadata but the data itself is stored somewhere else.
      - 🙏

- I'd suggest to be even more clear about when you're switching files/windows and verbalize which one you're in. I'm flipping back and forth between the video, the material, the live Q&A doc, and my own terminal so sometimes when I come back to the video I have no idea where the thing I'm looking at is located.

- Feedback via HackMD was not optimal. When all where typing at the same time in basically the same place I could not even see my own cursor... Also would be good to adjust the width of the shared screen so that its possible to have zoom beside your own terminal locally. Like Radovan did.


---
*Always ask questions at the very bottom of this document, right above this.*

*We are watching this hackMD, but we will reply every now and then so that you can focus on the speaker.*
