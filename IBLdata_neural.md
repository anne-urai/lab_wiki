---
layout: default
title: IBL behavioral data
---

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