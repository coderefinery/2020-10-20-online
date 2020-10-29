---
permalink: /hackmd-day4/
---
# October CodeRefinery HackMD, day 4

## Icebreaker, day 4

The "helper" in the breakout rooms: what is a better name for their role?
- Tutor +3
- Facilitator
- Code Masters
- Code Refiners
- Helper :+1: 
- Assistant
- https://www.thesaurus.com/browse/helper
- Guide
- The Auditors (of Reality)
- Exercise leader
- Minions
- Acolytes
- Expendables
- guardians of the refinery
- stack overflowers
- Senpai
- UnforGITables
- baby bugs
- deputy assistant educational communication junior executive managers

How are the breakout rooms going in general?:
- good
- so far so good, no complain! :+1:
- Good, I guess the quality correlates directly withN the experience of the helper.
- Helpful
- Works well!

## Intro questions:


## Reproducible research


### Break-out session 1
Reconvene at 9:35

#### Discuss with your neighbors or among all participants
Computer programs are expected to produce the same output for the same inputs. Is that true for research software?
Can you give some examples? What can we do about it?

#### Word-count example
Let’s look at [an example project](https://github.com/coderefinery/word-count) which follows the project structure guidelines given above.

Since we’ll continue working with this repo, import it to your GitHub namespace by clicking “Use this template”. This generates a fresh repository from a template.

This project is about counting the frequency distribution of words in a given text, plotting results and testing Zipf’s law. We have subdirectories for raw data, source files, documentation, processsed data and results, and README and LICENSE files.

What are the requirements.txt, Dockerfile, and Snakefile files for?
Do you think this project is reproducible?

#### Group 16

Research Software Problems:
- Messing up input files, not finding old ones
- different software doing the same thing give different results
- different machine -> different results
- how to treat special cases/special solutions
- different defaults
- different versions of the same software

What can we do about it?

- Put it all into a big data blog, code, inputs, publication
- Read the documentation
- Document everything

- Are you using version control? - 
- How do you handle collaborative issues?
- How would you like it to work if you could decide?


#### Group 11

- Are you using version control?
Yes, we use git to track the changes in our own codes, but never use it for collaboration in a large project.

- How do you handle collaborative issues?
Use a log file and send code through email.

- How would you like it to work if you could decide?


#### Group 4

- 


#### Group 15

- Package management can cause problems, its not trivial to replicate the same python environment that was used in producing some research, especially as time goes on and new versions of packages are released.

#### Group 8

- requirements.txt: which python packages and which versions



- Dockerfile: creates a fully operative environment (includin python distribution, nano and the repo) on top of the reference operative system. Interestingly enough, it installs python packages one by one and does not use the requirements.txt file present in the repo itself

- Snakefile: defines a series of operations and each time states which python files have to be executed and with which input files (the exact workings are misterious to us). Also allows to determine the number of threads/ parallel processes.

#### Group 14

- requirements.txt: In general well-written, versions of the used libraries are given. No need to state the versions of the software used to build the documentation and check the python code style. Python version used for testing this software is not known


### Compare requirements.txt:
A:
- No information at all. +2 
- This doesn't seem like a good strategy.
- Which version of scipy? etc. +16
- no information of project
- .

B:
- Packages and versions are clearly given, but the master branch of the git repositories is given, which may change in the future
- Only packages are given, it implies that the repo works with the latest version, which may not be true. Dangerous.
- list of softwares, or minimum requirements but no further information
- One problem I anticipate with this approach is when th master branch evolves it might break our code
- .

C: 
- I don't know what these git links are. Would be useful to have a word on it.
- I also don't know exactly the meaning of the git commands. However it 
- 
- 
- 
- seems the best alternative, since it specifies the exact location and commit from which to clone.+1
- Does seem possible to do automatic linking with this one.Documentation will probably be available in the github.
- The git links are the path to a source code bundled as a python package. Ideally, I would upload it first as a python package on PyPI (python package index) and then simply wrtie the package name in the requirements.txt like how the other packages are listed along with the version number. This makes for a clean dependency management and the package itself can also be used by others just like how you would use numpy or a pandas.
- I think this is the best way to state the requirements file. Version numbers are given and for each git repo a specific commit and/or tag is given to clone. +2
- software versions given with link to master branch 

D:
- This seems to be the best description for me. Precise information given. :+2: 
- What does "someproject" mean? And what about "anotherproject"? Where does this version refer to?
-  _I'm not sure about the suitability of C vs D
- . "Someproject" and "Anotherproject" are probabaly git repo's and not libraries that can be pulled by pip/conda. The git clone links should be given.
- I thought someproject and anotherproject are just generic names for this example. If not, it is of course a problem.
- Here you have to manually search for the project / repository on github & the version. What if you don't know the repository link? 

E: What problems do you forsee when you write down minimal version constraints like `scipy>=1.0`?

- Future versions of the package might depreceate some functions or change how they work, or have different dependencies +2


Related questions:

- Can python or similar generate and read requirements.txt or is it meant to be created and read by humans? 
  - often written by humans and read by humans but also used by tools (tools like virtual environments, Conda, Binder, ... understand this format)
  - another popular and standard format to document Python dependencies is environment.yml (Conda) 
  - yes it can. Try 'pip freeze > requirements.txt' and you'll have all the packages in the requirements file. I don't remember the exact sintax, but there is something like a pip install that takes requirements.txt as an argument and installs all the packages therein.

- Does using the git+ statement in requirements.txt, just clone the repository or also install the package?
  - it downloads the package from github and installs it, so it expects that the repository/package contains specific files like setup.py or similar
  - this can be useful to test package installation during development before sharing it on PyPI (Python package index)
  
- Is D now better than C or still not good enough?  
  - D is pretty good, versions are defined, packages not likely to disappear
      - Thank you for the clarification
  - more advanced answer for library developers: if you develop a *library* which is a dependency of other tools or libraries, you may want to not over-specify dependencies: you may want to prefer version ranges rather than specific versions, otherwise this can create problems for the libraries depending on your library. 

- Sorry, missed what pip freeze does. Could you explain again in short?
  - write out the current environment into a requirements.txt file: all installed libraries and their versions ("freeze the current environment into a file")
  - Usage: pip freeze > requirements.txt

- I think I need refreshers for now about how to get myself into the git environment in terminal all the way through a few times still. I'm just still not certain of the order of commands and such
  - Good point. We should remind these when we now use new tools. We will point it out when restarting after break.


- what do you do if two packages require the same dependency, but of different versions?
  - then you have a problem, assuming both are in the same project :-) ("dependency hell") you can then try to convince one of the two packages to relax its version requirements. see also the "advanced answer" 3 questions up, exactly for this reason.
  - if these are two different projects, then you can set up a virtual environment or Conda environment for each of these
  - This is why I usualyl don't advocate strict dependencies for reusable software.  my attempt at getting people to design their software well: https://scicomp.aalto.fi/scicomp/packaging-software/

- when usingusig 'pip freeze > requirements.txt', should we edit the file and keep only the modules we directly import into our projects? otherwise, it seems to me that we could have a VERY long list of apparent dependencies that we don't really use in our project. 
  - I think there is a way to freeze only the packages actively installed (in conda you can do this with `--from-history`)
  - What I do to avoid this is that I don't `pip freeze` but rather I always first document a new installation to `requirements.txt`, then I install it from that file, then I end up only with the "first-degree" dependencies. (+1)
  - If you use this to say, publish a paper, your results may depend on the exact version of nested dependencies.
    - I agree, for a paper I would document all dependencies, the full `requirements.txt`

- lets say package A depends on package B. If I keep only package A in requirements, is it safe to assume package A will require the correct version of package B?
  - depends on how much you trust it!
  - If freezing an environment for a paper, may as well freeze all
  - If freezing an environment for you to use later, I usually freeze the minimum.

- In R my packages update automatically, is that something I should shut off when I finish a project? I don't know how to shut it off for only one project since my packages are commonly shared between projects
  - For R I recommend to use https://rstudio.github.io/renv/articles/renv.html which is very similar to virtual environments in Python. This creates a `renv.lock` file which documents all dependencies. Each project can then have its own `renv.lock`

- I have to use Matlab. Is it so that it is enough to put only the matlab version.
  - Documenting the version is good. Sorry I don't know matlab well enough but how do you install libraries in matlab? Or is everything already packaged as one package with everything? 
  - I would indeed mention the MatLab version you are using and all the additional packages you use. For example, you might have installed the Signal Processing toolbox. Annoyingly, if you haven't installed the right package, MatLab doesn't always give this as an error, but just says a certain function is missing without referring to the missing package...
  - Thank's. I don't even remember if I've installed packages. Good real-world example! :D
  - Pretty often all the toolboxes (or all that you have licence for) get installed automatically, so then one might not notice which function was "core" Matlab and which in a toolbox, until it breaks when you try to run it somewhere else ;)

- Very general question: the very first thing was to put everything related to one "project" in one folder. But how do you define a "project"? I have stuff that starts up as one "simulation project" that ends up being used in multiple experiments/papers/whatever
  - Putting everything into one folder indeed assumes that we don't reuse things across projects but we also want to reuse things. So if a code gets used in several projects, it can become a library, and perhaps should live in its own Git repository. There are ways to include Git repos in other Git repos. Another option might be to put the library part into PyPI or Conda or CRAN and to use your own code as library in multiple projects.

- General feedback point: I don't like this glancing over content. I would prefer either covering it in a depth that I can actually use it later on (like we did with git last week), or leave it out. Now I'm just getting slightly confused between all the different things covered. :+1:
  - I second this, it leaves me confused and in a blurry state. 
  - Thanks for feedback. I understand.
      - Sure. I also understand there is limited time and these are probably all really important things. But my capacity for learning is also limited, I guess.
        - We will comment on that so that we do this better in remaining sessions.
    - I sort of like getting a brief overview of stuff that's out there, so that at least I know what exists and can look further in my own time. But there is a balance, the question below is a good example of too much detail which is just confusing for me.
      - Thanks for the feedback: Since we're short on time I tried to give Snakemake to the break-out rooms, so you have time to explore and discuss.
      - As a helper, this needs to be communicated upfront, because it means I am also assuming the role of instructor.
    
- what does "record the environment in the image part or the recipe part" mean?
    - where was this mentioned?
        - at the end of https://coderefinery.github.io/reproducible-research/04-environments/
    - this refers to containers where you can create images from recipes (e.g. Dockerfile or Singularity file). You could either take an image and add your dependencies on top of it (this would be "documenting in the recipe part") or you could install all your dependencies into an image and publish that image ("in the image part"). We glanced super quick over it so it's not your fault if this is unclear after 2 minutes of explanation. Happy to talk about it more after the session today.

- Is it good practice to create the virtual environment inside the project repo and then .gitignore it? Or is it better to have all virtual environments in the main python installation folder?
    - You normally want to track changes to your `requirements.txt` in your git repository because it reflects the dependencies of that repo, the environment folder itself (e.g. `.venv`) is system-specific and should be ignored.
    - As to where to place them: I like to create them into the project folder, then I see the venv in the same place as the project and don't forget where they are.
    - Its's the other way around. You first create a virtual environment and then start working on your project inside it. Right from cloning the git repositry to everything else that follows it is done after you have created the virtual environment.
        - Things like this are really useful info, thx!


### Exercise: snakemake
20 minutes, until xx:37
https://coderefinery.github.io/reproducible-research/05-workflow-management/#exercise-using-snakemake


Breakout room status:
- 10: snakemake help (check)

- 16: 
    - we had to exlain snakemake first, we did not go into snakemake exercise at all, breakout room time was way too short
    - windows and snakemake exercise gives errors, I guess the python scripts are not plattform independent, or the pipes.
    - 

- 9: we had an issue with "&&" in the echo command in one step

- 18: Error when running `snakemake -j 1`, need help
    - Which error? I got "one of the commands exited with a non zero exit code"
 - yes, same error. Although some MAC and LInux users are able to run it successfully, whil other aren't
     - I am on Windows and Anaconda.
     - SOLUTION: delete the echo and make sure the shell command is similar to the script on the website.
- Which echo? 
    - There is a command chain in the snakefile (under the rule count-words) including an echo statement. This is currently in the file:         
    '''
        echo "Running {input.wc} with {threads} cores on {input.book}." &> {log} &&
            python {input.wc} {input.book} {output} >> {log} 2>&1
        '''
    - Just delete the line containing the echo so it is similiar to the script on the website. I believe this is only an issue on Windows systems.
    

- I changed to this line but still didnt work: shell: 'python {input.wc} {input.book} {output} >> {log} 2>&1' :+1: I have the same problem.
    - Can you specify the error message you get?
    Error in rule make_plot:
    jobid: 4
    output: results/last.png
    shell:
        python source/plotcount.py processed_data/last.dat results/last.png
        (one of the commands exited with non-zero exit code; note that snakemake uses bash strict mode!)
    - Ok, same error, different location in the script. Don't have a solution ready for you yet
    - My error was that I didnt have installed numpy and matplotlib. So I did that and it worked now
    - Thanks! Alright, perhaps that is the issue. First step is to install the dependencies and replicate the project devlopment environment. Then go ahead and run snakemake. I see that these steps are mentioned in the exercise previous to snakemake exercise. Because that exercise was skipped, it resulted in a confusion. 

- When we create a conda environment and then use pip to install a package, how could we make sure that package will be installed in the conda environment?
    - I tend to check that with `which pip`; it will show the location of the `pip` executable which should contain the location of the virtual/conda environment. To activate the environment run `conda activate my_env_name`.
        - If you activate an env, any installation will always be into that, right?
          - yes


- Should I add snakemake to the PATH environment variable? 
  - if you run this in Anaconda prompt on Windows, then the executable should be visible without adding it to a PATH environment variable. Or are you on a different operating system?

- No, we could not succeed, maybe you can show in the main channel now? +4
  - We will go through this after 12 CET.

- That was now completely useless for me. We could not get over the first line, I have no clue about Snakemake now. +1
  - indeed many were confused by this. We will explain after 12 CET but apologies if this creates scheduling conflicts.

- I got errors because I was on the wrong shell (zsh instead of bash)
  - good to know. we need to remove bash-specifics. I am opening an issue: https://github.com/coderefinery/reproducible-research/issues/130

- 2: We followed the first steps of motivating having a script with commands, that was quite straightforward. Then the step to snakemake was extremely steep and we struggled to understand what .book was, the different ingredients of the rule construction, and in fact the point of snakemake. The only way some of us could identify some of what was going was because we had seen makefiles before. A walk-through and introduction to the different snakemake components, as well as demonstrating on a minimal example would be helpful, before going to a complicated one. +1
  - We should have done a walk-through first, before the group exercise to show commands and explain the point of this tool and exercise.

- (feedback on Excercise: Snakemake): It would be perhaps nice for the lecturer to go over excercise before we head to the breakout rooms like was done last week by [name=staff]. :+1: :+1:
  - thanks for feedback, indeed this is how we should do this next time

- [name=staff]'s style was way clearer and easier to follow. I don't feel I learned anything yet and got more confused with this lecture style. Too much and not well explained. +1
  - thanks for feedback, we will adapt to this.

- I have a feeling that we have way too many areas discussed today. I can not follow anything anymore. If we want Zenobo, we could leave out snakemake or the other way around. +2 
  - indeed we need to show things more selectively, less, clearer

-> We can have a walk-through of the snakemake exercise after todays session (please stay in the main room after 12CET/13EET). Hope we can clear things up there :)


### Fair software
How to make your software reproducible
- https://fair-software.eu

What are the other alternatives for Zenodo?
- [name=xxx] In my opinion use Zenodo, it is the defacto standard at least in my area of expertise, but pretty common are also http://datadryad.org/ http://figshare.com/
- some alternatives are listed here: https://coderefinery.github.io/reproducible-research/06-sharing/#services-for-sharing-and-collaborating-on-research-data

- is the doi is connected to a specific commit, tag, release, or to the general repository? if I release a new oficial version, do I have to create another doi?
    - Both; you get a DOI per release and an overarching DOI for all releases of the project. A zip file is created from the released version and uploaded to the Zenodo servers.

- you cannot submit before answering all three

## Break

:::danger
Break until xx:03
:::

## Social coding and open software

you can find the slides here: https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/master/talk.md/#1

- The most concerning thing for me about sharing data/code is that I think it takes too much time compared to any benefit I can see (to clean up stuff well enough that I would dare publish it)
  - yes, many feel this way
  - you do not have to, just make your repository public, people might help you cleaning it up if it is public. Also cleaning up might benefit you as well, because you understand what you did 2 years ago.
  - Another unmentioned benefit of opening your code is that it outlasts your working environment. Many researchers work under contracts that leaves the copyright of their code with the employing institution. Open source code will be available to you even after your employment ends. Plus it will be clearly accredditing you as the originator / maintainer. :+1: (This is the most important point by far)

- What a cool comment. "I expose my ugly code. Who cares?" I will take this home with me and don't care at all.

- Could [name=staff] comment what would be a correct license to prevent stealing, making money from it?
    - licenses come in types. There is a type called 'non-commercial' which prohibits commercial use. I would look for licenses including the commons-clause: commonsclause.com. It often is attached to general source licenses. one example of this would be the Apache 2.0 license. You will find this license under the label "Apache 2.0 and Commons Clause"

- From chat: How would you track license violations? 
  - good question, as a normal person you wouldn't manage too much: you might find one incidentally.  In reality, copyright helps big people more than you, (+the academic expectations are more important.)
  - but then again, in academia the community is typically small and perhaps somebody else will notice
  - Enforcing your claim is quite expensive as well and success is not guaranteed

- In my field somebody was so clever to put a patent on data analysis code. Now it can not be publically shared, at least in Europe. Only in US it is open because the US government can make use of all patents. Really bad and it is now a major technique. 
  - Apache license prevents this kind of abuse, this is what sets it apart from BSD or MIT license.
    - Thank you. I guess for Europe it is now too late for this code.
  - Can you share a link to this? It would be great to show this as an example when we teach about licensing next time.

- Does the comment about Stackoverflow imply that every time you find a solution to a small problem there, you adapt it to your problem, you should refer to that post?
  - for non-trivial things I like to leave a link to the post to at least make clear that I did not invent it when others later copy things from me. :+1: 
  - 
  - https://legalict.com/2016/01/07/what-is-the-license-status-of-stackoverflow-code-snippets/

- It would be great to develop the next numpy, but even more great that I would have credit for it, and no-one else would get enormous sums of money for it. It's not for getting rich but prevent global major corporations exploiting everyone elses work. But my code is certainly not important to anyone. :D I like to publish all my awful code.
  - great point, the credit system has a lot of room for improvement
  - does anyone know the group behind numpy? No googling.

- Do I understand correctly that the default is "forbidden to look at", i.e. if there is no license, you are not allowed to use it in any way?
  - no license means: unclear whether one can distribute derivative work which means I would not touch it because later I would not be able to share what I do (journals may later "force" me to publish my code but I would not be allowed to)
  - There are private use clauses, but you enter a minefield. In general no-license-> Lawyers ->Do not touch!
     - This is the domain of EULAs, the things you never read and click Yes.
     - Do not touch yes, but how about just looking?
         - Practically looking is fine, if it is in the open. If you want absolute clarity, get sued and wait for the court ruling. 
         - This sounds very frightening and discouraging to even try to learn anything. That is why I like that code is hidden if it is not intended to be something that someone can learn from.
         - [name=xxx] To the previous comment. It should be the opposite, get familiar with the different type of software licences to share your code safely and with clear instructions for others on how to re-use. It is a good idea to talk with your research group about it and maybe arrive to a standard licence to use for the code you create. [name=xxx] (Actually ask your employer not the group, because if your employer holds the copyright and you publish it without their permission, you might be in trouble (unlikely in practice)) [name=xxx] true, but better come with a proposal that the employer can approve or reject :+1: 
             - As said above there are private use clauses in most copyright laws in the world. So looking is always fine practically. Just add a common license to your code. But ask your employer before, because normally the hold the copyright. 
  - Forbidden to redistribute original or derived works.
  - Software is subjected to Copyright law!, if there is no usage licence you need permission from the creator to re-use and make the output publicly available
  - There is a scope of "fair use". But it may not be impractical for most academic purposes beyond teaching. Here are EU copyright law limitations to its enforcement (from wikipedia): https://en.wikipedia.org/wiki/Copyright_law_of_the_European_Union#Limitations
  -

- I worry about being scooped, but not in the sense that someone will make money out of my code. Instead, I worry that a group with better funding/manpower will take my code, use all the ideas that I/we have worked for years to solve, and use it in a private fork/version to produce research results without ever giving us credit. Not even a proper license would help us in this scenario? Furthermore, if they have significantly better funding/manpower, their output can be so great that we can never catch up, and all the "low hanging fruit" will be harvested by this group, leaving little research for us to do. :+2 :
    - This is a legitimate concern, but there is a flip-side to this coin. Someone can see your code/method and your carreer is boosted by that funding from the other group because you start a collaboration. It depends on the field you're in and the sensitivity of the work you're doing.
    - I know of two cases where code was copied without giving credit and both cases were from closed-source. With open source you can at least "prove" that you were first by showing the Git hash.
    - The academic communities are typically small and if somebody copies code without credit, I think sooner or later the community will notice.
    - But your concern is very valid in particular if you are developing a "low-level" library (in terms of abstraction, not in terms of quality) which is not directly visible to the user. Getting credit for base libraries is problematic. Make sure to collect usage metrics somehow and that the code using your library should cite you. Make your code clearly and easily citable so that you can measure usage.
    - In my experience there are two kinds of code a) code so bad nobody can use it, so basically useless for anybody outside b) code that is soo good, it is disadvantageous to not cooperate. With people having to publish there code more and more your fear will subside with time. At the moment, this fear is still valid in certain areas. On the other hand if you open-source your good code, you might gather lots of people who contribute and this easily outpaces the evil "high-man-power" group.

- What is the threshold between "rewritten code in language Y"/non-derivative work and a protected design pattern like fx. a propietary algorithm?
     - "Protected design pattern" this is murky area: for instance it is not possible to copyright an "idea" as such; If an algorithm is patented rewriting it in a different language wont help you much, but this has nothing to do with copyright law. It kind of depends on how much you looked at the original code.
     - note that rewritten code in language Y often *is* derivative work


- I am confused about the entire licensing lecture part. If we write code, should we directly get a licence on it? If we don't then people cannot use it? If we need to get these licences, where can we get them from?
    - This is a legal issue and cannot be presented deterministically by code refinery. Any conflict and specific advice should be given by/sought from legal professionals. Universities/bigger organisations usally have specialiced staff for that.
   - Ask your employer/legal department! Then use a standard license
   - In practice this mean: use a standard license for your own code, and clarify license before using other people's codes (often you wnnnnhave to be have to be have to be )
- Who has actually the ownership of the code when I leave the university? 
     - It is sometimes stated in the contract which you signed with the university.
     - Ask your legal department, noone here knows your specific situation and I have no idea what I am talking about nor does anybody else. At least not enough to protect you if you do the wrong thing. (Okay in reality normally nothing will happen, it is a bit like walking a red light, normally fine but you might get hit by a lorry.)
    
     
- I heard that the code is mine, but the data is not.
     - If you are employed by the university in most cases (look at your contract) everything belongs to the university (i.e copyright holder).
     - Depends also on the country. Sweden seems to be an exception in the sense that the code is possibly yours in terms of copyright. 
         - I think my work contract did not specify something like this, just my work hours, overtime, length of contract. Yes, contract is from Sweden. 
             - Ask your legal department if you want to know. Or just do it and maybe you get sued and then the court ruling will tell you. Please tell us afterwards, we are always interested. 
                 - :-) 
                 - this is very risky, since the ruling may entail that you are not allowed to use your code anymore.        
                    - that is why YOU should do it, not me. 
                        - you troll!
                            - yes, sorry copyright law is extremely complex, and finding out absolute truths entails court rules and massive sacrifice in money and time. So please you do it or follow best practices (ask legal department/use common licenses/ do not touch unlicensed code)
- If I don't licence my code, is nobody allowed to use/share my code? Or is not licencing my code a "mistake" from my side, and can everybode then do with my code what they want?
    - a) is it really your code? If you got paid for it it might not be yours
    - b) if you do not license the code nobody can use it.

## Snakemake demonstration

- What is the advantage of Snakemake over a bash script? I can see how Snakemake creates the workflow.
  - great question: if the whole thing takes 30 seconds, bash script is probably simpler. Advantage of Snakemake (or other workflow managers) is if the whole pipeline takes longer and many steps and many files and you change something "in the middle": then you don't have to rerun everything every time. Workflow will figure out what changed and what needs to be recreated and only recreate the outputs which are "out of date". 
    - Could I mix with Snakemake Matlab, Python, C++ programmes?
      - yes, the actual steps can call any language. so one could use a workflow manager to "orchestrate" many smaller steps that can be done by any of the above.
        - Thank you. Good to know. Seems to be worth looking into it!
          - yes also note that there are 100 or so tools similar to snakemake so the main message here is that workflow tools can be useful to "document" computation steps where you don't want to rerun everything every time
            - Understood! I did not know any of them, so this is a good start. And I know scientists who don't know this at all. A little step along the way to become better and more reproducible, in particular if one has to handle big data files.

- Could we say the main advantage of using sankemake is to automate Input/Output process?
  - yes but also scripts can do that, see above questions where we discuss pros/cons

- Snakemake is only for Python?
                    - no the steps can be in any language
                    - you can invoke runtime environments and languages as you would in normal shell commands (fx. "python script.py")


- Is snakemake more focused to test code or to batch process data and get results?
  - more for batch processing. good if you have many steps and many similar input files and if the steps take more than just a second (for super short post-processing, "normal" scipts may be simpler)


- How is "snakemake" different from "make" ?
  - very similar, basically a reimplementation. "make" is equally good. snakemake has better integration with running on clusters.

- I assume when we want to mix languages in Snakemake, the languages need to be command lines based, right? Matlab could handle this.
  - right. command-line based. anything that you can run on the command line can be a step in a Snakefile

- Suppose that I use a modify a code with MIT license. Then I want to relaease my code. Of course I will need to reference the author of the code in my code and paper, but do I have to release my own code with MIT license as well?

:::danger
Break until xx:45
:::

 


## Feedback Day 4

Please write here something positive about today and something that we can improve on

- Very interesting and useful topics. Everyone doing a research education (e.g. BSc/MSc, PhD, Postdoc) should learn about reproducible and FAIR science. Thanks for creating a very good intro to this wide topic, and thanks for gathering useful resources for further reading! +1
- The first hour went quite fast - it was confusing that many exercises/discussions were skipped. It was hard to know which exercise we were supposed to do when the breakout rooms started.

- [name=social coding]'s lecture was very interesting, still a bit fast (but he also realised it :-) Thank you), but luckily there is the recording and I will watch it again.
  - Maybe it is worth to extend the course to more days even further?

- The first past of the day was hard. Select better the material and don't say we won't cover it now, it is somehow stressing. Make a better selection (and point out where one could continue reading.)
The whole confusing about the exercise 4 could have been avoided by doing exercise 3 first, at least for me. [name=staff]'s explanation of the exercises on day 3 was a good example! Clear, clear instructions, we knew what we had to do. 
The after session with [name=staff] helped to fix that I took something home with me from the first part of the day. Thank you very much.

- [name=staff]'s mic volume is lower than the other lecturers'. I want to learn from you but I found it difficult to hear. [name=staff]'s mic is the most crispy among all.

---
*Always ask questions at the very bottom of this document, right above this. Switch to view mode if you are only watching.*

*We are monitoring this hackMD, but we will reply every now and then so that you can focus on the speaker.*
