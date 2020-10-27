---
permalink: /hackmd-day3/
---


# October CodeRefinery HackMD


## Icebreaker, day 3

What operating system and what display setup do you have?
- Windows laptop, no external monitor (one 15'' screen)
- Windows laptop, with one external monitor. +3
- Windows laptop 13" (with remote Linux access) + external monitor.
- Linux on laptop + 27" external monitor. +1
- Laptop running MacOS Catalina + external monitor.
- MacOS Catalina 
- MacOS Mojave
- Linux Mint, laptop 15", no external screen
- Laptop (mac) with no external screen
- Ubuntu 18.04LTS in WSL on a WIN10 Laptop;<br> 13' Laptop monitor + 27'' external screen
- MacOS Catalina 13" laptop and external monitor +1
- Windows 10 laptop (Zoom), Windows 10 desktop with two monitors (coding)
- Fedora GNU/Linux, laptop + 27" external monitor, prefers half-maximized screen share.
- .
- Windows 10 host (zoom client) Monitor 2, Ubuntu 20.04 VM Monitor 1
- Windows 10 laptop with a 14" screen,no external display.
- Windows 10 laptop with 2 external monitors
- Linux Ubuntu 18.04, 2 external monitors (+1)
- Ubuntu 20.04 LTS desktop pc, 2 screens
- Manjaro linux 24"
- Mac OSx Catalina 13" with an external monitor
- MacOS Catalina 15", no external
- Ubuntu 20.04 LTS, dual-boot Win10 laptop with external monitor
- Mac OSx Catalina 13", half-maximized screen is nice. 
- MacOSX, one MacBook, 15", one screen
- Linux laptop 13", no specific setup. Jumping around.
- Ubuntu 18, only laptop screen: 14.0"
- Windows latop wtih 25" external monitor
- Gentoo linux, computer/laptop with external monitor, one screen.

## Intro questions:

- Not a question, but a comment: I would like to downvote the vertical arrangement of windows :) +4 -4 :)
- why is fast forward good? like, why would I *not* want to see a merge commit message there? I understand that it is logical to move the sticky note along as far as possible, but it's not obvious to me why you wouldnt want a notification of that.
    - Yes, Some people (like me) prefer the merge commit most cases
    - But if the mental model was "I added new stuff on the end", maybe the merge commit doesnt' have much meaning.

- Anyone else seeing an ominous flashing in the video over zoom? Looks like the zoom header thing.
    - Yes

## git-collaborative
https://coderefinery.github.io/git-collaborative/

### Concepts around collaboration
https://coderefinery.github.io/git-collaborative/01-remotes/
- How do you create a tag?
    - if its your own repo, you can see the tag next to the branch dropdown in the code tab, by clicking there you can see and create tags
        - So it is only a online github thing, not on the command line?
            - No, works offline too: https://git-scm.com/book/en/v2/Git-Basics-Tagging
        - there is also a git tag command, usage:  `git tag releasename`
    - I recommend to always create annotatet tags, then it's also clear who created the tag and it can carry some meta-information.


- How do we keep a fork in sync with the "origin"?
    - We'll get to that

- What is that "Watch" element next to the "Star"?
    - Click that, and you will receive email notifications for every event on the repository.

- I would be curious to know how to work with 2 different repos. How do we switch the origin? How does git know how to push to different repos when I work on different projects/repos?
    - You give each remote a unique name, "origin" is just the default name

- What if you have a GitLab account instead of a GitHub one? That still works?
    - No. These are competitors.
        - So I better create a GitHub one real quick. :thumbsup: 

- Be aware of the spelling of centralized/centralised! 





### Exercise
https://coderefinery.github.io/git-collaborative/02-centralized/#centralized-workflow-exercise
Ends at xx:17, then break until xx:27
Try to accomplish *steps 1-8*, we will do 9 once we meet back together.  If things don't go perfectly for everyone, it is OK since we start anew in the next part.

(it is better to share usernames by chat in the room, since this is a public document)

Write "done" when you are... done!

(group information removed)

### Break
:::danger
Until xx:27 - don't forget to get up and walk some!
:::

### Centralized workflow exercise, follow-up

- Could you emphasize on the difference between git pull and a pull request?
  - we will discuss this but: `git pull`: fetches changes from remote and merges them into my present branch. `pull request` maybe an unfortunate name for a change proposal/ merge proposal/ merge request (it's called "merge request" on GitLab)
      - "merge request" makes so much more sense.

- How to find the repository invite if it did not arrive via email?
  - one option is to check the github notification for the invited person (top right, bell symbol)
  - another option is for the administrator to copy the link "pending invite" next to the invited username and the invited person can visit that link and approve there

- In this excercise we pushed and then opened a pull request to merge our branch, right? Would it be possible to also open a pull request to push?
  - pull request really means merge request (name is for historical reasons, will make more sense later today in the forking workflow). Alternative would be to push directly which you can do if you are a "collaborator" and if the branch is not write-protected.

- How are "forking a repository" and "using a template to generate a repository" different from each other?
  - fork preserves all branches and history but "generating from template" "flattens" the history and creates a newly-looking repository with one commit corresponding to the last commit on the template repo
    - In what situations do we use "generating from template"? What are its use-cases?
    - if you want new repos to start with a specific structure but no "fork relation" to the template, in other words you don't intend to communicate any changes "back". example: you want to create new python projects with a specific folder structure but the projects are completely independent.


- How to write-protect a branch in github?
    - settings -> branches -> branch protection rules

- Is it common to submit pull requests through the website rather than from command line? Is that better somehow?
    - personal opinion: website is better. The GUI is good and it forces you to go through all the steps. 

- Is there as well a rejection button or the owner of the repo simply does not accept the pull request?
    - you can close a pull request without merging, which basically rejects the change

- What do you do when senior researchers do not want their PRs reviewed by you?
    - I guess life isn't perfect...

- what is the relation/difference between git pull origin master and origin/master?
    - `origin/master` is a name that indicates the `master` branch on `origin` remote.  `git pull origin master` fetches `master` from `origin`, updates the `origin/master` label (← that much is `git fetch`), then mergen that to your work

- So any change should always happen in a branch, unless you are completely certain it will (need to) be part of the main?
    - best practice: never push anything on master. Always make a new branch. It is considered extremely impolite unless specically allowed (which it never is). Unless you are the owner, then you can do what you want, but your contributor number might drop. Also live what you preach to others.
    - But, I [name=staff] realize that there are many more small personal projects that are not well organized than large collaborative projects.  Don't let perfection get in the way of using version control for everything.

- If you use the GitHub desktop client, it basically forces you to first pull from the main branch to make sure your branch is up to date. Have we discussed this yet? Did I miss it?
    - Good point, I don't think we've discussed this

- What is "-u" switch in the push command?
    - "this branch will remember that it default pushes and pulls from here"
    - Can you expand on this? What does it mean remember? The default is to push to a remote branch with the same name as the branch I am on locally, correct?
    - "remember" = "setting the branch upstream". Each branch has an "upstream", which is what I described.  Can be seen with `git branch -vv`, and controlled with other `git branch` commands.
 
- What if I'm the only owner of a repository? Should I also never push to master, but rather always use pull requests? 
    - depends. If you do not have other people you can do what you want. Using branches makes it cleaner and it is a better practice. Matter of opinion but I think I am right :).
    - Almost all of my repositories start with pushing to master until they become organized enough that pull requests have a benefit, and there is actually someone to do a review.
    - ok, thank you!

- What if in step 10 of the centralized workflow part I would just use the command "git pull", would it have the same effect?
    - If you are on master, then yes (unless the default upstream is changed)
    - If not, then you'll end up pulling to some other branch.
    - So basically, make sure you are on master and it should work (our extended commands make sure it works for everyone, no matter what stat they are in).

### Distributed version control / forking workflow
https://coderefinery.github.io/git-collaborative/03-distributed/

#### Exercise: 
https://coderefinery.github.io/git-collaborative/03-distributed/#exercise-practice-collaborative-forking-workflow
Lasts until xx:33
In the session, try try to do steps A-E.  We will meet back in the main room for the rest.

(group information removed)

- When (staff) chose the owner of the repo, one could see multiple names. Is he part of different groups/organisations with different names and he is able to work under different names on different repos?
  - I could create the new repo either under my namespace or under one of the organizations that I am part of. The reason why I created it under and organization in this case is so that I can fork it to my userspace. In the exercises you don't have this problem because somebody else creates that exercise repo.

- Can I fork a github project to my gitlab account?
  - You can either import it or you can have the repository on both and synchronize via your computer (one can also sync automatically), but to my knowledge you cannot fork or send merge/pull requests across services.

- If branches in origin are still not merged, and I do 'git pull origin' in my terminal, I only get the master branch, but not the other branches. Is that like this? So I can only pull the other branches once they have been merged to the master in origin. 
    - this depends a bit on your git configuration. Git normally pulls the branch you are on locally. I typically checkout the branch I want to pull, i.e. `git checkout test_branch` `git pull origin` which then pulls that branch. 
        - Ok, but, if I am in my local, and I have "master", "branch_A". But I want to pull from remote "branch_B", I just type `git checkout branch_B`??
          - yes, this will work. if a 'different(in the sense of same name but unrelated to the remote)' branch_B does not exist locally but exists on remote, Git assumes that you want to create a local branch tracking the remote branch.
              - It worked! thanks :)
    - it is possible to pull all branches, but I prefer to do that one by one

- Could I ask with respect to the previous question something:
'git pull origin master' will pull changes from the origin remote, master branch and merge them to the local checked-out branch. But what would I do if I want to pull not the master branch from the remote, but another one?
And would I have to checkout the local non-master branch before the pulling?

- my helper just merged all pull requests in our group. How can I now update my local repository to include all these? do I have to re-fork or something?
  - if this is the first exercise, then: `git checkout master` followed by `git pull origin master`. No need to re-clone.
     - yes first exercise.

- If I mention the "; closes #N" in the commit message, then make another commit after failing checks in the pull request, do I need to add the "; closes #N" again in the new commit message?
    - You shouldn't need to, as for as I know.




### Break
:::danger
Until xx:11 - don't forget to get up and walk some!
:::



#### Main room exercise repo

https://github.com/coderefinery/forking-workflow-exercise-october

Back from breakout rooms at xx:33. If your room needs help, please write here.

Group 18: One person could not push their change branch to their fork. Investigating via chat. Solved in breakout room.

- In our group, someone automatically closed their issue by naming the pull request appropriately. Is that necessary? What would be the manual method to do that?
    - It's a good thing if you remember, otherwise go to the issue and click "Close".  Then, I would note where it was closed.

- If you put "closes #1" in the title of a pull request or in the commit message, there is not a "linked issue" in the milestone coloumn when viewing the pull requests. Why not?. The linked issue shows up if you added "closes #1" to the description.
    - Good question, I don't know right now.  I'd think it should...

- If I file an issue, can you assign someone to resolving this issue? Such that not multiple people start solving it at the same time.
    - yes on github you can assign someone or yourself also after the issue was created, right side 'assignees', the assigned persons avatar can then also be seen in the issue overview
    
- What should you do if you commit and close a issue but later figure out that the issue is not resolved by the commit? Is there a way to merge (maybe the commit made some progress) but not close the issue anyway?
    - You can reopen old issues, or open a new one and refer to the closed issue. Normally you would make a new PR to fix it. 

- What if the forked repository has a different issue with the same number? Is there a risk for wrongfully closing issues?
    - issues and pull-requests have sequentially increasing numbers (i.e. even issues and PRs will not have same number). So the same repository will never have repeated numbers.

- Is there any way to edit a pull request, such that the start and target branch are changed?
    - yes, at the top of your PR you can change the target/source of a pull request, but this can be restricted by your rights. 

- When updating the fork, is it still good practise to make a branch where you pull the upstream remote and then pull request that to master?
    - As long as you do not develop on your own master branch, I would not care. Depends on how careful you want to be. I would do my changes on a separate branch and use my master to pull upstream changes.

- Can I set different fetch and push addresses to one alias?
    - I mean, why the remote -v shows: 
    - origin	https://github.com/(removed)/forking-workflow-exercise.git (fetch)
    - origin	https://github.com/(removed)/forking-workflow-exercise.git (push)

        - They are the same alias for origin. In this case `origin` is equivalent to `https://github.com/(removed)/forking-workflow-exercise.git `
        - I understand that, but why on earth the console prints two lines, if they are always the same. So the alias refers to the same line both pulling and pushing. What is the purpose of the -verbose doing this?
        - Ahh yes you can do that https://stackoverflow.com/questions/2916845/different-default-remote-tracking-branch-for-git-pull-and-git-push
        - In my experience you still should not :)- 
        - Yeah. I wouldn't but thanks for the link. Understanding the mechanics is always good even if you don't plan to use everything (f.e. for troubleshooting).
            - I was wondering about this too and with the stackoverflow I made it work:
                - git remote add origin https://github.com/project/forking-workflow-exercise
                - git remote set-url --push origin https://github.com/user/forking-workflow-exercise
                    - whoops, only --push works (--pull doesn't) 
                - Nice! Thanks.
                    - I just realized why this isn't great, because now when you do git graph you can't distingish between branches on the project original and branches on your fork (they're all called origin/branchname).
                    


- How did you linked pull request and issues?
    - just go to the webpage of the PR/issue and copy the url into your comment. Github does the rest. 
    - github/gitlab understands the words "close", "closes", "fix", "fixes" followed by issue number; both in pull request title or text or commit messages

- [name=staff]'s shortcut example mentioned twice master, but he said we should creat another branch. I was slow to follow. Should I rather not perform the shortcout in this way, create a new branch. But where would I place this new branch? In the push command? The pull requests remains as in the example, i.e. with master, pulling from master?
  - Ah now I understand, I think I did not read carefully or understand during the session and answered something else. It's probably this shortcut: https://coderefinery.github.io/git-collaborative/03-distributed/#shorter-route. This is to update the master branch with changes that happened "upstream" and in this case we don't need to create a new branch and in this shortcut we don't even have to define remotes since we use the URLs directly.

### Contributing to projects
https://coderefinery.github.io/git-collaborative/04-contributing/


- These last few minutes were super interesting, thank you! +2 
    - Yes they were, but a bit rushed unfortunately.
        - Is there a specific session at some point on git etiquette/practices?
          - Some of the etiquette/practices will come back next week when we talk about documentation and testing.

- Can you expand on: "If you receive pull requests with a lot of code, clarify its license and copyright". Do you need to ask the contributor what the origin of the code is?
    - In theory, GitHub terms of service say that you should only submit code that goes under the repository's license.  But, as an author, it's good to do due diligence and make sure 
    - More about that in https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/master/talk.md/


## Feedback day 3

Please let us know one thing that you liked and one thing we can improve on:


- Today was great overall. +5
    - Best day so far! +1

- Very interesting session on collaborative distributed version control. I finally understand what pushing, pulling and forking is about. Thor is a very helpful helper :) Thanks to the teaching team. +1

- Last few minutes on etiquette was really nice. This really helped me put things into procedural perspective. The two exercises also made a lot of sense. We didn't get around to conflicts between pull requests, that seems important so I think it could get some more time allotted, including breakout. +1

- Really liked the increased breakout room time and exercises focus. +4

- very helpful to have hands on practice with exercises. I knew some of the things in theory before, but never really got my head wrapped around it. Know I feel like I'm more likely to actually do things.

- All the exercises were easy to follow and give good insight into working of git. very informative session and. suggestions on forking that I will incorporate in my project.

- Very good session. I am lucky with my group and with [name=helper] as helper. I guess I wished we had more time for the last 15min explanations as they were very important and I was already a bit slow to follow up.
- Instructions for the exercises were clear today. Thank you very much!

- Could the colors in [name=staff] terminal be a bit of higher contrast? Sometimes it was difficult for me to see the darker colors on the black background.
  - thanks, I will adjust that for next time

- Today I made use of the video recording on Twitch because I missed a part of the explanation. Thank you for foreseeing this!

---
*Always ask questions at the very bottom of this document, right above this. Switch to view mode if you are only watching.*

*We are monitoring this hackMD, but we will reply every now and then so that you can focus on the speaker.*
