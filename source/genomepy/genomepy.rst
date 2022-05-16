.. _backbone-label:

Genomepy
==============================

Introduction
~~~~~~~~
``Genomepy`` is designed to provide a simple and straightforward way to download and use genomic data. For more information, please check its website: https://biocontainers.pro/tools/genomepy and its home page on `Github`_.

Commands
~~~~~~~
- genomepy

Module
~~~~~~~~
You can load the modules by::
    
    module load biocontainers
    module load genomepy

Example job
~~~~~
To run Genomepy on our clusters::

    #!/bin/bash
    #SBATCH -A myallocation     # Allocation name 
    #SBATCH -t 1:00:00
    #SBATCH -N 1
    #SBATCH -n 1
    #SBATCH --job-name=genomepy
    #SBATCH --mail-type=FAIL,BEGIN,END
    #SBATCH --error=%x-%J-%u.err
    #SBATCH --output=%x-%J-%u.out

    module --force purge
    ml biocontainers genomepy

.. _Github: https://github.com/vanheeringen-lab/genomepy