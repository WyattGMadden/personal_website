---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "High Performance Cluster (HPC) Notes"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2023-08-18T17:09:03-04:00
lastmod: 2023-08-18T17:09:03-04:00
featured: false
draft: false
---

This post contains notes on working with an HPC running SLURM. 

It includes a guide to submitting multiple R/Python jobs and other odds and ends.

Some useful resources (and sources for this post):

* [official documentation](https://github.com/RSPH-HPC/Documentation/blob/master/HPC%20Getting%20Started%20Guide.pdf)

* [BIOS specific documentation](https://scholarblogs.emory.edu/rsph-hpc/)

* [yanglab introduction](https://yanglab-emory.github.io/assets/ComputationSlides/RSPH_HPC_StartGuide_Yang.html)

* [BIOS virtual workshop](https://scholarblogs.emory.edu/rsph-hpc/files/2020/11/2020-11-20-BIOS-HPC-Workshop.pdf)



# Run R jobs

## Run a function across multiple jobs with different parameters

This is an example of running an R function across many jobs, each with a different parameter combination


### Create function file

This is the `R` code that you want to run.

`my_function.R`:

```R
get_normal_sims <- function(n, mean, sd) {
    sims <- rnorm(n = n, mean = mean, sd = sd)
    saveRDS("sims")
}
```

### Create CSV with parameter combinations of interest

Each row of this csv contains one parameter combination of interest, to be inputed into the previous `R` function.

`job_params.csv`:
```csv
n,mean,sd
1000,0,2
100,10,1
10000,50,1000
```

### Create job script to send one job to HPC

`run_one_job.sh`:
```hpc
#!/bin/bash
#SBATCH --job-name=rnormalsim      # create a short name for your job
#SBATCH --nodes=1                  # node count
#SBATCH --partition=day-long-cpu
#SBATCH --ntasks=1                 # total number of tasks across all nodes
#SBATCH --cpus-per-task=1          # cpu-cores per task (>1 if multi-threaded tasks)
#SBATCH --mem=4G                   # total memory per node (4 GB per cpu-core is default)
#SBATCH -o rnorm-sim-%A_%a.out  # output file format (%A is jobID, %a is task index)

module purge
module load R

Rscript -e << EEOF
source('your_function.R') 
get_normal_sims(n=as.integer(Sys.getenv('PARAM1')), 
                mean=as.integer(Sys.getenv('PARAM2')),
                sd=as.integer(Sys.getenv('PARAM3')))
EEOF
```

Note that the output of `Sys.getenv()` is always a string, and thus needs to be converted to the type that `get_normal_sims()` expects.


### Create shell script to run all the jobs

`run_all_jobs.sh`:
```bash
#!/bin/bash

tail -n +2 job_params.csv | while IFS=',' read -r param1 param2 param3
do
    sbatch --export=PARAM1="param1",PARAM2="param2",PARAM3="param3" run_one_job.sh
done
```
### Submit jobs

Finally run the following bash commands in the cluster to send all jobs:

```bash
chmod +x run_all_jobs.sh
./run_all_jobs.sh
```









# Other Notes

## Install R package from github

This is an example of installing current version of `grmbayes` from my github. 

Run the following code on the HPC:

```bash
module load R
Rscript -e "devtools::install_github('wyattgmadden/grmbayes')"
```

## ssh into node

```bash
ssh NODE#
top -u wmadden
```

## See current jobs

```bash
squeue -u wmadden
```

## Cancel all jobs sharing a name

```bash
squeue -u wmadden --format="%i %j" | awk '$2=="job_name" {print $1}' | xargs -I {} scancel {}
```

## Check current use of private nodes

```bash
sinfo -p nodeowner  -o "%10N %20C %20m %10F"
```

where `nodeown` is the username of the owner of the private nodes. 

