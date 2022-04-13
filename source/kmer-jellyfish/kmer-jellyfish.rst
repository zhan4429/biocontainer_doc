.. _backbone-label:

Jellyfish
==============================

Introduction
~~~~~~~~
``Jellyfish`` is a tool for fast, memory-efficient counting of k-mers in DNA. A k-mer is a substring of length k, and counting the occurrences of all such substrings is a central step in many analyses of DNA sequence. For more information, please check its website: https://biocontainers.pro/tools/kmer-jellyfish and its home page: http://www.genome.umd.edu/jellyfish.html.

Commands
~~~~~~~
- jellyfish

Module
~~~~~~~~
You can load the modules by::
    
    module load biocontainers
    module load kmer-jellyfish

Example job
~~~~~
To run Jellyfish on our clusters::

    #!/bin/bash
    #SBATCH -A myallocation     # Allocation name 
    #SBATCH -t 1:00:00
    #SBATCH -N 1
    #SBATCH -n 1
    #SBATCH --job-name=kmer-jellyfish
    #SBATCH --mail-type=FAIL,BEGIN,END
    #SBATCH --error=%x-%J-%u.err
    #SBATCH --output=%x-%J-%u.out

    module --force purge
    ml biocontainers kmer-jellyfish