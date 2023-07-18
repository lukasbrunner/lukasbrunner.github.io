---
permalink: open_science/
title: "Open Science"
author_profile: true
share: false
---

<p style="text-align: center;"><b>For me open science means making results, code, and data usable and not just accessible &ndash; for the scientific community as well as society.</b></p>

I try to follow best practices such as <a href="https://climatefootnotes.com/2016/11/16/this-article-is-open-access/" target="_blank">open access publishing</a>
<!-- <a href="https://www.youtube.com/watch?v=L5rVH1KGBCY" target="_blank">open access publishing</a>  -->
and <a href="https://creativecommons.org" target="_blank">permissive licensing</a>, coding <a href="https://pep8.org/" target="_blank">style guides</a> and <a href="https://realpython.com/documenting-python-code/" target="_blank">documentation</a>,  <a href="https://cfconventions.org" target="_blank">metadata conventions</a> and <a href="https://www.go-fair.org/fair-principles" target="_blank">the FAIR data principles</a>, as well as <a href="https://github.com" target="_blank">version control</a> and transparency in data and code usage in general.

You are free to use any of the material I provide following the rules of the indicated licenses (mostly <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC BY</a>). In addition I'd be thankful if you let me know so that I can keep track (but you don't have to).

If you publish scientific work based on material I provide please consider citing some of my papers and putting me in the acknowledgements if appropriate.

<!-- Impact -->
<!-- ------ -->

<!-- - Climate Model Projections of 21st Century Global Warming Constrained Using the Observed Warming Trend (Liang et al. 2020): "We acknowledge Lukas Brunner and Ruth Lorenz for publishing their weighting code." -->

<!-- - "We thank Urs Beyerle, Jan Sedláček, Ruth Lorenz, and Lukas Brunner for retrieving and preprocessing the CMIP data" -->
<!-- https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2019GL086812 -->



Code
----

### Model Learning: Data and Code for identifying climate models

Model learning combines the terms climate model and machine learning providing a framework to disdinguish models and observations based on output maps. The backgrounds are described in Brunner and Sippel (<a href="https://lukasbrunner.github.io/files/Brunner2023.pdf" target="_blank">2023</a>), the data and code version used for the publication are available from <a href="https://doi.org/10.5281/zenodo.7998436" target="_blank">Zotero</a>, and the most recent version of the code can be found on <a href="https://github.com/lukasbrunner/model_learning" target="_blank">GitHub</a>.


### Global blocking detection

During my PhD I implemented a blocking detection algorithm in Python and manly based on [xarray](https://xarray.pydata.org). It enables the classification of atmospheric blocks based on global geopotential height fields and following different definitions from the literature. A detailed description can be found in section 3.2 (page 25f) of my <a href="/files/Brunner2018_PhD.pdf" target="_blank">PhD-thesis</a>. The code is freely available under a MIT license on GitHub:
<a href="https://github.com/lukasbrunner/blocking" target="_blank">https://github.com/lukasbrunner/blocking</a>

<!-- <blockquote style="padding: 10px"> -->
<!-- We follow the three-step algorithm described by Brunner and Steiner (2017) and Brunner (2018). -->
<!--  &ndash; <a target="_blank" href="https://doi.org/10.1002/wea.4020">Yessimbet et al. 2019</a> -->
<!-- </blockquote> -->



### Climate model Weighting by Independence and Performance (ClimWIP) &ndash; Standalone

The Climate model Weighting by Independence and Performance (ClimWIP) package is based on earlier work by people from the Climate Physics group at ETH Zurich (mainly Reto Knutti, Jan Sedláček, and Ruth Lorenz). Ruth Lorenz and I have implemented the current version in Python and it is freely available under a GPLv3.0 on GitHub:  <a href="https://github.com/lukasbrunner/ClimWIP" target="_blank">https://github.com/lukasbrunner/ClimWIP</a>

<!-- <blockquote style="padding: 10px"> -->
<!-- We acknowledge Lukas Brunner and Ruth Lorenz for publishing their weighting code. -->
<!--  &ndash; <a target="_blank" href="https://doi.org/10.1029/2019GL086757">Liang et al. 2020</a> -->
<!-- </blockquote> -->


### Climate model Weighting by Independence and Performance (ClimWIP) &ndash; ESMValTool

Supported by the eScience Center and the ESMValTool team (in particular Peter Kalverla) we have also added the ClimWIP method as a _diagnostic_ to the <a href="https://docs.esmvaltool.org" target="_blank">ESMValTool</a>, including several _recipes_ to reproduce some of our published studies: <a href="https://docs.esmvaltool.org/en/latest/recipes/recipe_climwip.html" target="_blank">ClimWIP recipes</a>


Data
----

### CMIP6 next generation data archive

I have lead work to post-process CMIP6 data from ESGF into a quality-controlled, highly consistent database termed ETH Zurich CMIP6 next generation archive (CMIP6ng). Due to technical reasons and because we do not have dedicated funding for it the data is not directly available online. I do no longer work at ETH but they normally provide download options (ftp, rsync) for the data upon request: [cmip6-archive@env.ethz.ch](mailto:cmip6-archive@env.ethz.ch). A documentation is available [here](https://doi.org/10.5281/zenodo.3734127).

<!-- <blockquote style="padding: 10px"> -->
<!-- We thank Urs Beyerle, Jan Sedláček, Ruth Lorenz, and Lukas Brunner for retrieving and preprocessing the CMIP data.  &ndash; <a target="_blank" href="https://doi.org/10.1029/2019GL086812">Beusch et al. (2020)</a>  -->
<!-- </blockquote> -->

<!-- <blockquote style="padding: 10px"> -->
<!-- Urs Beyerle and Lukas Brunner prepared the CMIP6 data server. -->
<!--  &ndash; <a target="_blank" href="https://doi.org/10.1029/2020GL089964">Pendergrass (2020)</a> -->

<!-- <blockquote style="padding: 10px"> -->
<!-- We thank U. Beyerle, J. Sedlacek and L. Brunner for downloading and processing the CMIP5 and LS3MIP data.  -->
<!--  &ndash; <a target="_blank" href="https://doi.org/10.1038/s41561-020-0594-1">Padrón (2020)</a> -->


### Gridded radio occultation data

During my PhD I created a dataset of gridded radio occultation (RO) climatologies from 2006 to 2016. I used them to investigate atmospheric blocking and related impacts but they might also be useful of other applications. A detailed description of the data and the processing can be found in section 4.3 (page 35f) of my <a href="/files/Brunner2018_PhD.pdf" target="_blank">PhD-thesis</a>. The data are freely available from the Climate Change Center Austria (CCCA):
- geopotential height: <a target="_blank" href="https://hdl.handle.net/20.500.11756/e4f48220">link</a>
- temperature: <a target="_blank" href="https://hdl.handle.net/20.500.11756/8245c63e">link</a>
- specific humidity: <a target="_blank" href="https://hdl.handle.net/20.500.11756/122eeb7a">link</a>
