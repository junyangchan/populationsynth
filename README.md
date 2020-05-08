# Populationsynth
Population Synthesize using Bayesian Network and IPU

Run in the following order bn_popsynth_person -> bn_popsynth_household -> combine -> IPU -> visualization

# Required

library(bnlearn)
library(tidyverse)
library(magrittr)
library(readr)
library(readxl)
library(ipfr)
library(plotly)

# Overview
We start by building Person and Household level data using Bayesian Network from bn_popsynth_person and bn_popsynth_household. 
In the combining stage, we start by allocating a person as head of household by matching variables from the household and person level data generated previously. Next, we breakdown the household into couple or noncouple household. 
For couple household, we then figure out how many children do they have based on Npax and NumofChildren variable. Next, we then allocate random people to fill up the remaining numbers in the Npax variable. For noncouple household, we figure out how many random people to allocate to fill up the household based on the Npax variable. 
After that, we finally breakdown the population into...

- household with 1 children
- household with 2 children
- household with 3 children
- household with 4 children
- household with 5 children
- household with 6 children
- household with 1 children with other people
- household with 2 children with other people
- household with 3 children with other people
- single household
- household with 2 others
- household with 3 others
- household with 4 others
- household with 5 others
- household with 6 others

After combining them all to form a population, we use this disaggregated sample to run through IPU.In the IPU stage, we first get target values which are basically tables extracted from SingStat. Next, we determine what variables should we aim for IPU to converge to*. After running through IPU, we finally get our intended output and can visualise the results in the Visualisation file. 

*while choosing to converge to subzone level attributes, it will take very long to converge. 
