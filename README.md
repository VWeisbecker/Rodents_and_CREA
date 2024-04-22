# Beyond CREA: evolutionary patterns of non-allometric shape variation and divergence in a highly allometric clade of murine rodents - data and code
<a href="https://zenodo.org/doi/10.5281/zenodo.10211694"><img src="https://zenodo.org/badge/721090538.svg" alt="DOI"></a>

Code authors: Ariel E. Marcy, Dr Thomas Guillerme, Associate Professor Vera Weisbecker

*All scripts are in RMarkdown format (.Rmd), which can be opened in RStudio. There, you can edit and run code chunks as normal or use the Knit button to create HTML versions with both code and output. After cloning this repo, remember to either set your working directory to the folder containing the code on your computer or open an RStudio project from that folder. 3D meshes for plotting are released separately on Figshare as per the manuscript*

## Data
**Landmarking data:**
* [MorphoSource Project 561](https://www.morphosource.org/Detail/ProjectDetail/Show/project_id/561) publically provides 3D meshes for all surface scanned crania landmarked in the study.
* [Raw_Coordinates.csv](Data/Raw/Raw_Coord_Data.csv) provides the shape coordinates from landmarked 3D crania exported from Viewbox.

If you use these data, please cite: 
> Marcy, A. E., T. Guillerme, E. Sherratt, K. C. Rowe, M. J. Phillips, and V. Weisbecker. 2020. Australian Rodents Reveal Conserved Cranial Evolutionary Allometry across 10 Million Years of Murid Evolution. The American Naturalist. https://doi.org/10.1086/711398

**Ecological metadata:**
* [Trait data from Breed & Ford 2007](/Data/Processed/in_ex_traits.csv)

If you use these data, please cite the original authors:
> Breed B & Ford F. 2007. Native Mice and Rats. Australian Natural History Series, CSIRO Publishing: Colling-wood, Victoria, Australia, 185 pp. ISBN 978-0-6430-9166-5.

**Phylogenetic data:**
* [Fossil calibrated ultrametric tree from Smissen & Rowe 2018 and Marcy et al. 2020](/Data/Processed/Marcy-BEAST01.con.tre)

If you use these data, please cite the original authors:
> Smissen PJ & Rowe KC. 2018. Repeated biome transitions in the evolution of Australian Rodents. Molecular Phylogenetics and Evolution. 128:182–191. doi: [10.1016/j.ympev.2018.07.015.](https://doi.org/10.1016/j.ympev.2018.07.015)

> Marcy, A. E., T. Guillerme, E. Sherratt, K. C. Rowe, M. J. Phillips, and V. Weisbecker. 2020. Australian Rodents Reveal Conserved Cranial Evolutionary Allometry across 10 Million Years of Murid Evolution. The American Naturalist. https://doi.org/10.1086/711398
    
## Analyses
**The first three scripts prepare the data for analysis and plotting**, the intermediate data they generate are stored as .rda files in the [..Data/Processed](/Data/Processed) folder. These are too large to upload to GitHub so scripts must be run sequentially. 

* [**01-extract-data.Rmd**](/Analysis/01-extract-data.Rmd) Extracts both 3D coordinate data as well as the metadata data from Viewbox and prepares it for analysis with `geomorph`. Runs GPA with bilateral symmetry, merges the symmetric shape component with centroid size, and calculates asymmetric variation.
* [**02-calculate-user-error.Rmd**](/Analysis/02-calculate-user-error.Rmd) Allows users to view outliers, find major landmarking errors, and take out replicated specimens from the shape data. Also calculates user error to report in terms of repeatability. 
* [**03-prepare-data.Rmd**](/Analysis/03-prepare-data.Rmd) Prepares the shape datasets, the metadata, the phylogenetic data, and the vectors with graphics information for plotting. All of which are used throughout the later analyses and are saved in three different .rda files to improve efficiency.

**The next four scripts perform the analyses**, the tables and figures they generate are saved to the [..Data/Results](/Data/Results) folder.

* [**04-Evomode_Models_Allometry_residuals.Rmd**](/Analysis/04-Evomode_Models_Allometry_residuals.Rmd) Calculates the likelihood of shape, size, and allometric residual data evolving according to either Brownian Motion, Ornstein-Uhlenbeck, or Early Burst evolutionary models. Creates allometric residuals for downstream analyses. **Creates Table 1**

* [**05-plot-phylomorph-dist.Rmd**](/Analysis/05-plot-phylomorph-dist.Rmd) Plots phylo-morphological distance plots for both the full shape and shape residual datasets.  **Creates Figure 1**

* [**06_Allometry_modules.Rmd**](/Analysis/06_Allometry_modules.Rmd) Computes allometry in individual modules based on joint and separate GPA **Creates Table 2 and supplementary Table 1**

* [**07-compare-PCAs.Rmd**](/Analysis/07-compare-PCAs.Rmd) Plots the full shape PCA versus shape residual PCAs colored by diet/locomotion.  **Creates Figure 2**

* [**08_01-heatmap-both-datasets.Rmd**](/Analysis/08_01-heatmap-both-datasets.Rmd) Plots the `landvR` heatmaps of shape changes over the PC axes for both allometric and residual shape (allometry-free) datasets. **Creates Figure 3**

* [**08_01-heatmap-both-datasets.Rmd**](/Analysis/08_01-heatmap-both-datasets.Rmd) Plots the `landvR` heatmaps of shape changes over the allometric fit based on a non-phylogenetically corrected model **Creates supplementary Figure 1**

* [**09-test-modularity.Rmd**](/Analysis/09-test-modularity.Rmd) Tests modularity and integration using the modules defined for mammalian skulls in Goswami 2006 & 2007. **Creates supplementary Figure 4 and Tables 3-6**


### Custom functions
Some analyses call custom functions, most of which are defined in the [..Functions/utilities.R](/Functions/utilities.R) file. A modified version of `geomorph`'s function `plotGMPhyloMorphoSpace` is defined in the [..Functions/plotGMPhyloMorphoSpace_plotmod.R](/Functions/plotGMPhyloMorphoSpace_plotmod.R) file.
