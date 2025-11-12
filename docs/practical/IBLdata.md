---
layout: default
title: Working with IBL data
parent: Data analysis
nav_order: 1
---
## Working with IBL data

Many projects make use of the large dataset collected by the [International Brain Laboratory](https://www.internationalbrainlab.com/).

### General info
* [eLife paper](https://elifesciences.org/articles/63711) describing the experiments and the behavioral data.
* [Video description of the data by Eric deWitt](https://www.youtube.com/watch?v=NofrFH8FRZU), for NeuroMatchAcademy.
* Explore the data through the [interactive data explorer](https://viz.internationalbrainlab.org/).

### ToDo: Colab for IBL data analysis without local Python install
See [here](https://medium.com/@nogamudrik_96888/how-to-access-dandis-dandisets-for-your-neural-data-project-64a643760d2b)

## Getting started with IBL behavioral data
* See [data.internationalbrainlab.org]https://data-sciviz.internationalbrainlab.org/sessions) for a landing page and overview.
* [Request access credentials](https://surveys.datajoint.io/nma-ibl-public) to the database.
    * [More docs on IBL-DJ access](https://github.com/int-brain-lab/iblenv/tree/master/docs_gh_pages/dj_docs)
* Explore the collab notebooks created by DataJoint: [NMA-IBL on GitHub](https://github.com/int-brain-lab/nma-ibl).

### To set up your local configuration
_This assumes that you've worked through the general Python setup, and that you understand GitHub, conda and some basic command line tools._
1. Create and activate your conda environment (*important*: use [these instructions](https://github.com/int-brain-lab/iblenv)).
2. Use `conda install` to install `seaborn` and `statsmodels`. 
    - You can also install the useful pingouin package for basic stats: `conda install -c conda-forge pingouin`.
3. Run `pip install nma-ibl` to get access to the IBL data via DataJoint.
4. Now create a new GitHub repo that will host your analysis files (if you'd rather not share it with the world, set it to private) and clone it to a convenient location on your local machine. Launch Python, either in the Terminal or in your Python IDE.
4. From the [NMA-IBL DataJoint GitHub](https://github.com/int-brain-lab/nma-ibl), launch the first Colab notebook and follow the instructions to enter your newly obtained credentials (but do this locally, rather than inside the Colab). After entering your username and password, check with `dj.conn()` that everything works. Then run `dj.config.save_local()` to create a local config file: you won't have to enter your DataJoint credentials anymore in the future! Note that this local file `dj_local_config.json` will only live inside the current folder, so it won't be recognized if you launch Python from somewhere else.
    * See more [here](https://docs.datajoint.io/python/setup/01-Install-and-Connect.html) and [here](https://int-brain-lab.github.io/iblenv/dj_docs/dj_credentials.html).
    * *Important:* make sure you add `dj_local_conf.json` to the `.gitignore` file in your repo, so that your credentials don't end up on your public-facing repository on GitHub. You can also copy [this .gitignore file](https://github.com/int-brain-lab/paper-behavior/blob/master/.gitignore).

### Play with the data
Now create a script that will load and save some data. 

Import things
```python
# datajoint-specific stuff
import datajoint as dj
from nma_ibl import reference, subject, acquisition, behavior, behavior_analyses
```
Then, query some basic information about all sessions that were run.

```python
# which subjects (i.e. mice) are in the database?
subjects = (subject.Subject * subject.SubjectLab * reference.Lab)
# this contains a lot of information that we don't really need 
# (and will increase the size of the data we want to download). 
# so let's get only the columns that we're interested in
subjects = subjects.proj('subject_nickname', 'sex', 'subject_birth_date', 'time_zone')
# note that this is not yet data - it's only a query to the database. fetch will actually get those data
df_subjects = subjects.fetch(format='frame').sort_values(by=['lab_name', 'subject_nickname']).reset_index()

# same for sessions - only take training sessions here
sessions =  behavior.TrialSet * behavior_analyses.PsychResults * behavior_analyses.ReactionTime \
            * behavior_analyses.SessionTrainingStatus \
            * (acquisition.Session & 'task_protocol LIKE "%training%"') * acquisition.SessionUser \
            & subjects # 
# only save some fields that we really care about for now (otherwise, the dataframe will explode)
sessions = sessions.proj('n_trials', 'performance_easy', 'threshold', 'bias', 'lapse_low', 'lapse_high',
                        'training_status', 'user_name', 
                        session_duration='TIMEDIFF(session_end_time,session_start_time)')
df_sessions = sessions.fetch(format='frame').reset_index()
# note: the two dataframes containing subject info and sessions info share 
# the column subject_uuid, which is called the 'primary key' that uniquely 
# identifies each mouse. use pandas' join to combine the two dataframes - 
# but beware the size of the data you're working with.
```

Now explore the DataFrame, for instance in 'scientific mode' in PyCharm or simply by printing different parts and groups to your command line. To better understand what the columns mean, see [this](https://leonh.notion.site/Master-Student-Knowledge-Base-88d54d9ca12a43f9aa01c4a05090e816) and [this list by Leon Hommerich](https://leonh.notion.site/Dataframe-Column-Explanations-13688128673c48559262653bc2ced3fc) as well as the official list of [IBL dataset types](https://docs.google.com/spreadsheets/d/1ieLXRPLLSgUKcLvFkrqizfZl5HjdfE6bQ2KLBCRmjQo/edit#gid=1097679410) (this doesn't match with the DataJoint names one-on-one).

*Exercise 1*: write some code to save this newly created Pandas DataFrame as a csv file. Make sure to avoid that this (large) datafile gets pushed to GitHub, for instance by creating a `/data` folder that is listed in your `.gitignore`. Then, for any analysis you want to run, load in this local file - you'll now be able to get data without connecting to the DataJoint database. Of course, you may need different datafiles for different purposes (at the level of animals, sessions, or trials).

*Exercise 2*: plot some basic information about all the sessions. When (at what time of day) where they collected? How many sessions were collected per lab, user, and animal? How does performance change as a function of each animal's progression in training?

*Exercise 3*: get more detailed info not at the session level (overall accuracy on easy stimuli), but at the individual trial level. You can use `sessions * behavior.TrialSet.Trial` to get this, but be warned that this will become huge/slow quickly. Better to first restrict to a subset of sessions (e.g. from one mouse), or to use `.proj` to select only those attributes of the `TrialSet` that you really need. See [here](https://github.com/int-brain-lab/paper-behavior/blob/master/figure3ab_psychfuncs.py#L41) for an example.

*Exercise 4*: recreate a figure from [the preprint](https://doi.org/10.1101/2020.01.17.909838), for instance figure 2a. Then compare your solution against the [code here](https://github.com/int-brain-lab/paper-behavior).

### Neural data
The IBL's neural recordings will be fully released once completed. Until then, you can find some example data and check out analyses [here](https://int-brain-lab.github.io/iblenv/06_examples.html).


### Neural data
* See [docs.internationalbrainlab.org/](https://int-brain-lab.github.io/iblenv/public_docs/public_introduction.html) for a landing page and overview.
* You can find some example data and check out analyses [here](https://int-brain-lab.github.io/iblenv/notebooks_external/data_release_repro_ephys.html).
* Browse the data in this [interactive visualization app](https://viz.internationalbrainlab.org/app).
- See [here](https://docs.google.com/presentation/d/1hH-iv7721-5mnPSmqlSuZRyMTOVWQizjC0mymWX1z5U/edit#slide=id.g2b37c37de99_0_61) for a tutorial given at COSYNE 2024 (recording [here](https://www.youtube.com/watch?v=NskZZ2dKeP8)).
- See [here](https://www.ucl.ac.uk/neuropixels/training/2024-neuropixels-course) for a online course on Neuropixels (recording [here](https://www.youtube.com/playlist?list=PLfhWmWntvjl7SYCcrM5Qy1RFIiIIO6MK-)).
### Accessing data on ALICE
Email the ALICE helpdesk to get access to the shared data folder: `data_pi-uraiae`. 

Then,

```python

# ===================================
# code to load shared (internal) data
# ===================================

import os
import pandas as pd
from one.api import ONE

# change my username to your own
project = 'churchland_learninglifespan'
save_dir = os.path.join(os.path.expanduser('~'), 'data_pi-uraiae/ONE/alyx.internationalbrainlab.org/', project)

# THIS IS THE OFFICIAL WAY - FIND THE RELEVANT SESSIONS FROM THE LOCAL CACHE
# If you want to use this cache without re-downloading data (i.e. keep the download cache the same as the main IBL Alyx), you can use the tags system.
one = ONE(mode='local', cache_dir = save_dir)
one.load_cache()
# one = ONE(mode='local')
# one.load_cache(cache_dir=save_dir)
print('Datasets location: %s;\nCache table location: %s' % (one.cache_dir, save_dir))
eids = one.search(lab='churchlandlab', query_type='local', dataset='spikes.times')
print(len(eids)) # should be 51...

# THIS IS THE HACK WAY - READ IN THOSE EIDS THAT CERTAINLY ARE AVAILABLE LOCALLY
eids = pd.read_csv(os.path.join(save_dir,'eids_on_alice.csv'))
eids = eids.eid.values
print(len(eids)) # should be 51...

```

## Getting started with IBL neural data
* See [docs.internationalbrainlab.org/](https://int-brain-lab.github.io/iblenv/public_docs/public_introduction.html) for a landing page and overview.
* You can find some example data and check out analyses [here](https://int-brain-lab.github.io/iblenv/notebooks_external/data_release_repro_ephys.html).
* Browse the data in this [interactive visualization app](https://viz.internationalbrainlab.org/app).
- See [here](https://docs.google.com/presentation/d/1hH-iv7721-5mnPSmqlSuZRyMTOVWQizjC0mymWX1z5U/edit#slide=id.g2b37c37de99_0_61) for a tutorial given at COSYNE 2024 (recording [here](https://drive.google.com/file/d/15uvU6A8eDyjVEhw_JOEzbqEbtt9U4-MX/view?usp=drive_link), accessible with an IBL account).

### Working with unpublished IBL data on ALICE

In our lab's shared ALICE project space (`data_pi-uraiae`) live IBL data which are not available through the `openalyx` public dataset. You can point ONE to use this local cache using the snippet below: 

```python
from one.api import ONE
one = ONE()

# Load with ONE in local mode
save_dir = os.path.join(os.path.expanduser('~'), 'data_pi-uraiae/ONE/alyx.internationalbrainlab.org/')
one = ONE(mode='local', cache_dir=save_dir)
```

In the same folder, there is a file `subject_info.csv` with date of birth and sex for all animals to compute their age at the time of the ephys recording).