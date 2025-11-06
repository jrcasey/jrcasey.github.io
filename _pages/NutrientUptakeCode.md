---
layout: single
title: Nutrient Uptake
permalink: /NutrientUptakeCode/
author_profile: true
---

NutrientUptake is a Matlab toolbox for the prediction of nutrient transport by *acclimated* microbes. Microbes acclimate to changes in external substrate concentrations by adjusting their size and the numbers and types of membrane transporters (among other things!). Leveraging the growth of quantitative proteomics and metabolic modeling, we developed a steady-state prognostic model of substrate transport which requires only a single measurement of transporter abundance under optimal growth conditions. 

To learn more about our work on this topic, check out our PLOS Computational Biology [article](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1008140) [pdf](/assets/docs/CaseyFollows2020.pdf) and some more casual discussion [here](/MonodDroopBlackman/).

What's needed to run NutrientUptake:

- Genome-scale metabolic model
- Dimensions of the transporter (check out [RaptorX](http://raptorx.uchicago.edu/) for structure prediction and [PyMol](https://pymol.org/2/) for rendering and measurement). 
- Transporter abundance at maximum growth rate
- Cell size
- Maximum growth rate

You can clone NutrientUptake from [here](https://github.com/jrcasey/NutrientUptake)  

Also, NutrientUptake can be easily translated into a linear program, which we have implemented for four nutrients simultaneously in a set of 69 strains of *Prochlorococcus* [here](https://github.com/jrcasey/mse).  
