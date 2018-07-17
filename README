#Introduction

Varsimlab is a command line python pieline designed to easily generate artificial genome or exome sequences, with structural and copy number variations. Using ART short read simulation and SInC error generation, Varsimlab can quickly simulate biologically realistic tumor and normal short reads

#Setup and Dependencies 
Varsimlab uses art_illumina to generate short reads with realistic sequencing errors. The documentation is available here 
(https://www.niehs.nih.gov/research/resources/software/biostatistics/art/index.cfm)
To install ART 
``` curl -O https://www.niehs.nih.gov/research/resources/assets/docs/artbinmountrainier2016.06.05linux64.tgz
tar -xvzf artbinmountrainier2016.06.05linux64.tgz
``` 

If you'd like to use Varsimlabs exome sequencing capabilities, Varsimlab uses Bedtools is required. bedtools documentation is available here (http://bedtools.readthedocs.io/en/latest/) 
to install bedtools 
```
wget https://github.com/arq5x/bedtools2/releases/download/v2.25.0/bedtools-2.25.0.tar.gz
tar -zxvf bedtools-2.25.0.tar.gz
cd bedtools2
make
```



Exome_Script.py [-h] (-use_genome | -bed BED) [-c C] [-s] [-l L] [-m M]
                       [-cnv CNV] [-cnv_min_size CNV_MIN_SIZE]
                       [-cnv_max_size CNV_MAX_SIZE] [-snp SNP] [-indel INDEL]
                       filename genome

positional arguments:
  filename              name of output file
  genome                genome to be processessed

optional arguments:
  -h, --help            show this help message and exit
  -use_genome           generate tumor and normal for entire provided sequence
  -bed BED              generate tumor and normal based on bed file containing
                        exonic regions

read generation parameters:
  arguments to adjust read generation

  -c C                  read depth of coverage
  -s                    use single end reads (default paired)
  -l L                  read length. default 100 bp
  -m M                  maximum distance for two bed ranges to be merged into
                        one range. If zero, merges only those ranges that
                        directly overlap with each other

error parameters:
  arguments to adjust tumor error generation

  -cnv CNV              percent of total input to be incorporated into a CNV.
                        Values from 0 to 100. 4 would signify 4 percent of
                        input should be included in CNVs
  -cnv_min_size CNV_MIN_SIZE
                        minimum size of CNVs
  -cnv_max_size CNV_MAX_SIZE
                        CNV_max_size
  -snp SNP              percent of total input to be turned into SNPs. Values
                        from 0 to 100. A value of 5 indicates 5 percent of
                        genome should be turned into SNPs
  -indel INDEL          percent of total input to be included in INDELS.
                        values from 0 to 100, a value of 1 indicates 1 percent
                        of the genome should be included in indels

