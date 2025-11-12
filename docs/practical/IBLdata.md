---
layout: default
title: Working with IBL data
rank: 7
---
## Working with IBL data

Many projects make use of the large dataset collected by the [International Brain Laboratory](https://www.internationalbrainlab.com/).

### General info
* [eLife paper](https://elifesciences.org/articles/63711) describing the experiments and the behavioral data.
* [Video description of the data by Eric deWitt](https://www.youtube.com/watch?v=NofrFH8FRZU), for NeuroMatchAcademy.
* Explore the data through the [interactive data explorer](https://viz.internationalbrainlab.org/).

### ToDo: Colab for IBL data analysis without local Python install
See [here](https://medium.com/@nogamudrik_96888/how-to-access-dandis-dandisets-for-your-neural-data-project-64a643760d2b)

### Behavioral data
[Working with IBL behavioral data](https://int-brain-lab.github.io/iblenv/notebooks_external/loading_trials_data.html)

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
