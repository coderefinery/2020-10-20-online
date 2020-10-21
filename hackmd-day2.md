---
permalink: /hackmd-day2/
---

# October CodeRefinery HackMD, day 2

:::danger
Please open HackMD, rename yourself to "(n) Name" (Participant list→hover over your name), and answer the icebreaker below. 
:::

## Links

- **Welcome!** Please open this HackMD and the course material!: --
- Course page: https://coderefinery.github.io/2020-10-20-online/
- Schedule: https://coderefinery.github.io/2020-10-20-online/#schedule
- HackMD from previous days: https://coderefinery.github.io/2020-10-20-online/#questions-answers-and-feedback
- Instructors terminal history: -


## Icebreaker

Name the most important thing you learned yesterday
- git can also just be used on a local folder. I always thought it had to be cloud-based (github, gitlab, etc).
- `git commit -p` to split changes into multiple commits +1
- That it is possible to link to a specific section of code and share the link (though right now I've forgotten how)
- git status
- Meaning of commits' hashes +3
- Staging. That I have to add something to the stage before git will do anything with it. 
- Staging. That you can do commits on specific files instaed of all the changed files.
- The `--oneline` flag to `git log`. +1
- Meaningful commit messages. Only git when something significant has changed
- The pointers about how multiple changes can be grouped logically into one commit. Was never sure how many changes one needed to make for a commit.
- What Git and version control means through some basic examples. Also, the difference between Git and Github/other applications.
- Git has many global config options that I did not know, including the option to link editors and visual diff tools.
- got introduced to git checkout, restore, revert and reset +2
- `.gitignore` functionality 
- purposeful use of commits

## Introductory questions
- How to handle sensitive personal data (e.g. human genotype data or clinical information) in git? Would Git-annex be a possibility?
    - First level question is more about what hosting service you use: if you use it only locally, no data is shared
    - Permanent history might be an issue sometimes, git-annex can help with that a little bit
    - If files are large, then that's another matter and git-annex or git-lfs are good options
    - You can have the metadata synced with other repositories (even public), but the actual data should stay local (no github/cloud/etc). If you are working on such projects, I can show what we are doing with the Finnish national neuroimaging biobank ([name=staff])
        - This would be very interesting. For now clinical files are totally outside version control on my end which is obviously not good.
            - You could version control the metadata about the file (date, filename, md5 checksum, file location).
        - git-annex is one way to handle this metadata.
- I use README.md for documentation of my GitRepos. However, I see that github uses HTML for rendering the file (better scaling of Images and text) whereas Bitbucket uses Markdown (not so fancy). What is the best way to make such README.md files so that they seamless work across all online git platforms.
    - markdown files get rendered nicely on GitHub also! Shouldn't be any difference between github and bitbucket, but please correct me if i'm wrong
    - Thanks! So short answer, just focus on Markdown. :) 
    - Sometimes I use README.rst. Advantage: I can get a table of contents automatically.
- If we go back in a commit and make changes there, how does this change move forward in other commits which were done previously.
    - I guess this will be part of the branching session today [name=fellow participant]
    - if you go back in time with `git checkout` and make a commit there, this commit will be *orphaned*, i.e. not belong to any branch and it will be difficult to find later. If you need to do this (e.g. for testing) you should create a branch from the commit in the past
    - Thanks! :)
- If I write code consisting of functions of dozens of lines (or more), would I commit intermediate/not-working steps of the development process, or only commit once the entire function is working and integrated with the rest of a repo?
    - I personally first write all the comments describing all the sub-parts of the function/script/code. Commit that. Then work on each sub-part and commit when the sub-part is ready.
        - that makes so much sense.
   - this is also where branches come in handy, new features (e.g. new functions) should be developed on a branch. You can have fine-grained commits with incomplete implementation on the feature branch, but the branch should be merged only when you're done

## git-intro
https://coderefinery.github.io/git-intro/

### Branching and merging
https://coderefinery.github.io/git-intro/06-branches/

- I don't understand what happens for c4 -> m1, when m1 is connected to d1?
  - `m1` is a merge commit which merged (combined) two lines of develoment. it has two "parents": d1 and c4.
- Checkout `<hash>` can also be restore `<hash>`, no?
  - Yes I think so. I think `restore` is more modern. Traditionally there was only checkout (if I remember correctly).
  - Yes correct.
      - I'm a bit confused since checkout `<hash>` and checkout `<branch>` seem to have very different functionality. Or am I not seeing the parallel?
    - You are right, this is a good question for [Name=Instructor1] to answer (and he did). Git switch and git restore are much nicer (need new git version)
        - Ok so I can completely avoid checkout? Or do I need it for something else?
- 
- Could he explain what it means git checkout ingredients.txt ? I missed this. +2
    - It brings back the committed version of the file. See the "interlude" at https://coderefinery.github.io/git-intro/06-branches/#interlude-different-meanings-of-checkout

- what will happen if there are unstaged changes based on the latest commit while I would like to go back and 'checkout' historical commits? Will those unstaged change lost? Must I stash the change first?
  - yes, unstaged changes will get lost. This means that before navigating to some past version it's always good to commit first and only do that after `git status` shows a clean state.

- What is the difference between `git switch <branchname>` and `git checkout <branchname>`?
  - both do the same thing. `git switch` has been introduced relatively recently and is not available in old git clients. if `git switch` exists on your client, I recommend to use it, since it is more clear what it does.

- about the different meanings of checkout, it says "This is unfortunate from the user’s point of view but the way Git is implemented it makes sense." Can you elaborate on this? (why it makes sense)
    - in all use cases of `git checkout`, stuff is fetched from git history (`.git` folder) and placed in the working directory (another branch, last committed version, version corresponding to particular hash)

- You have introduced `switch` and `restore` as more modern and more specific versions of checkout, for branches and files/paths, respectively. What about hashes, though? Can one use `restore` then too?
    - In general hashes work in place of branch names or tags when it makes sense.

- When I edit a file I cannot get the correct differences with diff command. E.g. I added cilantro in ingredients and I get  * 2 avocados* 1 lime * 2 tsp salt -* 1/2 onion which is strange because I never removed onion! :)

- will the `git graph` alias be saved for all time or do I have to retype it in every terminal / git repsository/ ..
    - If you set it with `git config --global` (emphasis on `--global`) it's there for everything on that computer.

- I have a problem installing snakemake, which we will be using next week. The error message indicates conflicts  because of incompatible packages. I have tried with both pip3 and conda, does anyone have an idea what the problem could be? Thanks

### Exercise:
https://coderefinery.github.io/git-intro/06-branches/
17 minutes, until xx:05  (+ 5 minutes)
1. Create experiment branch add the two coommits as the instructor.
2. Try to accomplish "Exercise: create and commit to branches"
3. IF something goes worng (and only if something goes wrong), Get and pre-p reared repo as described in the begening of Merging branches secion. 

Breakout room status:
- room 1: we have confusion about the branches, could use some extra help. conclusion: there are some inconsistensies in the exercise instructions. 
    - What we noticed: If you commit and stay in "less-salt" branch you won't get the same git graph as in the first picture of the exercise. I guess because we did "git checkout less-salt". Adding "git checkout experiment" to go back to the experiment branch, makes it look like the exercise page. 
        -  but at first we also forgot to do "git checkout less-salt" because it's not explicitly in the instruction (yeah we should know to do that, but it's so easy to forget)
- room 3: Done.
- room 2: We're done.
- room 7: Ok
- room 8: We're done, just trying to fix the issue below
    - Anaconda prompt issues with git branch. Seems like branch is not showing master or any branches at all. Similar with other commands. Is it due to the anaconda prompt? any ideas?
    - https://github.com/coderefinery/installation/issues/113

- room 11: pleased with the extra time :)
- room 17: All good, there was some confusion on `git branch "branchname"` not automatically checking out the respective branch
- Room 14: Good. Done with the exercise.
- Room 18: All good
- room 9/10: seem to be going well
- Room 5: all good 

### Break
:::success
10 minute break, until xx:16
:::


- Is it like git branch?: git merge merging-branch master-branch ? 
  - `git merge the-other-branch`: git merge modifies the *current* branch by incorporating `the-other-branch`
  - `git branch some-name` creates a new branch from current branch with the name `some-name`
      - The question was if I can provide the target branch, but it seems it is automatically set to the current branch. Git branch provides at least the option to specify from where I could create the branch. 
- Doesn't the "HEAD-> branch" in git graph already show which branch you are on?
  - yes, this is the same as the "*"

- will it merge to the HEAD branch?
   - HEAD is not a branch, rather it is the tip of the current branch
        - so how do I specify what should be merged? where is the specified branch goin to merge?
          - see two questions up: you always merge into current branch and the name you give is the other branch that you want to incorporate.

- In git graph can you explain the color scheme for the edges in the graph?
    - The colors of edges have no meaning, they are just to tell them apart.

- You really have to explicitly switch to every newly created branch,  right? so after *git branch foo*, you always have to *git switch foo*. Stumbled over this twice now.
  - yes, `git branch` does not change branch. But you can do these in one step:
    - either: `git checkout -b somename`
    - or: `git switch [-c|--create] somename` (meaning using either `-c` or `--create`)

- I don't understand what happened with the fast forward or why it's useful... more context please.
- I got completely lost in the fast forwarding. It went way to quick for me +1
  - `git merge` normally produces new (merge) commits. but if the two commits to be merged are linearly related (one is an "ancestor" of another), it can move it "forward" without creating a new merge commit.

- @staff, *git diff* also does not do anything on anaconda prompt (like *git branch*). Possibly related to issue #113 (https://github.com/coderefinery/installation/issues/113).
    - Yes, this is most likely it
        - Oh weird it just worked now.

- git diff shows a and b. That refers to the input variables, right? I have to keep track of what is a and b?
    - Refers to the two input files.  I never look at these and always remember what I am diffing.
    - The reason why that annotation is there on top is to make the output compatible with the unix `patch` command (in the old days before github, patches produced by `git diff` were sent sometimes by email and applied with `patch`)
- What is a fast forward? Switching the head to another point?
    - See two questions above


### Conflicts
https://coderefinery.github.io/git-intro/08-conflicts/

- does the git graph show which branch was prioritized after the conflict?
  - I don't think it does, it shows the two parent commits but to really see what was "decided" in the merge, I would inspect the merge commit with `git show`


### Exercises session (type along)
LINK https://coderefinery.github.io/git-intro/08-conflicts/#type-along-create-a-conflict
10 minutes, until xx:00.
Create a conflict and try to resolve it. Try to repeat the same thing the instructor did 

Breakout room status:
- Room 1: ok
- Room 2: We're almost done. xx:00 seems good.
- Room 3: done.
- Room 7: Done (had some connection issues)
    - We added few more minutes (until xx:00)
- Room 8: All done
- room 9/10: we're fine
- Room 17: Going well
- Room 7: Need more time
- Room 14: Going well
- Room 5: all good
- Room 18: all good
- Room 4: All done and good


## Break
:::warning
On a break until xx:12.
:::

- I created a conflict that I tried to resolve with mergetool (which works). I added a (different) new line in each file (at the same position). How can I resolve this conflict by keeping both new lines, just one under the other? Instead of keeping one and discarding the other.
    - This requires human thought (there's no way to know what you want).  Your mergetool hopefully lets you make the edit you want, and then you can set it to what you want.  Or, open in an editor.
        - yeah so mergetool (meld) only provides little arrows the let you choose a line (or delete it by holding shift). I don't see any option for "keep this but put it on a new line".

- Does it make any difference if one merges the less-c

lantro branch first and then merges the more-cilantro branch and vice versa? Or the order of merging doesn't matter (in case of a conflic between these two branches)? thanks!
    - The conflict will look a bit different, but it does roughly what you think.
    - ok, thank you!
 
- Is the conflict not mainly arising because the two cilantro branches started from the same point in master?
  If not and I merge dislike-cilantro and then I merge like-cilantro into the master, it would just overwrite the amount of cilantro without a conflict?
  - Git can figure out that there is a conflict anyway, since it can follow the differences on both sides.  Wouldn't conflict if one of the branches was made after the other change.
      - I don't understand what you mean with "Wouldn't conflict if one of the branches was made after the other change." Might ask after the course.
  - If you make a branch, merge it, then make a new branch, new one can't conflict with old one
      - Thank you.


- does git log always show the entire history?
    - By default yes (in pager, which only loads recent history so it doesn't have to generate everything)
        - oh ok I had to deactivate pager because of anaconda issues, so it is looking kinda long now.
        - Yeah, in that case it'll get long.  We'll need a better solution.
        - `-10` should limit to 10 commits, etc.
- After using difftool (meld) to solve the conflict and merged, I saw one extra file named 'ingredients.txt.orig' in the folder. The content is the conflict file created by Git. (the file with <<<<< and >>>>>). Is it safe to remove this file or it is supposed to be removed automatically after merging?
    - It can probably be removed, yes.  My guess is meld made it, sometimes you see these as things try to be safe: If I know conflicts are successfully resolved, I remove them.

### Sharing repositories online
https://coderefinery.github.io/git-intro/09-remotes/

- some github authentification is required first for me: Please make sure you have the correct access rights and the repository exists. +1
    - Hm, we should follow up on this after today is done.  It will be important for tommorrow, but not urgent now.
            - OK I will stick around after the lesson ([name=xxx]).
    - Things I would check: is it https or ssh?  If ssh, have you set up keys, is it configured in github?  Is repository URL correct?
    - It seems the push commands don't change when you click HTTPS, so it still is the SSH

- I got stuck doing this so I'm missing basically all the history stuff going on now.
    - I would pay attention and you can try to review later, or get help in breakout room
        - I gave up and am now following the lecture. Just some feedback on the fact that I missed the start of the lecture since I got stuck on the sharing and there wasn't really a closure of that subject.

### History inspection

- networkx was moved from SVN to Github at some point?
    - Probably so, at least you do find some projects like that occassionally

- Was git annotate previously git blame?
    - I think they have always existed together.  They have slightly different formats, not sure why there are two commands.
    - I use them interchangeably. I thought they do the same thing.

- How did [name=staff] search online on github with git grep Fixme, please?

### Exercise
LINK: https://coderefinery.github.io/git-intro/10-archaeology/#exercise-basic-archaeology-commands
20 minutes, until xx:00

Breakout room status:
- Can someone help room 4? :)   Juho will help
- Room 8 done, exploring some extras now
- Room 18: need clarification on the last step of the exercise : "How would can you bring..." Enrico there, all good. Covered the main exercise.
- Upon git cloning many of us in the breakout room got some "detached HEAD" message. Is this as expected? And what does this mean?
    - Also wondering that. Is it because the branch was merged and deleted? 



- Is the ~1 a magic command to switch back one hash?
    - hash~1 means go back one commit from the hash


## Please give us feedback about today

*One thing that you particularly enjoyed, one thing we should improve/change. Thank you!*


- **Suggestion** Maybe it will be a good idea to name the webpages and the links with the same name. It will be easy to follow the webpages on the fly. :) 
  - can you give an example? (I am sure it's a good suggestion, just want to know what precisely you mean)
- **suggestion** Also, if things could be numbered on the webpages, it would be easier to refer to sections and places. "go to 2.3.1" instead of "scroll up a bit".
  - ah yes, good point, thanks!
- **suggestion** for the users is to write the questions in another window (notepad or something) and copy/paste into hackmd the full question.It will help dealing with the lag some experience.
- How bad is the lag?  Can you "+1" if lag is bad for you?
    - I notice that refreshing the page sometimes helps a lot
    - have had lag when editing but less when in view-mode for some reason

- I like the "google-docs" like document that [Name=Instructor1] used to track his commands inserted in the terminal. It is nice as a back-up, even if you don't actively look at it. 
- I liked todays session! It was good paced.
- I really liked the branching/merging exercise. I do not fully understand why we are briefly touching on (what feels to me like) advanced things like bisecting or forward merge without the time to really understand/practice them. It does not help my understanding. +3
- I would prefer to go a little slower, so we can type along. We can then use break-out sessions for more advanced exercises +7
- I prefer the second way of displaying the contents
- Great session but I was a bit lost in the first half of the session. A bit too fast.
- I don't look currently at the google docs because besides Zoom, hackmd there are otherwise too many windows. I am fine with hackMD, no delays. It would have been nice if [Name=Instructor1] could have made his terminal larger in vertical direction to see more.
- [Name=Instructor1] was too fast with the fast forwarding for me, I think this was a pity. +2
- I have only one small screen, I could cope with [Name=Instructor2] and [Name=Instructor1]'s version, but then I am looking mostly at Zoom, less on hackmd. But my terminal still fits next to Zoom. I did not look at google docs, but would just have wishes to see more of [Name=Instructor1]'s terminal.
- I'm on three screens so happiest with side by side. But I can adapt. +1
- about screens - the later layout is easier to adapt to many different monitor setups. If you have several large monitors (I have) you can still make the window quite large, but if you're on just a laptop it's a lot more usable.
- some parts were quite fast today
- I think highlighting of the shell input would be useful. i.e. the input should be a different colour to easily differentiate it from the shell output because I find myself looking for where the last output started. +3
- I really enjoyed [Name=Instructor2]'s screen arrangements (and I have multiple large displays, display space is not the issue), and style in general, and how it was indicated very clearly what's going on and where we are in the material. With [Name=Instructor1] it was more difficult for me to follow and not quite clear what we were supposed to do in the exercise (instructors cleared that out though).
- I really liked [Name=Instructor2] explaining what he was going to do and what we should/should not worry to much about. e.g. showing the cloning, but mentioning that now it is not critical to completely follow it. Also it is good that he very clearly outlines the excersize that comes up and what we are expected to do.  +4
- Don't use commands not really introduced/discussed to save time. It was sometimes confusing. 

- The conflict example could be improved so that it would demonstrate the merging needs better. In one line f.e. (master) 1 spoon of milk; 2 pools of toxic; (branch A) 2 spoons of milk; 2 pools of toxic; (nranch B) 1 spoon of milk; NO TOXIC!!!; The current one just "used" one of branches and did not save anything about the other.
- [name=xxx] explains very well, thank you!
- for next time you could even out the pace between sessions, yesterday was so slow I finished the exercises and even some optionals before even being put into the break rooms, but today I fell behind immediately.
- I enjoyed it when the instructor followed the material exactly, instead of doing *almost* what was written. If I have to name smth that could be improved, I'd go for timing, it felt at times that the time was underestimated. However, since this is the 1st time it is given in the online format with many more participants, it is amazing how you manage it!


