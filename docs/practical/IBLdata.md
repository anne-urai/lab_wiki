---
layout: default
title: Working with IBL data
parent: Data analysis
nav_order: 2
---
## Working with IBL data

Many projects make use of the large dataset collected by the [International Brain Laboratory](https://www.internationalbrainlab.com/).

### General info
* [eLife paper](https://elifesciences.org/articles/63711) describing the experiments and the behavioral data.
* [Video description of the data by Eric deWitt](https://www.youtube.com/watch?v=NofrFH8FRZU), for NeuroMatchAcademy.
* Explore the data through the [interactive data explorer](https://viz.internationalbrainlab.org/).

## Behavioral data
* See [data.internationalbrainlab.org](https://docs.internationalbrainlab.org/notebooks_external/2021_data_release_behavior.html) for a landing page and overview.

### Neural data
The IBL's neural recordings will be fully released once completed. Until then, you can find some example data and check out analyses [here](https://int-brain-lab.github.io/iblenv/06_examples.html).

* See [docs.internationalbrainlab.org/](https://int-brain-lab.github.io/iblenv/public_docs/public_introduction.html) for a landing page and overview.
* You can find some example data and check out analyses [here](https://int-brain-lab.github.io/iblenv/notebooks_external/data_release_repro_ephys.html).
* Browse the data in this [interactive visualization app](https://viz.internationalbrainlab.org/app).
- See [here](https://docs.google.com/presentation/d/1hH-iv7721-5mnPSmqlSuZRyMTOVWQizjC0mymWX1z5U/edit#slide=id.g2b37c37de99_0_61) for a tutorial given at COSYNE 2024 (recording [here](https://www.youtube.com/watch?v=NskZZ2dKeP8)).
- See [here](https://www.ucl.ac.uk/neuropixels/training/2024-neuropixels-course) for a online course on Neuropixels (recording [here](https://www.youtube.com/playlist?list=PLfhWmWntvjl7SYCcrM5Qy1RFIiIIO6MK-)).

# Accessing data on ALICE
{: .warning }
Currently, the ALICE IBL data (described below) has not been maintained - instead, lab members analyzing internal IBL data should ideally follow the IBL onboarding procedure to get access to data that has not been publicly released.

In our lab's shared ALICE project space (`data_pi-uraiae`) live IBL data which are not available through the `openalyx` public dataset. You can point ONE to use this local cache using the snippet below: 

Email the ALICE helpdesk to get access to the shared data folder: `data_pi-uraiae`. 

```python
from one.api import ONE
one = ONE()

# Load with ONE in local mode
save_dir = os.path.join(os.path.expanduser('~'), 'data_pi-uraiae/ONE/alyx.internationalbrainlab.org/')
one = ONE(mode='local', cache_dir=save_dir)
```

In the same folder, there is a file `subject_info.csv` with date of birth and sex for all animals to compute their age at the time of the ephys recording).

See the snippet below to load from the cache.

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
