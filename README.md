# bmc_bioinf_2016_erbilgin
## Predicting Resource Depletion of Mixed Bacterial Cultures
![alt text](https://raw.githubusercontent.com/biorack/bmc_bioinf_2016_erbilgin/master/trp.tiff "Tryptophan prediction and usage")

### A workflow to use exometabolomics data collected over the growth curve of a bacterial species to predict how a co-culture of bacteria will deplete resources in a medium or environment
##### Authors: Onur Erbilgin and Ben Bowen, Lawrence Berkeley National Laboratory

This workflow is described in the publication:
>Dynamic substrate preferences predict metabolic properties of a simple microbial consortium. (2016) Onur Erbilgin, Benjamin P. Bowen, Suzanne M. Kosina, Stefan Jenkins, Rebecca K. Lau, Trent R. Northen. BMC Bioinformatics, in review.


## Required Packages:
* Python 2.7
* Pandas
* NumPy
* SciPy
* MatPlotLib

## Input Data:
* Compound concentrations for each species, replicate, and timepoint
  * Example file: `./data/20151130_OAM1_QuantResults_v2C.csv`
* Biomass measurements for each species, replicate, and timepoint
  * Example file: `./data/Data/20151014_3B10_9B05_L13_timecourse.csv`
* Growth rate (average and error) of each species on individual carbon sources
  * Example file: `./data/singleresource_data.xlsx`
* Starting molarity of each compound in the growth medium
  * Example file: `./data/molarity.txt`
* Percent amino acid composition of the translated genome of each species
  * Example file: `./data/percent_AA_composition_genome.xlsx`
* Experimental observations of metabolite usage of the co-culture, to compare predictions
  * Example file: averaged: `./data/20160328_Enigma_coculture_avg_v2.csv`
  * Example file: standard error: `./data/20160328_Enigma_coculture_stderr_v2.csv`

## Description of Notebooks
### `./notebooks/ch1_load_data.ipynb`
1. Reads in metabolomics data and organizes it into a dictionary

### `./notebooks/ch2_fit_data.ipynb`
1. Fits the metabolomics data to a published model of resource depletion
2. Calculates "T-half" (time of half depletion)
3. Calculates "Usage Window" (time of resource usage)
4. Calculates maximum resource depletion rate relative to biomass
5. Plots average T-half and Usage Window on the average growth curve of each species

### `./notebooks/ch3_correlate_data.ipynb`
1. Plots T-half, growth rate on a single resource, maximum uptake rate, starting molarity of compound, and percent amino acid composition against each other
2. Calculates correlation coefficients and p-values of the comparisons

### `./notebooks/ch4_predict_depletion.ipynb`
1. Using metabolomics data collected on single-species growth (Notebooks 1 and 2), predict how a co-culture of the different species would deplete resources in the same medium

## License Information
Coming soon
