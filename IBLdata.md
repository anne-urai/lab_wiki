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
* Explore the data through the [old interactive portal](https://data-sciviz.internationalbrainlab.org/home) and the newer [interactive data explorer](https://viz.internationalbrainlab.org/).

### Behavioral data
[Working with IBL behavioral data](https://anne-urai.github.io/lab_wiki/IBLdata_behav.html)

### Neural data
[Working with IBL neural data](https://anne-urai.github.io/lab_wiki/IBLdata_neural.html)

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