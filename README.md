# Introduction

Varsimlab is a command line python pieline designed to easily generate artificial genome or exome sequences, with structural and copy number variations. Using ART short read simulation and SInC error generation, Varsimlab can quickly simulate biologically realistic tumor and normal short reads

# Setup and Dependencies 

Varsimlab uses art_illumina to generate short reads with realistic sequencing errors. The documentation is available [here](https://www.niehs.nih.gov/research/resources/software/biostatistics/art/index.cfm)

To install ART 
``` curl -O https://www.niehs.nih.gov/research/resources/assets/docs/artbinmountrainier2016.06.05linux64.tgz
tar -xvzf artbinmountrainier2016.06.05linux64.tgz
``` 

VarSimLab uses SInC simulator to generate biologically realistic tumor genomic variations. The source files are available [here](https://sourceforge.net/projects/sincsimulator/files/?source=navbar)


Varsimlab can be called from the command line using python 3

Lastly if you'd like to use Varsimlabs exome sequencing capabilities, Varsimlab uses Bedtools is required. bedtools documentation is available [here](http://bedtools.readthedocs.io/en/latest/) 

To install bedtools 
```
wget https://github.com/arq5x/bedtools2/releases/download/v2.25.0/bedtools-2.25.0.tar.gz
tar -zxvf bedtools-2.25.0.tar.gz
cd bedtools2
make
```

# Quick Start Guide 
### genome sequence usage
To simulate tumor and normal reads for a genome sequence Varsimlab requires 3 arguments 
1. A name for the output file which will contain tumor and normal reads
2. The reference sequence you are interested in simulating
3. the flag -use_genome 

References for the human genome can be found online [here](https://genome.ucsc.edu/cgi-bin/hgGateway?db=hg38)

an example usecase 
``` python3 Exome_Script.py output_directory ~/chr20.fa -use_genome
```
### exome sequence usage
To simulate tumor and normal reads for a exome sequence, Varsimlab requires the following
1. A name for the output file which will contain tumor and normal reads
2. The reference sequence you are interested in simulating
3. -bed argument, followed by the path to a bed file containing the positions of the exonic regions of your sequence 

That last part might sound daunting but fortunately UCSC tablebrowser makes it easy. The website can be found [here](https://genome.ucsc.edu/cgi-bin/hgTables?hgsid=677064941_DieH2qjeHz0zB8ElNBfAc4ojENCa)
and here is an explanatory video from USCS that may be helpful 
<a href="http://www.youtube.com/watch?feature=player_embedded&v=6JoUqM1iKxQ
" target="_blank"><img src="http://img.youtube.com/vi/6JoUqM1iKxQ/0.jpg" 
alt="Exome bed file explanatory video" width="240" height="180" border="10" /></a>
6JoUqM1iKxQ

# Available Arguments
to see this guide on the command line, type 
``` python3 Exome_Script.py -h ```
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

