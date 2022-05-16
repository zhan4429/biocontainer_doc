.. _backbone-label:

Prinseq
==============================

Introduction
~~~~~~~~
``Prinseq`` is a tool that generates summary statistics of sequence and quality data and that is used to filter, reformat and trim next-generation sequence data. For more information, please check its website: https://biocontainers.pro/tools/prinseq and its home page: http://prinseq.sourceforge.net.

Commands
~~~~~~~
- prinseq-graphs-noPCA.pl
- prinseq-graphs.pl
- prinseq-lite.pl

Module
~~~~~~~~
You can load the modules by::
    
    module load biocontainers
    module load prinseq

Example job
~~~~~
To run Prinseq on our clusters::

    #!/bin/bash
    #SBATCH -A myallocation     # Allocation name 
    #SBATCH -t 1:00:00
    #SBATCH -N 1
    #SBATCH -n 1
    #SBATCH --job-name=prinseq
    #SBATCH --mail-type=FAIL,BEGIN,END
    #SBATCH --error=%x-%J-%u.err
    #SBATCH --output=%x-%J-%u.out

    module --force purge
    ml biocontainers prinseq