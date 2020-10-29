---
permalink: /hackmd-day5/
---

# October CodeRefinery HackMD, day 5


## Icebreaker, day 5

Remember some software you used/improved, that was very hard to use.  Why was it hard to use? (remember to be nice, though!)
- Code send to me without any documentation. Forces me to read the code, all of the code, to figure out what it does.
- There was documentation but it was outdated or for a different version.
- the input was not well specified
- Installations with incomplette dependency list.
- No explanation for why some of the choices in implementation were the way they were. No explanation for what some of the scripts were for.
- [name=staff] made a list of common issues https://scicomp.aalto.fi/scicomp/packaging-software/
- Latex, very difficult to do basic things like making a nice table. Error messages are cryptic

How do you make your software easier to use (or how would you)?
- What is the "entry point"? What script/file/thing do I need to run in order to "start" running the code?
- Copy-pasteable example that actually works and gets me started
- Example of inputs and outputs
- A READme file for starters. More than single line explanations somewhere.
- Very clear naming. Not afraid of long names if they help explain the state and pupose.
- Separation of concerns. Write very specialized methods with as few sideeffects as possible (none?)
- Abstraction layers. Layers of methods with high-level names like "run_service_x" that handles initialization and execution of functionality. The function header reads like documentation.


## Documentation:
https://coderefinery.github.io/documentation/


### Motivation

#### Exercise: is project documentation important
https://coderefinery.github.io/documentation/01-wishlist/#exercise-in-the-main-room
Is project documentation important why?

- Yes, it is important to remember detail of the code after a long time 
- Yes, not only for others. But sometimes I don't even remember how I did a particular part of the code few months ago ! +2
- Yes! Communication, further developments by others
- Yes, if the purpose of coding is to share it is absolutely important, sharing can be also with your future self
- Yes, it forces you to clearly state your code so that it is still understandable after a few weeks.
- yes, especially for myself.
- yes, it can help reflect over architecture and use cases.
- Overview of the code from the high to the low level.
- It also helps you to structure your code more logically.
How would you describe documentation?

- Dalton
    - Not so clear where to search for information
    - best for sharing with people, who do not have to work on the code themselves
    - the long PDF (Dalton) seems useful for reading background and figuring out the capabilities of the package (less so for problem solving)
- Cubicle
    - Definitely needs documentation. Makes it way more efficient for people to grasph what the code is doing.
    - it actually has documentation as docstrings with usage info.
- Numgrid
    - Good mix between completeness and user-friendliness, still keeping the doc simple

- MNE-Python
    - Seems like you need a specific team only for writing the documentation ;)
    - Swanky!
#### What do you need from documentation?
https://coderefinery.github.io/documentation/01-wishlist/#documentation-comes-in-different-forms---what-is-documentation

- Documentation requries deep understanding of what the code is performing 
- A time-consuming gift for my future self. +6
- Instruction on how to reproduce the results
- An overall view of what the code is doing, along with small comments about how each piece of it is working
- Not having a heart attack when I need to run simulations with a code of 6 months to X years old.
- Instructions on how to at least re-produce results, and of course as instructions on how other can use it as well. 
- A manual, both for users and developers.
- Something which is generally conceived to be easy to do. Though people generally forget it, or make a poor documentation (hard to interpret for others and even the writer itself).
- a journal of projects
- fast and intuitive overview if what I visit is what I am searching for.
- confirmation that documentation, examples and code are in sync with each other (successfully version controlled)
- testiment of quality of code / project / community work


How can you motivate your collegues to contribute to the documentation?

- Cookies!
  - nice! great idea +1
- Involving them in the research
- Make it easy for them to get started adding things to the documentation
- It is important for people to understand the structure of your software and how it functions
- It will improve your output, as it will be easier for everyone to use.
- I don't review code unless it contains documentation

- Make it part of the deliverables. No work-around it

- Ask them nicely.

- ask them to use your code without documentation ! +1


- Ask them to interpret a code they have written 5 years ago that is not documented



- How much time to the Code Refinery members spend on documentation and testing in comparison to actually writing the code?
  - about 20% of the time
  - I think looking over the entire lifetime of a project, my feeling is I spent more time documenting, testing, and debugging than actually writing new lines of code. Somewhere I read that good progress should be counted by number of lines removed rather than number of lines added.
      - Do you think 50% is more realistic?

- The documentation of all LaTeX usepackages is in PDF. It can work. 
  - But it can be painful to copy-paste from


### Questions

- What do you mean by docstring?
  - In Python one can have this: (like here: https://github.com/sphinx-doc/sphinx/blob/3.x/sphinx/transforms/references.py#L50) from which documentation can be autogenerated from

- Is README file automatically rendered in Github/Gitlab? or we need to do something after making the document?
  - README.md (markdown syntax) or README.rst (ReST syntax) are rendered bu GitHub/GitLab

- Why Sphinx and not, say, Doxygen?
  - Doxygen works just as well

- This may be a rethorical question, but, at what stage of the developement should you start wrtiting documentation?
  - I recommend to write it with the code, as soon as the code grows out of just a single screen and is not trivially understood. Also once you give the code to somebody else. This is even more important if you work on it only every couple of weeks, to not forget everything until the next time.
  - My opinion: I prefer to write comments first (including documentation within the code) and then insert the code in between the comments.

- If I have both a documentation and a README, whcih essential info should I put in the README?
  - Where to find the longer documentation, license, how to cite? build/test status (if automated testing)
  - How to install.


- What do I say to someone who claims their code is self-documenting?
    - Code can say what it does, but not why.
    - How does someone know where to get started?  There are different types of docs for different purposes
    - Not all users want to or even can read the sources. So self-documenting code is not enough for those who get the binary or library or pip-install it and never look into the code.

- (from chat) Not a programmer at all, but I wonder...How do you integrate this into your workflows? While you are writing code you use Git for versioning when do you start with this other tool? Is it possible to integrate this with Git?
  - yes we recommend to put documentation sources (like in this case Sphinx/RST, but can me markdown) into the same Git repo as the code/scripts, then the documentation goes with the code history: we can branch it, we can also go back to a past state and recreate documentation from it. We will later see how to set up documentation so that it refreshes upon each commit/push.
  - if you are feeling fancy you can configure GitHub to automatically run sphinx on your documentation every time you commit something to the repo. We will show you how this works with "Read the Docs".
  - "Automated testing" lesson (tomorrow) is generated using Sphinx:
    - result: https://coderefinery.github.io/testing/
    - source repo: https://github.com/coderefinery/testing/
  - Another suggestion to incorporate it in your workflow when there are multiple developers: you require that any new code is documented before it is accepted/merged (for example in the code review stage).





### Exercise: generate the basic documentation template

Link: https://coderefinery.github.io/documentation/04-sphinx/#exercise-1-generate-the-basic-documentation-template
10 minutes, until xx:35

- What does this line mean in the exercise? "the first line of the content must be indented to the same level as the options (i.e., :maxdepth)."
    - it means to indent "feature-a" (or the corresponding file name) by 3 spaces, so that it is aligned with `:maxdepth`

(moved one question further down)



# Breakout room comments:

- Room 18: need more time. Facing an issue with sphinx on MacOS. Need someone to look over.
    - If the "python" command is not coming from the conda installation, you can eventually type the full path as full anaconda path/bin/python ([name=staff])
- ```$ python -c "import sphinx; print(sphinx.__version__)"
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'sphinx'
(base) saey0002@slumc0313 ~ $ python -c "import sphinx_rtd_theme"
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'sphinx_rtd_theme'```
  - Assuming you use Anaconda: `conda install sphinx_rtd_theme`
  - Assuming you don't (virtual env?): `pip install sphinx_rtd_theme`

- Unsure whether this is a problem/question? ```$ sphinx-quickstart --version
sphinx-quickstart 3.1.2```

This was shared to convey that the command to verify sphinx installation works but not the verifcation check commands. We thought it would be helpful for debugging.

- Room 5: done with ex 2
- Room 11: half of the people are finshed
- Room 16: ex 2 done
- Room 14: done
- Room 7: ex 1 & 2 done
- Room 1: done
- Room 18: can anyone help me figure out why Sphinx isn't showing up for me when it says it's installed?  - macOS+conda activation
------

### Break
:::danger
We are on a break until xx:03.  Don't forget to walk around some!
:::


### Exercise: Deploying Sphinx documentation to Read the Docs
https://coderefinery.github.io/documentation/05-rtd/
Ends at xx:24

- In Sphinx: What is a pickling environment? 'pickling environment... done'
    - It's bundling up all of the code, packages and everything into a single binary file. I'm not sure why Sphinx is doing this though.
    - TIL! Although I have built Sphinx docs thousands of times, I have never noticed this :-)
        - What means TIL? "today I learned"
    - It is using that to cache some of what it reads, so that future builds can be faster

- From the lesson: "It is no problem to serve using your own URL http://myproject.org instead of http://myproject.readthedocs.io"   - how?
  - If you have a custom domain, you can do this: https://docs.readthedocs.io/en/stable/custom_domains.html#custom-domain-support

- room 16: read the docs login is reluctant to let new users in. Signup with github not working for us. Neither does registering a new account
  - in this case perhaps one person who has an account already, can screenshare and demonstrate it? 

- Room 18: Need bit more time. Facing problems in Step 2: Import a project to Read the Docs by connecting to GitHub due to an already existing project with the same name. Unsure how to remove the existing entry and import a new project
    - can you adjust the name it imports as?
    - If there was more time, you can connect it via a different name, too - I've done it.
    - Yes, we are trying that option.
    - Works now!
    - Were able to host the documentation but could not cover the github push integration part

- Room 12: needs a bit more time, also signup issues with read the docs

- How are the step 1 and step 2 of the exercise related? The step 1 is on my local computer and step 2 is on the remote server.
  - right we did step 1 so that we are able to start a sphinx project, but also so that we are able to preview it locally on the computer (can be useful to check how things look before pushing changes). Step 2 is to let Read the Docs (RTD) do "step 1" for us every time we push changes. In this case RTD runs `sphinx-build` and generates HTML every time we `git push`: very convenient.

- Room 16 has a problem with Authentication of Read the docs on Github. The problem was Chrome browser. Worked with Firefox.

- I'm guessing that Read the Docs needs your github repositorty to be public. What if I want to first work on it for a long time in private mode and then go live at some point and make the docs in advance?
  - right. in this case you can still use sphinx to build locally, you can also make `sphinx-build` part of  CI (continuous integration, more about it tomorrow) to generate pages and deploy them to a web server only visible to your group
  - Using GitLab pages on a private repository will make it possible to deploy a private documentation (only visible to whoever has access to the repository). Probably works in GitHub pages as well(?). There are also external services, e.g. netlify.com.
- ReadTheDocs only allows public documentation (unless upgrading to a paid plan). Do you have suggestions for other hosting services that can be used with private access, for example before the code/documentation is ready for going public?
    - see also above question/answer
    - At that point, I would think about making a private web server, you can build the HTML files and host it there without too much difficulty.  Then you have full control.
      - Right, I guess another option is to use a private GitHub/GitLab-pages.


- room 8: all done
- Room 14: We hosted the repo on `Read the docs` but did not get around to applying changes to see the integration.
  - sorry for short time but it would have probably worked. once you connect these, the documentation refreshes upon each git push.:+1:

- Can I write doc strings into Python functions and get the function name and the description (input, output, function description) to Sphinx to get an overview of my functions and their functionality?
  - yes (can somebody link to a good resouce on how?), basically all Python documentation we see on the web is generated this way
  - You're looking for the "autodoc" and "autosummary" plugin for Sphinx:
      - https://www.sphinx-doc.org/en/master/usage/extensions/autodoc.html
      - https://www.sphinx-doc.org/en/master/usage/extensions/autosummary.html
        - Thank you so much! I think this can help me to become better in documentation and keep the overview about existing functions. I lost it, also not looking daily on my code. :-)

- I am curious about how to write documentation using the  GitHub pages (seems suitable for "small" academic coding projects, rather than large open-source packages). 
  - https://pages.github.com/ it is really neat to build a digital CV as well
  - it's a good option if you don't need to serve several versions at the same time, most of our CodeRefinery content (this lesson, also coderefinery.org) is done using GitHub Pages

- Is Read the Docs (RTD) a remote compiler of sphinx? or it is more than that?
  - yes, it's basically a server that clones your repo, runs sphinx-build, and hosts the generated HTML 

- What is the function of this conf.py file? 
  - in there we configure the name and version of the documentation, there you can load plugins, change the theme and looks
  - read about all settings here: https://www.sphinx-doc.org/en/master/usage/configuration.html

- What is the difference between Read the docs and Github Pages?
  - github pages serves HTML, in practice often HTML generated from markdown using Jekyll but you could serve sphinx-generated documentation also on GH pages (we do this here: https://coderefinery.github.io/testing/)
  - Read the Docs generates sphinx documentation from a Git repository, generates HTML and serves the HTML
  - The real difference is that RTD is designed to be able to serve multiple versions at the same time

- Read the docs and the website cannot handle underscores in the name. They are converted into hyphens. I had the problem at least.
  - thanks, adding this here:  https://github.com/coderefinery/documentation/issues/152



### Github pages
https://coderefinery.github.io/documentation/06-gh-pages/

### Pause
:::danger
Break until xx:34 (we will have a proper break at the usual time)
:::

## Jupyter and Jupyter Lab

- I am very curious to know how to use Git for Jupyter notebook. I tried once and it did not work well/easily. Do you have any tips?
  - We somewhere mention two nice extensions (Git and GitHub) for JupyterLab.
  - Also we will comment on https://nbdime.readthedocs.io/ which is useful to diff ("di") and merge ("me") notebooks.

- So far I have done virtually all my coding in Jupyter notebook/lab. I installed Atom for the first week of this course, it seems nice but also definitely a transition. Is it worth switching?
  - I think Atom (or similar editors) can be good for larger projects which may not be "linear" and may not really fit into a notebook. We will discuss cases which fit better into "files" instead of a notebook.
      - Great, looking forward to that.
      - A nice IDE that acts as an editor, but is also able to work with jupyter notebooks, is VS Code.

- Everytime that a cell runs in Jupyter, the notebook file changes. How is it possible to keep track of a notebook file in Git without need to commit every single change (caused by running a cell)?
  - Personally I run all cells from time to time (to make sure I did not create some inconsistency by running them out of order) and commit every time I improved the notebook. See also above: we will mention Git and GitHub plugins for JupyterLab which make this easier without leaving the notebook. 
      - Thanks I would really like to hear your recommendation regarding GitHub plugins for Jupyter Lab notebooks ! :+1: 

- How are the jupyter lab and jupyter notebook different from each other? +1
  - Traditionally there were only notebooks, the "Lab" is newer which makes it easier to navigate between notebooks, offers a terminal, and better plugin management.
  - In practice you can run notebooks in either of them. If you are new to notebooks, probably better to start with the "Lab" which offers more.
 
- Do you have any thoughts/recommendations on when to use a dedicated GUI above a jupyter notebook for ease of interaction?
  - By GUI you mean an editor such as Atom or VS code or Spyder or similar?
  - No, I mean a coded user interface. I can for example use python to code a user interface to access the underlying code base
    - Ah! This is really personal preference but personally I like when a user interface is a website so that it works on any operating system. So personally I am not a fan of GUIs where I need to install things and which only works on Linux or macOS. So I would personally prefer a JavaScript or a notebook-based GUI or something like R Shiny or D3.js.

- When and in what kinds of projects you recommend to use Jupyter lab environment over a proper IDE?
  - We will comment on that but I like Jupyter for "linear" workflows (such as: read data, filter data, compute statistics, plot ther result). Then it's excellent since I can then easily share this with others using mybinder.org. For "non-linear" problems, where I want several files and it does not really fit into "run one cell after another", I prefer an IDE and a project with several files.

- How did we get the heading there, I missed that?
  - declare a cell as markdown cell and then `# this will be a heading` (the "#" makes it a heading)

- Throughout this workshop you repeatedly refer to markdown. Is it a scripting language with the same syntax in all environments (README, Jupyter, ...)? 
  - yes, it became somehow standard, note that we are writing markdown right now. another common standard is reStructured Text (which we have seen in the last lesson). Many tools understand and render markdown. Another reason it's so popular is that it is "lightweight" and readable also in the terminal, not too many backslashes and parentheses (like LaTeX). Some people write books in markdown.

- I don't see the cell numbers in jupyter, how do I show them?
    - they start empty. After a creation of a cell it will remember the sequence in which cells were created/executed

- I double-clicked on a markdown cell which seems to get back to edit it, but how does it go back to "display" the stuff?
    - with "escape" you can jump out again. to display it, "run" the cell.
    - see the [shortcuts here](https://coderefinery.github.io/jupyter/02-interface/#keyboard-shortcuts)

- Is it really required to use %matplotlib notebook ? I remember that plots can be shown inline. Or for what is this command for, please?
  - I only know `%matplotlib inline` to instruct the notebook to display figures as part of the notebook.
  - `%matplotlib notebook` makes interactive figures. This lets you e.g. zoom in as if it is a pop-up figure.
    - AHA! nice.
    - Thank you

- how do I re-run everything without going one by one?
    - There is a "Restart and run all" option in one of the menus.
    - Good practice to do this before committing and before sharing the notebook with others. Because running all cells is the first thing they will do, to make sure we get the same result.

- How to strip output when commiting to git?
    - There is a tool called `nbstripout` which can be used as a git hook, to remove all the output from git.  It's designed for this

- is it possible to convert the code into pure python and run outside jupyter?
  - yes it is possible: "download as" or "export notebook as"

- ```
  File "<ipython-input-12-67f16f572576>", line 1
  - square area: $s = (2 r)^2$
             ^
  SyntaxError: invalid syntax
  ```
  - It probably needs to be turned into a markdown cell
      - yup, thanks!

- I guess we can also
    - that's the spirit! :D
    - always finish what you have

- Does anyone experienced that jupyterlab is running very slow and making the PC slow too, like if one is running heavy code on it. It is like jupyterlab is running something in the background. It should be some setting. I am running it on firefox
    - JupyterLab is basically a wrapper to Python, so it shouldn't use much more resources than the code itself, if it was running without Jupyter
    - but, there are some cases it could: displying too much in the browser, certain things like variable inspectors.  It could use some more debugging.

- There are also other notebook formats, too, which aren't JSON so can be version controlled better.
  - Examples:
    - https://rmarkdown.rstudio.com/
    - Pluto (julia)

### Break 
:::danger
Break until xx:11
:::


### More Jupyter: sharing notebooks

- what is the usual sharing workflow with jupyter? Sharing the .ipynb? Does it create a web link that I can share? Where is it stored?
  - what many people do is to put .ipynb on github and share link to it via mybinder.org which serves it dynamically (we will hopefully show how to)

- I think I have installed the extensions in jupyterhub, but I don't see the git symbol on the left side.
  - maybe you need to close and reopen the jupyterlab?
      - Unfortunately, this did not help.
  - there are similarly named plugins. Are you sure you got [the right one](https://coderefinery.github.io/installation/jupyter/#github-extension)?
  - It can be tricky, there is both a backend server extension and JupyterLab extension.  Both are needed, and it is confusing!
        - I think I have @jupyterlab/github, @jupyterlab/git, nbdime-jupyterlab under installed. I check your link now.
    - The documentation on the jupyterlab-git repo (https://github.com/jupyterlab/jupyterlab-git) mentions the terminal command 'jupyter lab build' under the installation steps.
        - does running the command and restarting jupyterlab solve your issue with it?
        - No, sorry, jupyter lab build did not change anything. I don't see the git symbol and everybody in room 18 seems to have the problem. But we don't worry now, we try the exercises.

- What is the point of github extension in Jupyter environment? We did everything manually ... 
    - In exercises you can experiment with more ways of doing things
    - We learned git manually to know/understand what is going on under the hood. Some people (like me) will still prefer to do this from the terminal but with the extensions you can do all that directly out of Jupyter, without switching to a terminal. If we had started with extensions directly, it would maybe be a bit too "magic"/intransparent. 


### Exercises
https://coderefinery.github.io/jupyter/05-exercises/
Ends at xx:45
Choose a few interesting exercises from this page: it's free-form, choose your own adventure

If you get problems with widgets or extensions, you can try to solve but we recommend you try something else, and we can check it out later.
- I indeed have them. From the installation instructions session it turned out that conda does not have any problem with the JupyterLab extensions. However I am not using conda...
    - Is there any workaround for non-conda users?
- For me the widgets appear under installed, but not in the left line. Redone the installations given by CodeRefinery, but nothing changed.
    - can you describe your setup (operating system, conda version)
        - MacOS Mojave 10.14.6, conda 4.9.1
            - a quick glance online suggests removing jupyterlab/settings/build_config.json 
            - Could you explain how to do it, please?
                - which jupyterlab should return the path of jupypterlab
                - whic jupyterlab did not return any output. Jumps to the next line.
                

- 2: We can import `interact` and `interact?` prints out the help, so it's available, but running the examples and the solution it doesn't seem to do anything?
  - hmm .... does it need a restart after installing the plugin?  
      - Installed the plugin earlier, only started jupyterlab now. Do we need %matplotlib inline  ?
        - for showing matplotlib figures as part of the notebook: yes
  
  - we will also later show how to deploy the notebook to binder where it will work out of the box so this can also be postponed

- 9: we also have problems with interact not showing a slider' in one case we cannot see the git options in Jupyterlab
    - I would not worry about it and work on something else, extensions are difficult

- Is there any best practice on how to divide code in cells? 
    - I think "what do I need to run separately?"  "What takes a while and should only be done once?"  "What will always be togetehr?"  I don't have any general rules...
    - A good size could be: "I might want to be able to copy-paste this cell into this other project of mine"

- When I run @interact the figure is still static. What could be the possible reasons?
  - It seems many people had this problem. We will hopefully comment on this in the main room.
  - I had this problem also, and this worked for me: `jupyter labextension install @jupyter-widgets/jupyterlab-manager` and then restarting jupyter

- Room 7: We tried the first exercise about widgets but run into widget problem (slider not appearing). So we moved to code profiling exercise. (Juho)
  - we will stay after the lesson to help out debugging this

- Could you after the course show how to tackle the extension problem? I don't have anybody who can help me really with this. Thank you.
  - yes we will stay after the lesson to help out debugging this :+1:


### Binder and notebooks
https://coderefinery.github.io/jupyter/06-sharing/

- Is there a way to get a list of in which order code was run in a notebook afterwards? 
    - left of the cells is the ascending run order of all cells. 
        - But if I see 1, 2, 4 only, can I figure out which was 3?
            - one of them will have been 3, but it can be off screen if you have many cells, or 4 was run twice.
            - or 3 was deleted after running the cells
            - or if some cell has been re-run many times, can I then see what happened
                - try it. it should create a growing gap to the previous one.
                - It does, but if I see for instance 4, 5, 6, I don't know if the first one was run 4 times, or all of those twice?
                    - I guess that is one of the limitations

- Do you have a recommendation regarding version control with the PyCharm IDE? Should I add an extension? Thanks 
  - it's been a while I looked at that one but I thought it supported Git out of the box. At the minimum there was a plugin but I have seen colleagues staging and committing directly from PyCharm.

- How to include any data needed by the notebook when putting it on mybinder? 
  - either as part of the repository or you can download the data as part of the notebook, example: pandas.read_csv can download csv from a URL
  - 

- Can jupyter notebooks deal with input arguments? For example, path to a data set, but then I want to re-execute this notebook with a different data set?
  - interesting question. I am thinking about how I would do that ...
  - basically: no, not by default.  Different There are different things yo ucan find, that let you run a notebook on different arguments (see references at the bottom link below)
  - This is what I am working on: https://github.com/NordicHPC/nbscript
  - the way I would solve it: one notebook for each but to avoid duplication, I would import the common stuff from a library into all the notebooks
            - Make the code itself into a module, right?
                 - yes

- I'd like to use Jupyter with a project I'm working on to do a bit of visualization. I have a bunch of code, and then some files where I call all my code to show some (example) output, which would work nicely in jupyter. How would I put all of that on github? Because I think now we created a whole new repository for the jupyter thing. How do I combine everything?
  - if most of the code (and data?) already is in some git repository, you can add a notebook to the existing one, maybe into a subfolder. then I would also create a Binder link to the subfolder with the notebook(s).
        - Thanks, I'll be trying that.
          - the nice thing is that if it's in the same repository, you can import functionality from the rest of the code into your notebook without making it a proper PyPI library.

### Final discussion
https://coderefinery.github.io/jupyter/06-sharing/#final-discussion

Already using Jupyter?  What for?
- Yes, I started there with the coding. Linear workflow, import data, modify it, extract values, plot, save the data. 
- Mainly to visualize data. Source code I write in a separate python file. In jupyter I import the python file and use specific functions used to visualize data analyzed through the python file.
- Yes I use Jupyter Lab a lot for my PhD work (focus on data science and machine learning). Jupyter made it easy to start coding in Python 3 (rather than Matlab). I am now switching to PyCharm. 

Are you new to Jupyter - what possible use cases do you see?
- I am not so new to them, but they can act like interactive cooking instructions.
- .
- .

Do you think they can help with reproducibility?
- I think they can be a valid addition/alternative to benchmark cases of some modules, especially beacuse they include nice markdown explanation and pictures all in one place. Sure, they shouldn't be too long, should be working at first run and should come with a requirements.txt.
- Jupyter notebooks are great for sharing results (visualizing results and sharing workflows in the form of tutorials)
- .
- Maybe difficult, because what do I do with multiple data sets. Can I hand over arguments to notebooks?



## Feedback, day 5

- Today was very useful. Good tools to document code; like sphinx and readthedocs. Also jupyter is very useful. Well presented by [name=staff]. +1
- I really enjoyed today: I liked the tips and tricks for Jupyter notebbooks and I did not know about Sphinx for writting proper documentation
- Please let us know who we should acknowedge (Nordic e-Infrastructure Collaboration, TUD graduate school and anyone else?) if we want to share info about the code refinery workshop on Linkedin/Twitter. Thanks :)
  - CodeRefinery, https://coderefinery.org (and if a long description,
    it's a funded project by the Nordic e-infrastructure collaboration)
- Very nice session. I only have thumbs up for today. +1
- Wonderful session! The Q&A in HackMD is super useful! +1
- Great day, good pacing. We discovered plenty of dependency issues with jupyterlab though, from our OS (Ubuntu 18.04) not providing a late enough version of nodejs (such that we could not access the extension manager), to not being able to use the `@interact` decorator in Jupyter. Otherwise, very nice hands-on exercises and HackMD Q/A sessions.

---
*Always ask questions at the very bottom of this document, right above this. Switch to view mode if you are only watching.*

*We are monitoring this hackMD, but we will reply every now and then so that you can focus on the speaker.*
rr
