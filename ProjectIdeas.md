---
layout: default
title: Project ideas
rank: 4
---

Some ideas for project topics and research questions.

### Publicly available data sets
My motto: if you can answer a question with existing data, why collect it anew?
- [Here](https://nivlab.github.io/opendata/) is a link to a large database of behavioral datasets.
- [Here](https://www.nature.com/articles/s41562-019-0813-1) is a paper describing a [database](https://osf.io/s46pr/) of >145 confidence datasets.
- [This paper](https://www.sciencedirect.com/science/article/pii/S0006322318300295#sec1) describes a perceptual decision making task with psychopathology questionnaires, dataset [here](https://github.com/metacoglab/RouaultSeowGillanFleming).

### Decision-making: data analysis
_See [here](https://anne-urai.github.io/lab_wiki/IBLdata.html) for some examples on getting started with existing IBL data_.
- Does choice history bias correlate with psychopathology, e.g. impulsivity? Reanalyse data from [Rouault et al. 2019](https://doi.org/10.1016/j.biopsych.2017.12.017) by fitting models of choice history bias (e.g. [logistic models](https://www.nature.com/articles/ncomms14637) or [drift diffusion models](http://dx.doi.org/10.7554/eLife.46331)). Can also collaborate with Tobias Donner to analyze personality questionnaires from [these data](https://www.nature.com/articles/s41467-022-33237-5) (see also [my PhD thesis](https://anneurai.files.wordpress.com/2020/12/urai.pdf), p.99).
- Do choice history biases transfer across tasks (i.e. do observers have an meta-prior estimate of the environment's stability, and apply it in different modalities/contexts)? Find dataset with large number of subjects who did multiple tasks, and correlate estimates of repetition/alternation behavior.
- How do decision-making strategies (such as perseverance) change with ageing? Fit behavioral models (e.g. [Ashwood et al. 2022](https://www.nature.com/articles/s41593-021-01007-z), [Findling et al. 2019](https://doi.org/10.1038/s41593-019-0518-9)) to decision-making data across the lifespan (both mice and humans). Potential collaboration with Peter Murphy, Dublin.
- Do learning and decision-making vary with the biological clock, and is it easier to learn when consistently practicing at the same time of day? Potential collaboration with [Christian Tudorache](https://www.universiteitleiden.nl/en/staffmembers/christian-tudorache#tab-1).
- How can we disentangle choice updating from slow drifts in decision criterion? Apply method proposed by [Gupta and Brody](https://www.biorxiv.org/content/10.1101/2021.09.17.460767v1), with Robin Vloeberghs.
- How much are human perceptual decisions affected by distinct states/epochs in behavior? Apply GLM-HMM method from [Ashwood et al](https://www.nature.com/articles/s41593-021-01007-z) (code [here](https://github.com/int-brain-lab/GLM-HMM/tree/main)) to open data from [the confidence database](https://www.nature.com/articles/s41562-019-0813-1) or [this longitudinal dataset](https://github.com/roeysc/dynamic_computational_phenotyping) with many different tasks.
- Fit data from [Gupta et al](https://doi.org/10.1101/2023.01.18.524599) with a history-dependent DDM, does the pattern found in [humans and mice](https://2023.ccneuro.org/view_paper.php?PaperNum=1119) also hold in rats? 
- Can we detect cognitive strategies using constrained RNNs? Fit new models (e.g. [here](https://www.biorxiv.org/content/10.1101/2023.04.12.536629v2), [here](https://www.biorxiv.org/content/10.1101/2023.05.17.541226v1), [here](https://www.biorxiv.org/content/10.1101/2023.06.23.546250v1), [tutorial](https://github.com/kstach01/CogModelingRNNsTutorial)) to perceptual decision-making data.
- Do mice show the same history-dependent choice history bias as humans? Implement [this work](https://2023.ccneuro.org/proceedings/0000544.pdf) in the new [HSSM package](https://github.com/lnccbrown/HSSM) and be a beta-tester. Together with Alex Fengler, Brown University.


### Neuroscience
- Test prediction: does inactivation of PPC (LIP inactivation in monkeys or TMS to IPS0/1 or IPS 2/3 in humans) during the ITI reduce choice history bias? Find data or run a TMS experiment.
- Do mice show 'handedness', i.e. a preference to respond with 'rightward' choices? Based on observation by Sebastian Bruijns, early on in the IBL task. Combine with literature review on handedness across decision-making tasks (especially in mice) with different response modalities.
- Using data from [Ni et al](https://www.pnas.org/doi/10.1073/pnas.2120529119), link changes in motivation under methylphenidate (Ritalin) to the Expected Value of Control theory. With Bryant Jongkees. Apply a DDM to go beyond simple P(correct).
- [Murray et al. 2014](https://www.nature.com/articles/nn.3862) found that cortical neurons display intrinsic timescales which become longer along the cortical hierarchy, and probably play an important role in longer-timescale functions like information maintenance. Has this finding been replicated in mice (beyond visual areas, see [Siegle et al.](https://www.nature.com/articles/s41586-020-03171-x)), and extended to subcortical areas (using the IBL dataset)? Does longer-timescale prior encoding (tracking of the block) mostly depend on neurons with long timescales in the IBL dataset? See also [Imani et al. 2023](https://www.biorxiv.org/content/10.1101/2023.01.01.522410v1).
    - Related: Cortical neurons display different degrees of intrinsic timescales, with longer timescales towards anterior cortical regions in primates (https://www.nature.com/articles/nn.3862). How do these timescales arise, and what are their roles in computation? One hypothesis is that these gradients arise from the genetic profile of different areas. As we're collecting the first brain-wide map of mouse neural activity during rest, this idea proposes to decompose the intrinsic timescale structure throughout the brain to different profiles of gene expression (from the Allen Atlas). See also [here](https://www.jneurosci.org/content/38/34/7476.long), [here](https://elifesciences.org/articles/61277).

### Decision-making: data collection
- How do decision-making strategies differ across mammalian species? Build and run a human version of the [IBL decision task](https://elifesciences.org/articles/63711), online and/or in the lab with EEG. 
- Are choice history biases consistent across different decision-making tasks, and over time?
- Can zebrafish learn the same decision-making tasks as mice and humans? Collaboration with [Christian Tudorache](https://www.universiteitleiden.nl/en/staffmembers/christian-tudorache#tab-1).

### Literature review
- How do different types of neural noise (measured with fMRI, EEG or cellular recordings) change with ageing? [notes and ideas](https://docs.google.com/document/d/1kLLwiOk3SCED-7TA_UJPe9wBCbTj4oFidi4L-bBUIkI/edit)
- The role of posterior parietal cortex in history-dependent choice biases. [first draft of mini-review](https://docs.google.com/document/d/147XMu9f7TnVrkyyEA8ord2bXruwk_jEJuaUvx5zBS1Y/edit)

### Climate action
- What type of messaging is most effective to mobilize people into climate actions? 
- How can we improve virtual conferences and meetings to make them a better replacement for in-person events?
- What is the carbon footprint of neuroscience data? Potential collaboration with [Charlotte Rae](https://profiles.sussex.ac.uk/p220408-charlotte-rae).
- How can we best visualize uncertainty and risk to communicate the urgency of the climate crisis? Data visualization and UX design.
- Analyze flight/travel data from university employees to see where the biggest improvements can be made. What kind of behavioral interventions  (policy, messaging, transparency) may help reduce aviation-related CO2 emissions?
- Visualize and describe the impacts of climate change on our city, university, faculty - and ways to adapt to sea-level rise, hotter summers, extreme weather.
- What is the effect of CO2 levels on cognitive function? Collaboration with Francesco Walker, using driving simulator. See https://doi.org/10.1038/s41370-018-0055-8, https://doi.org/10.1029/2019GH000237, 10.1289/ehp.1510037 
- see more ideas for climate psychology projects at [1in5](https://onedrive.live.com/redir?resid=A673B09CD3ADE8F9%2170595&authkey=%21AJAze9l8HYmInCI&page=View&wd=target%28Psychology.one%7C0f801ffb-c9dc-49b4-8f6b-94ea415b7ac3%2FCognitive%20Psychology%7Cf56caf88-c63c-4f71-b2bc-03fff9835dcc%2F%29&wdorigin=NavigationUrl). The 1in5 project: https://www.1in5project.info/

### Random
- Replicate [academic family tree clustering](http://www.nature.com/news/majority-of-mathematicians-hail-from-just-24-scientific-families-1.20491) using [Neurotree](https://twitter.com/AnneEUrai/status/769270998965321728).
- Add graphical contribution table to [Tenzing](https://github.com/marton-balazs-kovacs/tenzing/issues/71) for tracking authorship in large teams
