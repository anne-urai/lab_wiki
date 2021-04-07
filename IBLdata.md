---
layout: default
title: Working with IBL data
rank: 5
---
## Working with IBL data

Many projects make use of the large dataset collected by the [International Brain Laboratory](https://www.internationalbrainlab.com/).

#### General info
* [Preprint](https://doi.org/10.1101/2020.01.17.909838) describing the experiments and the data.
* [Video description of the data by Eric deWitt](https://www.youtube.com/watch?v=NofrFH8FRZU), for NeuroMatchAcademy.
* Explore the data through the [interactive DataJoint portal](https://data.internationalbrainlab.org/).

#### Getting started with IBL data
* See [data.internationalbrainlab.org](https://data.internationalbrainlab.org/) for a landing page and overview.
* [Request access credentials](https://datajoint.io/events/nma-ibl-public) to the database.
* Explore the collab notebooks created by DataJoint: [NMA-IBL on GitHub](https://github.com/int-brain-lab/nma-ibl).

#### To set up your local configuration
_This assumes that you've worked through the general Python setup, and that you understand GitHub, conda and some basic command line tools._
1. Create and activate your conda environment (e.g. called `iblenv`)
2. Use `conda install` to install `seaborn` and `statsmodels`. 
    - You can also install the useful pingouin package for basic stats: `conda install -c conda-forge pingouin`.
3. Run `pip install nma-ibl` to get access to the IBL data via DataJoint.
4. Now create a new GitHub repo that will host your analysis files (if you'd rather not share it with the world, set it to private) and clone it to a convenient location on your local machine. Launch Python, either in the Terminal or in your Python IDE.
4. From the [NMA-IBL DataJoint GitHub](https://github.com/int-brain-lab/nma-ibl), launch the first Colab notebook and follow the instructions to enter your newly obtained credentials (but do this locally, rather than inside the Colab). After entering your username and password, check with `dj.conn()` that everything works. Then run `dj.config.save_local()` to create a local config file: you won't have to enter your DataJoint credentials anymore in the future! Note that this local file `dj_local_config.json` will only live inside the current folder, so it won't be recognized if you launch Python from somewhere else.
    * See more [here](https://docs.datajoint.io/python/setup/01-Install-and-Connect.html) and [here](https://int-brain-lab.github.io/iblenv/dj_docs/dj_credentials.html).
    * *Important:* make sure you add `dj_local_conf.json` to the `.gitignore` file in your repo, so that your credentials don't end up on your public-facing repository on GitHub. You can also copy [this .gitignore file](https://github.com/int-brain-lab/paper-behavior/blob/master/.gitignore).

#### Play with the data
Now create a script that will load and save some data. 
Import things
```
# general module import
import pandas as pd
import numpy as np
import os
import seaborn as sns
import matplotlib.pyplot as plt

# datajoint-specific stuff
import datajoint as dj
from nma_ibl import reference, subject, acquisition, behavior, behavior_analyses

```
Then, query some basic information about all sessions that were run.

```
subjects = (subject.Subject * subject.SubjectLab * reference.Lab)
sessions = acquisition.Session * behavior * behavior_analysis * subjects & 'task_protocol LIKE "%training%"' # only take training sessions here

# only save some fields that we really care about for now (otherwise, the dataframe will explode)
sessions = sessions.proj('')

# fetch as DataFrame
df = sessions.fetch(format='frame').sort_values(by=['lab_name', 'user_name', 'subject_nickname']).reset_index()
df # take a look at what we've got
```

Now explore the DataFrame, for instance in 'scientific mode' in PyCharm or simply by printing different parts and groups to your command line.

*Exercise 1*: write some code to save this newly created Pandas DataFrame as a csv file. Make sure to avoid that this (large) datafile gets pushed to GitHub, for instance by creating a `/data` folder that is listed in your `.gitignore`. Then, for any analysis you want to run, load in this local file - you'll now be able to get data without connecting to the DataJoint database. Of course, you may need different datafiles for different purposes (at the level of animals, sessions, or trials).

*Exercise 2*: plot some basic information about all the sessions. When (at what time of day) where they collected? How many sessions were collected per lab, user, and animal? How does performance change as a function of each animal's progression in training?

*Exercise 3*: recreate a figure from [the preprint](https://doi.org/10.1101/2020.01.17.909838), for instance figure 2a. Then compare your solution against the [code here](https://github.com/int-brain-lab/paper-behavior).