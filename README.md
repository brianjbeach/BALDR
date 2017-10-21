## BALDR

BALDR is a pipeline for reconstructing human or rhesus macaque immunoglobulin(Ig)/B cell receptor(BCR) sequences from single cell RNA-Seq data generated by Illumina sequencing. 

BALDR is based on the *de novo* assembly of RNA-Seq reads. It allows reconstructions using following methods:
1. Unfiltered (human and rhesus) - Use all reads for assembling transcripts and select Ig transcript models
2. IG-mapped_only (human and rhesus) - Assemble reads mapping to Ig loci
3. IG-mapped_Unmapped (human and rhesus) - Assemble reads mapping to Ig loci + Unmapped reads
4. IMGT-mapped (human) - Assemble reads mapping to IMGT V(D)J and C sequences
5. Recombinome-mapped (human) - Assemble reads mapping to the Ig recombinome
6. FilterNonIG (rhesus)- Assemble reads after filtering those that match to non-Ig genes in the genome

## Pre-requisites
1. [Trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic)
2. [Trinity](https://github.com/trinityrnaseq/trinityrnaseq/wiki)
3. [bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml)
4. [STAR](https://github.com/alexdobin/STAR)
5. [samtools](http://www.htslib.org/download/)
6. [IgBLAST](https://www.ncbi.nlm.nih.gov/igblast/faq.html#standalone)
7. [seqtk](https://github.com/lh3/seqtk)
8. Perl 5

## Installation
Clone or download the BALDR package. 
`cd BALDR`
`chmod +x BALDR`

## Command line usage
```
BALDR <input files> <options>

  --single        fastq.gz file for single-end run (--single or -paired required)
  --paired        fastq.gz files for paired-end run. File names must be separated by a comma only
                  (e.g. --paired R1.fastq.gz,R2.fastq.gz) (--single or -paired required)
  --methods       One or more reconstruction methods. For multiple methods, separte only by comma.
                  human: IG-mapped_Unmapped (default), Unfiltered, IG-mapped_only, IMGT-mapped, Recombinome-mapped 
                  rhesus_monkey: FilterNonIG (default), Unfiltered, IG-mapped_only, IG-mapped_Unmapped
                  (e.g. --methods Unfiltered,IG-mapped_Unmapped)
  --organism,-o   human (default) or rhesus_monkey
  --trimmomatic   Path for trimmomatic.jar file (e.g. ~/Trimmomatic-0.36/trimmomatic-0.36.jar) (required)
  --adapter,-a    Path for the Trimmomatic adapter file (e.g. ~/Trimmomatic-0.36/adapters/NexteraPE-PE.fa) (required)
  --STAR_index    Path for the STAR genome index (optional). 
                  If not specified, the genome index for GRCh38 (Ensembl release 86) or MacaM v7 will be built the
                  first time BALDR is run and used. BALDR presently only supports GRCh38 (human) and MacaM v7 (rhesus).
  --BALDR         Path for the BALDR directory (e.g. ~/BALDR) (required)
  --memory        Max memory for Trinity (default 32G)
  --threads,-t    number of threads for STAR/bowtie2/Trinity (default 1)
  --version ,-V   Version
  --help,-h       Print this help
```


