---
layout: single
title: Microbial Simulation Environment
permalink: /MSE/
author_profile: true
---

The Microbial Simulation Environment (MSE) is a MATLAB Toolbox for the simulation of microbial genome-scale models (GEMs) in the natural environment. MSE expands beyond traditional flux balance analysis (FBA) by incorporating physiological acclimation processes which are otherwise assumed to be static. Microbes suited to life in dynamic environments, where resource availability and temperature change on multiple time-scales, are remarkably plastic in their metabolism and physiology. In addition to the many changes in metabolic flux topology, alterations to biochemical compositions are coordinated to drive elemental quotas lower when resources are scarce, thereby increasing growth yields. In addition, nutrient transporters are adjusted to match uptake rates to resource demands. For photosynthesizing microbes, pigment content is adjusted to harvest light more efficiently when light is low, or to provide protection from damage when light is high. From an individualist perspective (ignoring microbial community interactions), a maximal growth objective is assumed to guide these acclimation processes, and is the basis for MSE. 

What's needed to run MSE:

- GEM (see our accompanying distribution [PanGEM](https://github.com/jrcasey/PanGEM) for the reconstruction of GEMs from a pangenome)
- Cell size range
- Macromolecular composition ranges
- Pigment composition ranges (optional)
- Transporter dimensions (check out our [work](/assets/docs/CaseyFollows2020.pdf) on this and the accompanying [code](https://github.com/jrcasey/NutrientUptake))
- Optimal growth temperature (just a proteome sequence is required! Check out Gang Li's machine learning approach [here](https://github.com/EngqvistLab/tome_cool)

MSE can be cloned from [here](https://github.com/jrcasey/mse), hope you enjoy!