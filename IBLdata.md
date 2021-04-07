---
layout: default
title: Working with IBL data
rank: 3
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
4. From the [NMA-IBL DataJoint GitHub](https://github.com/int-brain-lab/nma-ibl), launch the first Colab notebook and follow the instructions to enter your newly obtained credentials (do this locally, rather than inside the Colab). After entering your username and password, run `dj.config.save_local()` to create a local config file. You won't have to enter your DataJoint credentials anymore in the future! Note that this local file `dj_local_config.json` will only live inside the current folder, so it won't be recognized if you launch Python from somewhere else.
    * See more [here](https://docs.datajoint.io/python/setup/01-Install-and-Connect.html) and [here](https://int-brain-lab.github.io/iblenv/dj_docs/dj_credentials.html).

#### Play with the data

