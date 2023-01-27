---
layout: default
title: IBL behavioral data
---

## Getting started with IBL neural data
* See [docs.internationalbrainlab.org/](https://int-brain-lab.github.io/iblenv/public_docs/public_introduction.html) for a landing page and overview.
* You can find some example data and check out analyses [here](https://int-brain-lab.github.io/iblenv/notebooks_external/data_release_repro_ephys.html).
* Browse the data in this [interactive visualization app](https://viz.internationalbrainlab.org/app).

### Working with unpublished IBL data on ALICE

In our lab's shared ALICE project space (`data_pi-uraiae`) live IBL data which are not available through the `openalyx` public dataset. You can point ONE to use this local cache using the snippet below: 

```python
from one.api import ONE
one = ONE()
project = 'churchland_learninglifespan'

# Load with ONE in local mode
save_dir = os.path.join(os.path.expanduser('~'), 'data_pi-uraiae/ONE/alyx.internationalbrainlab.org/', project)
one = ONE(mode='local', cache_dir=save_dir)
```