---
permalink: /hackmd-day6/
---

## Icebreaker, day 6

- Do you use continuous integration (or any form of automated testing) for your work? If so, to which degree?
  - Not at all. +4
  - Automated generation/deployment of documentation.
  - doctest in C++. +1
  - unittest in python


- How is this online workshop format working for you? What are the differences against following our materials individually?
  - Love it! Much more convenient than waiting for the workshop to be given on site. +1
  - Very well! Doing the workshop and exercises in groups has many benefits, for example through the many discussions and group exercises. It also makes more sense to learn about collaborative code development together.
  - The breakout rooms where we can get our doubts cleared in a personal manner
  - Your team managed the online workshop very well, the instructors and helpers were great, the content was useful. The six mornings were the right length, in my opinion. I have learnt practical new skills, so thanks. I do however think that I would have found it a lot more fun to meet you all in person :) 
  - The online format probably lowered the barrier enough that I actually registered! I feel I might still get more out of an in-person workshop, but then I might have never found the time to sign up for one, and/or never bothered to go through the materials on my own 
  - Great. Impossible for me to attend otherwise (in person). I liked the group I was in, low barriers, a very good helper, very good instructors. Good course material. I think the course could even be longer.

## Automated testing
https://coderefinery.github.io/testing/

- How do you test a code if you don't know an expected result like a certain temperature?
    - can you give an example?
        - I have 2D images and I want to extract data from them. It is not a simple calculation like [name=staff] just showed. Materials composition can vary, I don't know what I find. How does one test something like this? [name=staff] knows what he puts in, what he expects.
            - I think for a test you always use known inputs, right?
                - I think so too, I have to generate some dummy images.
                    - Yes for tests you should know what output the input generates. For physics problems we often use testcases which you can solve analytically, as a test case

- How to test a (e.g. Snakemake) pipeline?
    - you could add files which verify the targeted files as a (final?) step. 


- I am working on a package that generates mp4 and gif files from data. I would like to create test(s) for this. Would I just test whether a file is created at all? Or use e.g. a hash to check it is exactly the expected file for a certain input? I don't think the file generation process is exactly replicable/deterministic across operating systems. I guess the broader question is: how precise should a test be?
    - how bad would it be to not detect failure? Do you have to be certain that the code produces error-free output? Or is there some form of constructive feedback in the development target? 
        - I would like to publish in JOSS and they require tests.
    - In general comparing these kind of output files is very difficult, because as you said, jpg and mp4 can differ in unimportant ways but make your test fail. I guess you have an intermediate representation, right before you convert it to the mp4/gif file, can you test that data?
    - Picture comparison is hard, I think google did some things on it, but most people say, do not do it. Of course you can test, if a file was created. 
    - You could have coarse tests like checking for approximate file size, cpu time used (on larger jobs).
        - That was roughly my thinking, yes.

- Why is a global variable bad? 
    - it is outside of the scope of the function. If you read the function/method as a dedicated functionality, outside assets are hard dependencies to achieve that functionality. But being outside of your function scope they can be subject to change through other code and thus tend to cause issues by changing its state, location, or existence.

- I feel like automated testing would be difficult to do when I'm writing scripts to run experiments - I can't have stuff run "automatically" if I don't have the experiment connected to the computer (but I do do a lot of testing, just not really automated). Would love to hear if someone has input/ideas/experience on how to test stuff that runs experiments
    - I think the term mocking comes into mind here. So you write a class which simulates your experimental machine. It recieves the input and does the same output. For testing you plug-in this "virtual" machine and run the code. It is not perfect, but it will cover a lot more. 
        - Yes, although of course my "experiment" often is not just a single machine but more like 10 different insturments that I need to control all of, and in a different way each time. But I see that aiming for something like this might at least lead to a bit more modular code ;)
            - So you have to write 10 classes. Writing tests is sometimes painful, but failing experiments are painful too. 

- Does it count as testing as well when I implement functions, if-statements to check what are input parameters handed over by the user? 
Would you recommend a function or is sometimes an if-statement sufficient?
    - That is not testing, that is input validation. It is also very useful, but these are not tests. 
- how to create test functions for class member methods? should the test be within the class or outside? +1 
    - https://stackoverflow.com/questions/39395731/testing-class-methods-with-pytest

- The Sphinx-built webpage seems better: searchable and has ToC.
  - Thanks for feedback! we are considering migrating other lessons to this format. One reason we are hesitating is that we want to be similar to Software/Data Carpentries lessons also.

## Exercise 
https://coderefinery.github.io/testing/pytest/

until **xx:42** (let us know if you need more time)

**goal**: run the test using pytest, then break it and test again

extra: try the pre-commit hook exercise as well (but we will also show this part in the main room)

Statusupdates:

- room 1: done
- room 5: done
- room 7: done
- room 9: 
- room 6: done
- roomx :-1: 
- room 16: done
- room 10/11: 2 done, 2 with installation problems


- I could commit the changes even after breaking the code. (I am in windows). Seems it does not fully support Windows.
    - Is this in the pre-commit hook part (that we are about to do)?
    - I got it to work on Windows using Git Bash by following the Linux instructions (other than I didn't need chmod)

- How could we check the variable types? For instance if I expect to receive only string or integer or a list.
    - python is not very type-stable. There is the isinstance built-in method.
    - a [solution from stackoverflow](https://stackoverflow.com/questions/2589522/proper-way-to-assert-type-of-variable-in-python#answer-2589572)
    - here is a blog post on that checking types in python (with optional static typing): https://lat.sk/2017/03/type-checking-assertions-exceptions-mypy/

- [name=staff], could you please wrap the earplug's cord around your left ear (or right ear) so the mic is hanging right below your mouth? That mic doesn't collect your voice very well.
    - seems fine for me? +2
    - the problem is that when he moves around the mic moves far or close to his mouth, so the volume is not consistent.
        -

- Comment: If you are using spyder (or other) with **iPython** you may have to put a '!' in front of the pytest call: `!pytest -v example.py`
  - thanks! I will add this to the material: https://github.com/coderefinery/testing/issues/100

- are hooks also added to the repository so that others get the same behaviour on commit? +1
    - client side hooks will be only on your local system. Server side hooks (as we will learn shortly) will implement the same behavior (running automated tests) for anyone that commits to the repository.
        - but is the hook file uploaded to github? If no, how can I share local hook files wtih ohters? I am sutkc with remote tests only?
          - you could add them to your git repository and sym-link them to the .git/hooks folder and add a script which creates these symlinks.

- I explored .git/hooks/ folder. Is this what [name=staff] is talking about? Seems there are more little scripts inside. git commit checks automatically the content of .git/hooks ?
    - correct
    - Yes, the scripts that are already there are examples, which have a .sample extension. This prevents them from being run.

- How does git commit know to execute the pre-commit?
    - it checks for a file named pre-commit in the .git/hooks/ folder if it finds the file it executes it
        - Was it a necessity to name the script pre-commit or would have any other name worked as well? Is the name 'pre-commit' somwhere defined inside git? 
            - Name matters, there is one name for each type of hook.

- how does git know the test failed? when pytest finds an error, does it signal to stderr?
    - basically yes
    - it looks at the return code (0: success, non-0: failure). in this case it was pytest which returned with non-0
        - so can I use other types of error catching strategies, like try/except, or even munal if [stuff] then sys.exit() ?
        - would it detect error handling methods inside the tested function also?
            - It is a bash script, so in general no it does not detect python error-handling. The hook should just care if your pytest run fails or not. I would not overdo it. All the language depended things and program dependent things should be handled by your tests.
        - Any kind of program that exits with 0/non-0 should work :+1: 

### Break

:::danger
until xx:04
:::

- In the exercise, a and b were integers and strings and the tests were written for integers and strings. What if instead an integer or a string there  is a 2D array of integers or floats? Let’s say 1000x1000 array. Does one have to  write tests for 1000x1000 arrays or testing of e.g. 10x10 arrays will suffice? 
    - depends on what you want to cover with the test. If it is iterating array dimensions then the smaller one may suffice. :+1: 
    - An interesting test case is also what should happen when you add a 1000x1000 array and an integer
      - this is also a good motivation to add tests in languages without strong type system (such as Python) since you don't really know what type you get at runtime


### Github actions
https://coderefinery.github.io/testing/gh-actions/

## Exercise
https://coderefinery.github.io/testing/gh-actions/
until xx:34

**goal**: up to step 4, or as far as you get

breakoutroom status updates:

Room 7: around step 5

Room 10/11: Step 5 for half the group

room 6: at step 5

Main room/stream:
- we can share our repositories here then

room 15:
- Last steps

room 1:
- a little more time would be good (we're at step 5/6)

room 4:
- More time will be great. Thank you.

room 8: 
- 2 participants fixed each other's issues

Room 12:
- A little more time would have been good (Step 4-5)


- Step 5 says: "git pull origin `master`", should not it be `main`?
    - True, good catch!  Github's new default
    - Thanks also for this: https://github.com/coderefinery/testing/pull/98

- Can I set up the Github actions to reject those commits being pushed that break the code? Or is it the client side's responsibility?
  - I would work on branches and then you can "reject" broken code by not merging it. It can be still useful to be able to push unfinished code to side-branches so I would not block that.
  - You should also use branch-protection for the master/main branch in your github settings, so people have to go via PR and cannot just push onto main/master.


## Break

:::danger
until xx:51
(you may go to your breakoutroom and say goodbye, since there will be no more breakoutrooms during the remainder of the workshop)
:::


## Modular code development
https://github.com/coderefinery/modular-type-along

- Really excited to see the integration between coding and testing. +2


- what do you mean by code refactoring?
    - If you have a working code, it is often desirable to rewrite parts; move things into functions, reordering code, you name it; all without changing what the code does: this is refactoring. Often this is triggered by reuse: you find out you need parts of older code in new functions.
    - "refactorig" = rewriting to nicer/better/simpler/readable/more efficient code while keeping the functionalty

- Really useful for climate models where various domains have to be coupled

### What is modular code development for you?

- writing functions or code that is generalizable enough that it can be used in various times and ways (e.g. splitting data cleaning from analysis)
- code that I can copy-paste to my other projects and it still works
- code that is reusable as much as possible
- code where I can replace X and it does not break all other components
- One function fulfills only one task. 
- Write code in separable units of functionality.
- 



### Your best practices to get readable/modular code?

- One function fulfils only one task. Break everyting ito smaller steps.
- Try to include others in project, or get feedback on your code. Oftentimes, a once modular code turns non-modular due to laziness. This will often be frustrating for others trying to use/develop the code, which they will then be quick to point out.
- organize code into functions which have no side effects
- Avoid use of global variables, keep state local as much as possible.
- Avoid repetitions, if you need global variables write a service for reading them. If you need to write global variables, establish event pipelines to listening modules.
- Wrap modules in semantic layers (human-readable named functions call low-level functions)


### Questions

- is "modular code" more than just splitting a big script into self-contained functions, and then calling them from some master script/file?
  - splitting things into reusable components is I think the essence of modular code development. In practice it's often that: organizing functions into modules, splitting too long functions, collecting modules into packages, reusing.

- Can we organize the main practical recommendations into 3-5 rules of thumb that we should keep in mind? (for example for me, if you copy and paste more than three times, think of a better way)
  - great question, here is my (biased) opinion, I would love to hear from others:
     - design code to be testable (or copy-paste-able)
     - if I need to scroll a lot, consider splitting it up
     - components should do one thing, not many different things
     - behaviour should be localized
 - there are coding paradigms which provide mnemonics for desiging your code. Relevant ones mentioned already would be "Separation of Concerns" and "Don't Repeat Yourself".

- Great comment: code is for other people, not necessarily for computers.

- "Solve the problem you have now" in a sense feels contradictory advice to writing modular code: the problem of not having modular code is a problem I will have in a year!
    - The key is balance. Only practice will teach you. 
    - Great observation :-) yes. This also means that it's OK to start with one long "ugly" file at the beginning and modularize as we go along.
        -    Yes and no. At some point you *know* that you'll have to clean up at some point. You can write modular code without generalising too much.
           - yes. great point. e.g. to be very careful about introducing global variables everywhere
   - Over time you get better at maintainable/modular by default.  Modular doesn't always mean more work.
       - you can settle on a limited set of design patterns for repeated issues with modularization. The first times are hardest, but reading "good code" really helps with that.

## Steps done in example, based on your suggestions below

1. version control setup with git (remember to commit)
2. .mean() from pandas library (using library)
3. functionalize reading the csvfile
    - add arguments (making the function more general)
        - num_measurements
        - csvfilename (adding csv to make sure that the input file should be a csv) 
        - key (which temperature to read from file)
    - rename function to describe what it does
    - rename variables to be more general: temperature -> column
4. functionalize plotting and saving results from above into png plot
    - add arguments
        - temperatures (result from above)
        - avgtemperature
        - outputfilename
5. for all new functions, create functional arguments such as key='Air temperature (degC)'
6. docstrings for the functions 
7. for loop around the functions for different number of measurements
    - output filenaming with adaptive naming
8. add `if __name__ == '__main__': main()` and create main function around other functions
9. parsing arguments via commandline (eg sys.argv or argparse or click (used in the example in material); the latter libraries also enable running the script with `python evaluation.py --help` to get information on which arguments are needed) -> no need to interact with the code anymore

## Suggestions for next steps for the example


- would write the sections in jupyter notebook, in separate blocks. so you don't execute all of them

- Use a library function to compute the mean: numpy.mean +1

- Implement a test if the `.csv` file is present and can be read
- Check if the column 'Air temperature (decC)' exists
- Put the code with "comment headers" in functions. +1
- not make num_measurements a global variable required in the function
- split each task into a function

- Modularise all the plotting into a function. Same for reading data.

- It is so easy to make suggestions to others when one does not have to do the programming himself/herself :-) Sorry, [name=staff]. You are doing great!
    - [name=staff] takes it so well :)
        - :+1:
- What happened there? The editor suggested a name? It was method and now it has a better name?
  - editor made it possible to abstract a section of code into a method (into a function) which was later renamed

- Pass the arguments to `ReadTemperatureFromCSVFile()`: filename, number of measurements +1


- but if you rename it to a genereic "filename", shouldn't it be clear that it has to be a .csv file? Now it looks like it could accept any kind of file
  - good point. this code here would fail if send in some file in another format. one could make this more robust by verifying inside the format first, or to indicate it by argument name or (if possible) by type or type annotation
      - Thank you. 

- What if you have some global variables like physical constants that a lot of functions will use. 
    - Keep them global?
      - can be OK if they are collected to a structure (in python i would use DataClass) where they are made read-only
    - copy them in every function?
      - we should not duplicate them because also physical constants can change
    - pass them as argument?
      - can be good but then I would collect them into a DataClass or similar so that we don't pass 50 arguments in but they are collected
    - How can physical constants change, please?
        - gravity varies across the globe, both for elevation and lat/long.
      - yes, some digits only (example: codata in computational chemistry which issues new version every few years)
          - But this happens on a very high digit position? 
              - yes and this can matter when computing with many floating point numbers
              - but the main point here is to not keep the same information in multiple places. what if somebody made a typo and a constant was wrong (in multiple places)? then the person needs to remember changing it in 17 places.
    - A constant is a function of zero arguments; functions are in a global scope also. Concerning the example of physical constants, most systems will have libraries for those. :sunglasses:
    
- in my opinion the code is a lot harder to read now. Is that a good tradeoff for "more modularity"?
  - often the abstract portions can be outsourced into other files leaving only their calls left to read and understand.
  - the csv reading function?
      - just understanding what the code does.
        - I would not consider the work done yet, at the end we would arrive with only functions (probably) and then the functions themselves are hopefully descriptive.
            - yeah it's better now.


- Don't hardcode the output name of the .png. I would extract it from the input filename or somehow make a connection to the input variables.


- We may need to set a delimiter agrument, in case the delimter used in the read csv file is different from the default. 

- As we extract a user-defined key, I think the output of the CSV-function should not be called "temperatures".

- It looks like its time to seperate the functions from the "script" part of the code. A python "module" or w/e it is called.


- Speaking about naming, `temperature` and `temperatures` look very similar -- use `temperature_array` instead.


- Functional arguments, would it not be better to do variable_name=inputargument in the functions?
  - good point, I like to do that since it makes it nicer to read when calling the function what these variables mean. This way I don't have to look at the function that I am calling to understand this.

- use pathlib to define files and folders. Otherwise you might have problems in different OSs. :+1:

- What do you think is the best practice? Putting your two functions in the same file or a different file and them importing them? 
  - Later I would like to collect related functions in a module: I would collect stastistics-related functions in one module, and maybe all plotting-related functions in another module.

- Write a small doc-string in each function what the function does. For these small functions it is obvious. But once functions are larger, this is very useful.
    - even here the role of the key argument is ambiguous until you read the code

- This project is getting complicated, we need to implement some tests! 😉+1
    - At that point you might want to isolate the main as `if __name__ == '__main__'`
        - I see this in python packages but have no idea what it means. Short explanation pls?
          - It means that when the module is called by another module (e.g. where you have your tests), the part below `if __name__ == '__main__'` is not seen by the caller. (https://stackoverflow.com/questions/419163/what-does-if-name-main-do)
          - if you import this file, this part is "invisible", if you run it directly, it will be run
              - "this part" = the part underneath the *if name = main*?



- does it make sense to include the type of something in its name? e.g. temperatures_list instead of temperatures
  - even better these days: type annotations in Python and you can use mypy to check types, example: https://docs.python.org/3/library/typing.html :+11:

- Is it good practice to put these four lines of code in jupyter notebook? only leaving the functions in the .py file? Seperate blocks than also provide modularity?
  - this could be good if you want to have several jupyter notebooks, all using some common functions. then the functions could live in a module which is imported to all these notebooks.
  - Code blocks in Jupyter do not equate modularity, in fact every block depends on code executed before. What Jupyter does really well is documenting what you do between the steps.

- You don't overwrite the name of the .png now with the 3 iterations? Edit:Okay, output name was changed.


- What if we ask for too many measurements, that is, more than exists in the file?
  - python loops indices right?
      - No. In this case `pandas` reads *upto* the amount of lines asked.

- Do we need still num_measurements_global=25 ?

- Will click do the test that the input is an integer and so on? If I don't want to have this interaction, would it not be better to put if statements into the function to check the type of the input parameters?


## Feedback
please give feedback below, one positive thing and something we can improve on

+ Great workshop! I will try to spread the word among the PhD students at our department at Chalmers university. I also think that making the recordings of the workshop easily accessible (easy to find) would be very usefull.
+ Sphinx website is nice to use, searchable and ToC. +3
+ Special thanks to [name=staff] for being super clear about what we were covering at any point - other instructors could make sure to make it as clear before each exercise what exactly were we supposed to cover! +6
+ Awesome workshop, thanks a lot!
+ Often I want to just mess around with the stuff we've learned after a session. Maybe it would be nice to set up a sort of "free-for-all" github repo where people can fork, branch, push, etc. to try things and interact with each other.
    + Or do a post-workshop practical free-for-all with a few helpers sticking around to help with issues
+ Great teaching material, I will be returning to these a lot in the future! +5

- First breakout session could include (more) time for introductions 

- I enjoyed the workshop on all the 6 days. Very informative. I have known and seen some of these things but never did them hands-on. I have already started implemented a few of these tools to my project. Thanks a lot ! +3


- the modular code development section and value of testing today was really great. It would be useful for me to have a section on workflow. Days 4 and 5 were pretty difficult for me to follow. I was having some issues with conda, but also I think I needed some more on the expected outcomes and practical utility of the different packages and such- this could also be improved with a workflow discussion.

- Maybe if there would be a way to tie the whole workshop into one project with your team. So that you don't clone new repo's every time, but continue on the same repo, first learning git and finally modular coding. 

- Modular coding was very nice, maybe a Q&A discussion with the helpers/team afterwards would be good as you can share some best practice
    - +1 It feels like there was a missed chance to learn even more from the fellow participants on how you all solved different issues.

- I really liked today's session. Tesing is very important as well as modular coding. Both presenters did it very well. I really like it that [name=staff] first in words goes through the excersizes we will do in the breakout room. As the breakout rooms are usually quite tight in time this makes the excersizes done more efficiently and more instructive for participants.+1

- [name=staff] did a great job today! [name=staff] was again super clear on the tasks. With Niket as helper in the breakout room it was very smooth. I got less stressed out today and did not have the feeling of being left behind. Maybe it was by chance, but I felt that the knowledge level in my room was balanced between participants.

- Being in a team with colleagues in the breakout room was fun, highly recommend. +1

- General comment: in the announcement of all the courses, I would recommend stating that next to the required software, it is recommended to have at least two monitors. Multiple monitors makes this workshop soo much more efficient for the participants. +1
    - I have only one monitor and manged it. (--> That's why I said recommended)

- I really liked [name=staff]'s document which kept track of his terminal commands. This makes it easier to reproduce what he was doing.

- Days 1,2,3,6 fit together. 4 and 5 felt a bit out of left field. Like, I appreciate that Jupyter Lab is nice and useful, but it didnt really fit the workshop theme for me.
    - Agreed. Sometimes it also felt like a lecturer was plugging something they themselves particularly liked. Can't remember what it was now but someone said "I'm using this, I won't explain it now, but it's great so look it up". Probably better to stick to the core of git and the very widely used things around it like sphinx. +1
        - Yes I think no one would have complained if we focused exclusively on git, GitHub, sphinx and testing.
        - Seeing Jupyter a little bit explained was super useful for me though

- Super impressed with the time-management ⏱ +2 

- Having constant action on HackMD was distracting but I dont have a better suggestion. Maybe it would be possibel to have some way to send in questions (hidden) during the talk and then have a dedicated time to go through them?

- I think that this entire workshop was organised really well. To host it online with over 100 participants is far from trivial. Special thanks to all the helpers and volunteers. Keep up the great work! I think in-person workshop would have been much more helpful but given that it is online, everything was handled well. I found the pace to be a bit fast, but then again there is a lot to learn over 6 days.

- Please don't use things that aren't explained. For example the IDE that was used in the last session. +2
    - or sometimes we did funky terminal commands with like four arguments/flags. So I just copy pasted them from the website, which worked fine. But I have no idea what they mean or how I should choose them for my own project.

- I think this has onestly been one of the most useful workshops I have ever attended. I am almost sad it's over :'(
    - More in the specific, I think that on the technical side everything was very well organized and explained. If I really need to add some critic, I share the opinion above that the Jupyter session was a bit disconnected from the rest. It is almost something that would deserve a mini-workshop on its own.
    - About the pace of the workshop, I think it was just right. It is true that most of the times we had to 'fly over' topics and not dive into them, but it's impossible to accurately do every topic mentioned. It's very good though that you gave loads of links and material to refine our knowledge.
