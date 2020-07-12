---
layout: single
title: Research
permalink: /research/
author_profile: true
---


## CBIOMES Project
####  Constraint-based modeling of marine microbial community metabolism and physiology

> As part of the [CBIOMES Project](https://cbiomes.org), I design detailed models of microbial metabolism and physiology to simulate microbial community dynamics in the marine environment. 

> Two MATLAB toolboxes are under development for this project: The **M**icrobiome **S**imulation **E**nvironment toolbox ([MSE](https://github.com/jrcasey/mse)) and the **PanGE**nome-scale **M**etabolic model toolbox PanGEM (sorry, still private). Lots more on them in time!    

> Here's a primer on what's to come...

<video src="/assets/images/Casey_narration.mp4" poster="/assets/images/poster.pdf" width="640" height="400" controls preload></video>


##### Mesoscale dynamics of *Prochlorococcus*

> **Update:** Our first full-scale simulation -- *Prochlorococcus* growth across an eddy dipole transect -- is complete! We are thrilled with the results and are currently sifting through all the data to develop a compelling story. 

> The model was run using *in situ* data collected on the [2017 MESO-SCOPE Cruise](http://scope.soest.hawaii.edu/data/mesoscope/),
including depth profiles of flow cytometry cell counts and scattering properties, ITS-based relative abundances, nutrient concentrations, spectral irradiance, and temperature. These data are fed at each grid point to genome-scale metabolic models (GEMs) for 48 sequenced isolate strains. Each GEM goes through a series of bilevel optimizations which **allow the cell to physiologically acclimate to its environment** by altering its size, its macromolecular composition, its pigment composition, and the abundance and types of transporters on the cell surface. Using the acclimated GSMM and the associated constraints, flux balance analysis is then run to predict growth rates and metabolic fluxes. Finally, we apply a modified Arrhenius function using optimal 
growth temperatures derived from a machine learning algorithm. Here is a teaser: 

[comment]: <> (![useful image](/assets/images/MSE_Pro_MESO-SCOPE.jpg =250x) )
<img src="/assets/images/MSE_Pro_MESO-SCOPE.jpg" alt="MSE_Pro_MESO-SCOPE" style="width:640px">
  
*Ecotype averaged growth rates (h<sup>-1</sup>), predicted at local noon across the MESO-SCOPE transect. Station 6 is the center of the anti-cyclone; Station 12 is the center of the cyclone. 5 Ecotypes are shown: **H**igh-**L**ight adapted ecotypes **I** and **II**, and **L**ow-**L**ight adapted ecotypes **I** **II/III** and **IV**. Don't worry about that HLI at the bottom lol.*   


> There seems to be either a boundless flow of genes or a jaw-dropping amount of persistent micro-diversity within the *Prochlorococcus* community. We could never hope to capture all the instances in GSMMs, so instead we are evolving *in silico*
strains synthesized from the pangenome using our PanGEM Toolbox. In addition to the 48 isolates, the pangenome also includes genes from 97 strains built from MAGs and SAGs, and we plan to include an additional 489 SAGs recently published by [Berube et al., 2018](https://www.nature.com/articles/sdata2018154).     

## Nutrient uptake
> **Update:** Accompanying code to Casey and Follows, 2020 can be cloned from [here](https://github.com/jrcasey/NutrientUptake).

#### Graphical Abstract
> Microbes acclimate to changes in substrate availability by altering the number of transporters on the cell surface, however there is some disagreement on just how. We revisit the physics of substrate uptake and consider the steady-state scenario whereby cells have acclimated to maximize fitness. Flux balance analysis of a stoichiometric model of *Escherichia coli* was used in conjunction with quantitative proteomics data and molecular modeling of membrane transporters to reconcile these opposing views. An emergent feature of the proposed model is a critical substrate concentration S<sup>*</sup>, which delineates two rate limits. At concentrations above S<sup>*</sup>, transporter abundance can be regulated to maintain uptake rates as demanded by maximal growth rates, whereas below S<sup>*</sup>, uptake rates are strictly diffusion limited. In certain scenarios, the proposed model can take on a qualitatively different shape from the familiar hyperbolic kinetics curves, instead resembling the long-forgotten Blackman kinetics.

[comment]: <> (![Figure 5](/assets/images/Figure_5.jpg =250x)  )
<img src="/assets/images/Figure_5.jpg" alt="Figure 5" style="width:640px">

#### Some comments about Monod, Droop and Blackman
> If you're reading this, you're likely familiar with Monod, at least vaguely familiar with Droop, and likely not at all familiar with Blackman kinetics, which I think is a shame. Let's start by describing the three models: Monod's model equates the growth rate with a ratio of the product of the substrate concentration and the maximum growth rate and the sum of the substrate concentration and the half saturation concentration; Droop's model relates the growth rate with the ratio of the cell quota of a limiting resource; Blackman's model relates the growth rate to a linear product of the substrate concentration up to some substrate concentration, above which the substrate is in excess. Thus, both Monod and Droop are hyperbolic, while Blackman is piecewise linear (first order -> zero order).    

Before we discuss the foundations and merits of these wildly different views, I will mention the obvious: these are by no means the only descriptions of substrate-limited growth (c.f., Westerhoff and probably hundreds of elaborations and witches brews of each), but that's well beyond the scope of this rant.

You may have noticed that the Monod kinetics model is structurally identical to the Michaelis-Menten model of enzyme catalyzed reactions, so let's critically evaluate whether the two systems they describe are fundamentally similar enough to be captured by a single model. Consider first that even the Michaelis-Menten model was analytically derived from a fairly radical simplification of otherwise complex reactions. The hyperbolic function describes the rates of formation of one or more chemical substrates to one or more products, catalyzed by a well-mixed, monodisperse enzyme catalyst suspension, held at steady state. In its most basic form, the reaction consists of two reversible steps - a step which binds a free substrate molecule to a free enzyme catalyst, forming a complex, and a step which then dissociates the product from the complex forming (a) free product molecule(s) and (a) free enzyme catalyst(s). The rate constants can be derived from collision theory, where a substrate-enzyme collision with insuficient energy to overcome an energy barrier results in no binding, or a sufficiently high energy collision between a product and the free enzyme again forms the enzyme substrate complex. Clearly there is a concentration dependence on both the forward and back reactions, as well as many other dependencies (e.g., temperature, pressure, pH, and chemical composition of the aqueous matrix). Anyway, one quickly realizes how oblique even this 2-step description is, considering the multitude of possible sequences of conformational changes associated with each of possibly multiple protein subunits, a dizzying array of poorly understood post-translational modifications, multiple substrates each with their own specificities, multiple intermediate reactions, ping-pong bi-bi, blah blah, *etc., etc., ad nauseum*. All this to say that replacing "enzyme" with "cell" is quite a leap, so it's less than obvious that cellular growth "kinetics" should be hyperbolic.          

Nevertheless, Monod saw, or wanted to see, a resemblance of Michaelis and Menten's *in vitro* reaction kinetics to his own *in vivo* measurements of *E. coli* and *M. tuburculosis* growth on glucose as a limiting substrate, stating in his seminal 1949 paper: *"Several mathematically different formulations could be made to fit the data. But it is both convenient and logical to adopt a hyperbolic equation."* But upon closer inspection, as several others would point out decades later, the *E. coli* data do not appear hyperbolic at all. A stepwise linear model, one with a sharp transition from first-order to zero-order, is at least an obvious candidate. The *M. tuburculosis* data do seem to fit a hyperbolic function, but no discussion of the difference in shape was bothered with. 

Considering the profound influence Monod has had on biochemistry and biophysics and their various applications in biotechnology, it is baffling that such a glaring inconsistency has been so overwhelmingly ignored for the better part of a century. Evidence in favor of both Blackman's and Monod's models can be observed in the literature, with some ensuing speculation about why one or another is right, but none have interpreted the data for what they show: that both are correct under different circumstances. For example, in a comparison of Monod and Droop with observations ([Sommer, 1991](https://ascelibrary.org/doi/10.1061/%28ASCE%29EE.1943-7870.0000257)),  


In our article, we provide a possible mechanism with can reconcile both of these views. 


[comment]: <> (> ![useful image](/assets/images/Figure_3.pdf =250x) ) 

<img src="/assets/images/Figure_3.pdf" alt="Figure 3" style="width:640px">

*Schematic of steady-state nutrient acclimation. A) – Optimal transporter abundances n<sup>*</sup> (solid green line) lie at the porter limitation (blue shaded region) boundary. All points above and below this boundary fail to maximize growth rate; for all points below, the uptake rate is sub-maximal; for all points above, some transporters are unoccupied. Over an interval of bulk substrate concentrations S<sup>∞</sup> ≤ S<sup>*</sup>, this boundary is met with diffusion limitation (orange shaded region), where the catalytic rate exceeds the encounter rate; as concentrations exceed S<sup>*</sup>, the porter limitation boundary transitions to an internal growth rate limit (yellow shaded region), where the catalytic rate exceeds the rate of some downstream reaction. B) – For smaller cells, or for transporters with slower k<sub>cat</sub>, membrane surface area limitation (a special case of porter limitation) may be encountered. In the interval bounded by S<sub>SA</sub><sup>lb</sup> and S<sub>SA</sub><sup>ub</sup>, n<sup>*</sup> is constrained to n<sub>max</sub> (black dashed line). C) – Growth rates of optimally acclimated cells (solid green line) follow the intersection of two limits: the diffusive limit (purple dashed line) and the internal growth limit μ<sup>G</sup><sub>max</sub> (black dashed line). These rate limits are, again, bisected by S<sup>*</sup> with a sharp transition. D) – If surface area limitation is encountered, growth rates in the interval S<sub>SA</sub><sup>lb</sup> ≤ S<sup>∞</sup> ≤ S<sub>SA</sub><sup>ub</sup> follow a more gradual, hyperbolic transition from diffusion limitation to growth limitation.*


## Biological thermodynamics
> Something "heating up" here... yuk yuk yuk.