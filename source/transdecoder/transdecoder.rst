.. _backbone-label:  

TransDecoder
============================== 

Introduction
~~~~~~~
``TransDecoder`` identifies candidate coding regions within transcript sequences, such as those generated by de novo RNA-Seq transcript assembly using Trinity, or constructed based on RNA-Seq alignments to the genome using Tophat and Cufflinks.

- TransDecoder identifies likely coding sequences based on the following criteria:

- a minimum length open reading frame (ORF) is found in a transcript sequence

- a log-likelihood score similar to what is computed by the GeneID software is > 0.

- the above coding score is greatest when the ORF is scored in the 1st reading frame as compared to scores in the other 2 forward reading frames.

- if a candidate ORF is found fully encapsulated by the coordinates of another candidate ORF, the longer one is reported. However, a single transcript can report multiple ORFs (allowing for operons, chimeras, etc).

- a PSSM is built/trained/used to refine the start codon prediction.

- **optional** the putative peptide has a match to a Pfam domain above the noise cutoff score.


Detailed usage can be found here: https://github.com/TransDecoder/TransDecoder/wiki#running-transdecoder


Versions
~~~~~~~~
- 5.5.0

Commands
~~~~~~
- TransDecoder.LongOrfs
- TransDecoder.Predict
- cdna_alignment_orf_to_genome_orf.pl
- compute_base_probs.pl
- exclude_similar_proteins.pl
- fasta_prot_checker.pl
- ffindex_resume.pl
- gene_list_to_gff.pl
- get_FL_accs.pl
- get_longest_ORF_per_transcript.pl
- get_top_longest_fasta_entries.pl
- gff3_file_to_bed.pl
- gff3_file_to_proteins.pl
- gff3_gene_to_gtf_format.pl
- gtf_genome_to_cdna_fasta.pl
- gtf_to_alignment_gff3.pl
- gtf_to_bed.pl
- nr_ORFs_gff3.pl
- pfam_runner.pl
- refine_gff3_group_iso_strip_utrs.pl
- refine_hexamer_scores.pl
- remove_eclipsed_ORFs.pl
- score_CDS_likelihood_all_6_frames.pl
- select_best_ORFs_per_transcript.pl
- seq_n_baseprobs_to_loglikelihood_vals.pl
- start_codon_refinement.pl
- train_start_PWM.pl
- uri_unescape.pl
 
Module
~~~~~~~
You can load the modules by::

    module load biocontainers
    module load transdecoder

Example job
~~~~~~
.. warning::
    Using ``#!/bin/sh -l`` as shebang in the slurm job script will cause the failure of some biocontainer modules. Please use ``#!/bin/bash`` instead.

To run transdecoder on our our clusters::

    #!/bin/bash
    #SBATCH -A myallocation     # Allocation name 
    #SBATCH -t 20:00:00
    #SBATCH -N 1
    #SBATCH -n 24
    #SBATCH --job-name=transdecoder
    #SBATCH --mail-type=FAIL,BEGIN,END
    #SBATCH --error=%x-%J-%u.err
    #SBATCH --output=%x-%J-%u.out

    module --force purge
    ml biocontainers transdecoder
    
    gtf_genome_to_cdna_fasta.pl transcripts.gtf test.genome.fasta > transcripts.fasta 
    gtf_to_alignment_gff3.pl transcripts.gtf > transcripts.gff3
    TransDecoder.LongOrfs -t transcripts.fasta
    TransDecoder.Predict -t transcripts.fasta
    
