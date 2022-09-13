---
layout: default
title: Code, analysis and computing
rank: 8
---

### Step-by-step instructions to getting started
1. [Download and install Anaconda](https://www.anaconda.com/products/individual)
2. [Download and install git](https://git-scm.com/downloads)
3. [Download and install Spyder](https://www.spyder-ide.org/) from the standalone
    - [Follow this tutorial on scientific data analysis in Spyder](https://docs.spyder-ide.org/current/workshops/scientific-computing.html?highlight=jupyter)
4. [Continue](https://anne-urai.github.io/lab_wiki/IBLdata.html) to setup your environment for analyzing IBL data
    - Make sure to [link Spyder](https://docs.spyder-ide.org/current/workshops/scientific-computing.html?highlight=jupyter#setting-up-the-working-directory) to your `iblenv` conda env: Settings / Python Interpreter / User the following Python interpreter / `anaconda3/envs/iblenvs/bin/python`

# Python and data analysis references
* Know your way around the command line
    * [Basic cheatsheet](https://github.com/moriahtaylor1/teaching-materials/blob/main/infographics/GIT%20GUIDE%20Part%201%20-%20INTRO.png)
* Understand what a virtual environment is
* Understand Git and GitHub
  * [GitLectures](http://git-lectures.github.io)
  * [Git primer by Brad Voytek](https://voyteklab.com/git/git-primer/)
  * [Even better Git intro](link)
  * Further practice: pull this wiki repo, add something in the [Markdown language](https://guides.github.com/features/mastering-markdown/), and submit a pull request (see Home for instructions on how to contribute to the wiki).
* Learn the basics of Python
  * [DataCamp](https://www.datacamp.com/groups/shared_links/bdca0f873fb4e2a3d00f489268470b8eef78a1eafcde11c025950376eed73c9c) has very good adaptive programming courses. Sign up with your _@umail.leidenuniv.nl_ address using the link for free access.
  * [Intro to Python](http://gureckislab.org/courses/fall20/labincp/chapters/03/00-python.html) & [lab in cognition & perception](http://gureckislab.org/courses/fall19/labincp/intro.html), both by Todd Gureckis.
  * Students at Leiden University can follow the [Introduction to Python course, offered by LIACS](https://stepik.org/course/73333/promo).
   *  You can also access [DataCamp learning resources](https://www.datacamp.com/groups/shared_links/a6bb93f6866b8ced468d96d1406e020a421592ea) with your Leiden Uni account.
* Think about the **structure of data**
    * [The structure of data, by Todd Gureckis](http://gureckislab.org/courses/spring21/labincp/chapters/05/00-data.html)
    * Learn to work with the [pandas](https://pandas.pydata.org/docs/getting_started/intro_tutorials/index.html) and
     [seaborn](https://seaborn.pydata.org/) packages for data handling and visualization.
     * [Pandas tutor](https://pandastutor.com/) with helpful dataviz.
* Once your code runs, make it better! 
    * [The Good Research Code Handbook](https://goodresearch.dev/) is a fantastic guide to write elegant, organized code that doesn't make you want to tear your hair out. Highly recommended. 
    * [Dan Larremore's lab guides to clean code](https://drive.google.com/file/d/1TraVwRkbkCbHq-s_-NS69ZEbRNwH8XNh/view)
    * [Consider code review](https://uwescience.github.io/neuroinformatics/2017/10/08/code-review.html)
    
### Open data, open code, open science
- Might there be a dataset or a tool out there that does what you need? Check out this [list of lists](https://github.com/openlists/).

### Computing resources
For most projects (especially those using behavioral data), your laptop will be more than sufficient to run Python
. If you need more heavy lifting, there are a few options:
- ALICE supercomputer @ Leiden Uni
  - [Get an account](https://wiki.alice.universiteitleiden.nl/index.php?title=ALICE_User_Documentation_Wiki)
- LISA / Cartesius clusters @ SurfSara
  - [Apply through NWO](https://userinfo.surfsara.nl/systems/lisa/account). Very well managed, but since Leiden doesn
  ’t have a contract with SurfSara you have to apply to extend your account every year.