# d2mr-assessment

This is a centralized directory for D2MR mini-project assessment materials. The purpose of this repository is to provide a single location for all mini-projects, which will allow you to easily access and complete them and your instructors to efficiently grade them.

Working with this repository will help you practice using git and GitHub, which are explicit learning objectives for the course!

Dr. Dowling owns the main repository, and you will create a fork of this repository to complete your mini-projects. This will create a copy of the repository in your GitHub account that you control and can modify without affecting the main repository or being visible to other students.

# Using this repo and completing assessments {#using-repo}
 
## Setup instructions {#setup}

1. Create a fork of this repository. 
    1. Click the "Fork" button in the top right corner of this page (assuming you are viewing this on GitHub)
    2. Rename the fork by appending your CNetID: `d2mr-assessment-yourcnetid` (e.g. `d2mr-assessment-ndowling`). 
    3. Add Dr. Dowling and your section TA as collaborators to your forked repository.
2. Create an R project in RStudio and clone your forked repository to your local machine. The course website has a full guide on how to do this, but the basic steps are:
    1. In RStudio, go to File -> New Project -> Version Control -> Git
    2. Enter the URL of your forked repository (e.g. `https://github.com/nrdowling/d2mr-assessment-ndowling.git`) and click "Create Project"
    3. Because you are using a forked repository, you can pull from both your remote version of the fork or from the main "upstream" repository, but then push only to your fork, confident that you're leaving the main (public) repository untouched.
3. Periodically -- at minimum before you begin a new project -- pull changes from the main repository to your forked repository to ensure you have the most up-to-date version of the assessment materials. There are [instructions for doing this in RStudio below](#pullupstream) (it's not quite as simple as syncing with your own fork or repos).

## Completing mini-projects {#completing-projects}

Mini-projects on the menu have a corresponding directory in this repository. Each directory contains (or will contain) either a README.md file with general instructions for approaching the project *or* a Quarto notebook (e.g., cleaning-level-1.qmd) that will guide you through completing the more structured projects.

Before submitting, you'll need to add a copy of the assessment.md file (found here in this top-level directory) to the project directory and complete it. This file will be used to assess your work.

### Project types

Mini-projects will mostly fall into one of the following categories: guided exercises, open-ended projects, or off-the-menu projects. The [menu overview](#menu-overview) below discusses these in more detail, but here's a quick summary of the mechanics for completing and submitting them:

### Guided exercises

These projects will have a Quarto notebook that will guide you through the project, like leveled data cleaning exercises. The notebook will include instructions, code snippets, and explanations to help you complete the project. Unless otherwise stated, all aspects of the project should complete these projects in the Quarto notebook.

### Open-ended projects

These projects will have a README.md file that will provide a general description of the project and some guidance on how to approach it. If it's sensible to do so, you can put your work in that same directory, in whatever form it takes.

In some cases it's won't make sense (or even be possible) to complete the project in the directory of your centralized assessment repo. For example, mini-projects that require some kind of "publication" (like a website or Quarto APA manuscript) will need to exist in their own dedicated repositories; they can't run as sub-directories of this one. 

In those cases, you should still add and complete an assessment.md file in the associated project directory (here in this centralized repo, not the one you made for the project), which will include any necessary information about how to access your work. 

### Off-the-menu projects {#otm-projects}

You can also design your own "off-the-menu" projects. To do so, create a new directory in the repository, name it appropriately, and add a copy of the otm-proposal.md file from this directory. Instructions for completing and submitting the proposal via Canvas are included in that document. 

Once approved, you can start working on the project. When you submit your finished project, you'll follow the same process as the on-the-menu projects, but you'll be resubmitting to the same assignment on Canvas that you submitted your proposal to.

## Submitting mini-projects {#submitting}

When you finish a mini-project, you should complete the assessment.md file in the project directory, then submit a link to that directory on Canvas.

**No matter what kind of project it is (structured, open-ended, or off-the-menu), the project needs a directory here in this repo, and that directory needs to include a completed assessment.md file.**

Submit to one of your 10 mini-project assignments on Canvas (whichever the next open one is, doesn't matter as long as it's not one you've already used). The Canvas assignment is simply a text box where you should include:

1. The name of the project and/or a brief description of the project
2. A link to the directory *in this centralized repository* where you completed the project
    1. If you completed the project in a separate repository, your assessment.md file should explain how to access your work.
3. Any additional info you'd like your grader to know

Submitting to Canvas functionally serves to alert us that you've completed a project and that we should grade it. The actual assessment, including any feedback, happens in the assessment file in this repository. Your Canvas assignment will be marked as "complete" when we've finished grading your project and have pushed the assessment back to your repo. Points earned will be added to your cumulative mini-project scores in Canvas (you won't see numbers for each project, just complete/incomplete).


### Pulling from the main (upstream) repository {#pullupstream}

You should periodically pull changes from the main repository to your forked repository to ensure you have the most up-to-date version of the assessment materials. Unfortunately RStudio doesn't have a nice easy button to click for this, so you'll need to do it from the terminal pane in RStudio.

Before the first time you pull from main, you need to tell git where the main repository is. You only need to do this once. In the terminal pane in RStudio, run the following command:

```bash
git remote add upstream https://github.com/nrdowling/d2mr-assessment.git
```

Now you can pull changes from the main repository by running the following command (in the terminal):

```bash
git pull upstream main
```

You may get the following message:

```
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint: 
hint:   git config pull.rebase false  # merge
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint: 
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
```

If you get this message and you understand all those options, you can make up your mind about what to do next. If this is jibberish to you, just run the following command:

```bash
git config pull.rebase false
```

Now try the `git pull upstream main` again. This time it should work, but you'll get pulled into a text editor to write a commit message. You have 2 options:

1. Just close the text editor (it's probably vim) by typing `:q` and hitting enter. This is quick and dirty and not ideal, but since you know you'll never need to merge your fork back to main, it's fine in this context.
2. Write a commit message. This is the "right" way to do it, but it's a bit more complicated. If you try to just start typing, you won't see anything happen. That's because you're in "command mode" in vim. If you want to do this:
    1. Hit 'i' to enter 'i'nsert mode.
    2. Type your commit message.
    3. Hit `esc` to exit insert mode.
    4. Type `:wq` and hit enter to save and close the text editor.

Granted, both these assume your machine is using vim (or similar) as a text editor. If that doesn't work, your machine is probably using something other than vim. On PCs it's probably nano. You can try `ctrl+x` to exit, and then `y` to save changes and `enter` to confirm. Still not working? Bust out your troubleshooting workflow. Google is your friend.

Have you hit an impassable wall with pulling from the upstream repo? It's ok. This isn't a major learning objective for the class. You can also do this outside of RStudio with apps designed for git, like GitHub Desktop. I'll leave it to you to figure out how to do that.

# Menu overview {#menu-overview}

Earn up to 40 points across all mini-projects for meeting course objectives. Some of the menu items are highly structured (like the data cleaning and wrangling), but most are very open to interpretation. Unless the mini-project has a link to a specific assignment, you should just work with the short description provided here and take it in whatever direction you like.

**These projects do not have strict submission or grading requirements.** You can make any mini-project as simple or as complex as you like. If you write a `hello_world()` function that's 5 lines long, that's fine, but you'll probably only be able to demonstrate a couple of the learning objectives. If you write a `hello_world()` function that's 50 lines long, or write multiple functions and build them into your own package, you'll probably be able to demonstrate a whole lot more than that.

Earn up to 10 points across all mini-projects for assignment engagement. That 5-line `hello_world()` function might not earn any engagement points, while the 50-line one could earn you all 10.

This goes for the structured guided exercises as well. The Level 1 exercises are designed to be relatively simple and straightforward, while the Level 2 exercises are more complex and open-ended, but you can complicate a Level 1 and simplify a Level 2 as much as you like. You're assessed on demonstrating the objectives and engagement, not on following the directions of the exercise to the letter.

Some projects are marked as "off the syllabus" (OtS). These are opportunities to learn and demonstrate skills that aren't explicitly covered in the course. These will let you showcase the skills we do explicitly cover in a different context, or let you explore something that interests you.

You are welcome to go "off the menu" (OtM) to design your own mini-project that lets you focus on your interests while still demonstrating the course objectives. If you choose to do this, you should submit a proposal for approval using the otm-proposal.md file in this directory. Instructions for completing and submitting the proposal are in the same document.

Tags:

1. GE: This is a semi-structured guided exercise with a .qmd notebook to guide you through the project. These typically have both a "Level 1" and "Level 2" version, with the latter being more complex and offering less guidance.
2. DEMO: This is not a mini-project, but a demonstration of the skills you'll need to complete the related mini-project. There is nothing to complete, and you should not submit these for grading.
3. OtS: This project is "off-the-syllabus" because it involves skills beyond the learning objectives of the class.

### Mini-project menu {#project-menu}

This is the structure of this repository. Second-level directories group projects by the category of skills they assess (mosty; expect a LOT of overlap!). Third-level directories are individual projects.

Materials for mini-projects (either a simple readme with general instructions or guided content with a .qmd) will be added to their respective subdirectories as we progress through the quarter, but you may complete projects before the materials are added. 

Projects may be added or revised throughout the quarter, so be sure to keep you fork up-to-date with the main repository.

1.  Data cleaning
    - (GE, DEMO) Walkthrough
    1. (GE) Level 1
    2. (GE) Level 2
    3. (Pairs/groups) Un-clean some data & swap to clean
2. Data wrangling
    - (GE, DEMO) Walkthrough
    1. (GE) Level 1
    2. (GE) Level 2
    3. (Pairs/groups) Ravage some poor datasets & swap to wrangle
    4. (OtS) Access, read in, and wrangle nested or non-tabular data (e.g., JSON, XML)
3.  Data visualization & presentation
    - (GE, DEMO) Walkthrough
    1. (GE) Level 1
    2. (GE) Level 2
    3. Create a custom ggplot2 theme
    4. (Pairs/groups) Make plots (w/ some minimum requirements) & swap to recreate
    5. Create beautiful tables with packages like `kableExtra`, `flextable`, `stargazer` , `gt`, or `xtable` ([there are lots!](https://towardsdatascience.com/top-7-packages-for-making-beautiful-tables-in-r-7683d054e541))
    6. Present the same data in multiple ways (e.g., bar chart, line chart, table)
    7. (OtS) Create a plot with non-ggplot2 packages
4. Data analysis
    1. (GE) Descriptive statistics
    2. (GE) Hypothesis testing
    3. (OtS) Higher-level statistics
5. Data communication
    1. Transpose a paper into Quarto markdown
    2. Write a memo or brief report based on a previous assignment
    3. Create a demo .qmd or .Rmd for one or more class topics
    4. (OtS) Recreate your Quarto report with papaja or RMarkdown
    5. (OtS) Use Quarto to publish something other than a document (e.g., website, presentation, dashboard)
    6. (OtS) Create a `shiny` app or dashboard
6.  R Programming
    - (DEMO) `hello_world()` examples
    1. Create a `hello_world()` function
    2. Create a plotting function
    3. Create a wrangling function
    4. Recreate a function from base R or a non-tidyverse package using tidyverse functions
    5. (OtS) Create a package
7. Git & GitHub (these can use real projects or dummy data)
    1. Set up a skeleton repo to create APA quarto manuscripts
    2. (Groups) create and maintain a repo as collaborators and use cloning, forking, merging etc
    3. (OtS) Create a GitHub pages website
    4. (OtS) Host a package through a GitHub repo
8. Unassessed Learning Objectives & Miscellaneous
    1.  Create and document a style guide and apply it to a script or notebook
    2.  Create a debugging journal
    3.  Write documentation for a function that you’ve written (e.g., a `hello_world()` function or something you use in your independent project), following the standard documentation guidelines and expectations (i.e., it should match what you see when you use `?somefunction` )
    4.  In the format of your choosing (bullet points, paragraphs, mindmap, flowchart, slides, etc.), show me how you understand the points listed under “conceptual skills”.
    5.  Get obsessed with LaTeX!
    6.  Contribute answers to stackoverflow, reddit, etc.
    7.  Create a tutorial on a topic of your choosing in the format of your choosing
    

### FAQ

1. **Can I use the same data from my independent project?**
    - No. You should use different data for each mini-project unless the assignment calls for it or you receive prior approval. You can use the same data for multiple mini-projects, but you should demonstrate different skills in each.
2. **Can I update the top-level assessment.md file?**
    - No(ish). Every mini-project should have its own subdirectory, including its own assessment.md file. Leave the top-level assessment.md file as-is and duplicate it for each mini-project you complete. The "ish" part of the no(ish) is that you can make changes you expect to apply to all your mini-projects (e.g., your name and section number).
3. **What's the difference between "off-the-syllabus" and "off-the-menu"?**
    - "Off-the-syllabus" projects are designed to let you practice skills that aren't explicitly covered in the course but are related to the skills we do cover. You'll be provided with some guidance for approaching the project, but it will be up to you learn the skills independently. These are already part of the menu and don't require a proposal.
    - "Off-the-menu" projects are entirely self-designed and can be about anything you want, as long as will help you meet the goals of the course. You can use them to check off assessed learning objectives, to go above and beyond like an OtS project, do demonstrate unassessed/conceptual skills, or a combination. You'll need to submit a proposal for approval before you can start working on the project.
4. **How are off-the-syllabus/off-the-menu projects assessed?**
    - The same as other projects, using an assessment.md file. If you want, you can earn all 40 points through OtS or OtM projects. They are also a great way to earn the engagement points, as they require you to take a more active role in your learning.
5. **There are no materials in the subdirectory for a project I want to start -- what do I do?**
    - Unless it's a guided exercise, just go for it! Most projects will just have a simple readme with very open-ended instructions anyway. If you start a project and then it turns out the instructions added later were way different than the direction you took it, that's fine. You're functionally doing an off-the-menu project.
6. **Can I do the same mini-project twice? Can I resubmit a mini-project after its graded?**
    - No. You get one shot at each mini-project, but this shouldn't be a limitation. There are 40+ menu items and you can always go off the menu to design a project that will let you demonstrate the same skills in a different context. If you're not sure if your idea is different enough, submit a proposal for approval
7. **Can I work with a partner or group on a mini-project?**
    - Yes! Well, mostly. Some projects are specifically designed for pairs or groups, and they are a great way to demonstrate community engagement on top of project engagement. You can also design OtM group projects.
    - For projects that aren't designed to be completed collaboratively, you should complete the work individually, but you still can (should!) collaborate to support one another. Discuss ideas, help debug, etc. Just make sure you're each doing your own work and demonstrating your own skills in your own assessment.md 
    - In all cases you should each submit your own assessment.md file in the appropriate subdirectory of your own forks and note on it who you worked with. If you have questions about what kinds of collaboration are ok or the logistics of group work, post your questions on Slack or email Dr. Dowling.
8. **Will I screw up the main repository if I do something wrong? Will my classmates see if I am terrible at github**
    - No. You can't make changes to the main repository unless you're a collaborator, and you can't become a collaborator unless you're a TA or Dr. Dowling. If you somehow managed to commit changes to the main repository, you would be prompted to create a "pull request," so you'd know you weren't in the right place. If you managed to accidentally submit a pull request, I would just deny the request and everything would still be fine. 
    - Your classmates won't see your work unless you show it to them. The only way they would see your work is if you made a public repository and shared the link or invited them as collaborators to a private repository. Your professor and section TA need to be collaborators on your forked repository to grade your work, but I promise we aren't digging through your commit files to judge your git prowess. That would be pretty counterproductive for the course goals. We also just don't have the time even if we wanted to.
9. **What does ((some term not on the syllabus)) mean in the names of the projects?**
    - It's probably part of an off-the-syllabus project. If you're curious about things like papaja, shiny, or LaTeX, look them up! If you're not sure whether something is off the syllabus or just something we haven't gotten to yet, ask on Slack.
10. **How many mini-projects must/can I complete?**
    - You can complete a minimum of 1 mini-project and a maximum of 10. Most students will complete 3-5. Points earned are cumulative across all mini-projects, but remember at least 20 points must be earned from meeting unique assessed learning objectives. You can repeat objectives in the remaining 20, but you cannot earn points for the same objective more than once per mini-project.
    
    
    
    