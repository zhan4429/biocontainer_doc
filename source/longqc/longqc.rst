.. _backbone-label:

Longqc
==============================

Introduction
~~~~~~~~
LongQC is a tool for the data quality control of the PacBio and ONT long reads.
For more information, please check:
Docker hub: https://hub.docker.com/r/cymbopogon/longqc 
Home page: https://github.com/yfukasawa/LongQC

Versions
~~~~~~~~
- 1.2.0c

Commands
~~~~~~~
- longQC.py

Module
~~~~~~~~
You can load the modules by::

    module load biocontainers
    module load longqc

Example job
~~~~~
To run longqc on our clusters::

    #!/bin/bash
    #SBATCH -A myallocation     # Allocation name
    #SBATCH -t 1:00:00
    #SBATCH -N 1
    #SBATCH -n 1
    #SBATCH --job-name=longqc
    #SBATCH --mail-type=FAIL,BEGIN,END
    #SBATCH --error=%x-%J-%u.err
    #SBATCH --output=%x-%J-%u.out

    module --force purge
    ml biocontainers longqc
