Installation and Dependencies
=============================

The following Tools and R Packages need to be installed on the user’s
system in order to use PatternCNV:

======== =============================== ==================
**Tool** **Download link**               **Tested Version**
======== =============================== ==================
Samtools http://www.htslib.org           1.0
Bedtools http://bedtools.readthedocs.org 2.20.1
R        https://www.r-project.org       3.1.1
Perl     https://www.perl.org            5.10.1
======== =============================== ==================

The following R packages are required, but can be easily installed using
the PatternCNV install script:

cd patterncnv_code_dir/

Rscript install_R_packages.R

=========== ================================================================
**Package** **Link**
=========== ================================================================
DNAcopy     http://www.bioconductor.org/packages/2.12/bioc/html/DNAcopy.html
fdrtool     http://cran.r-project.org/web/packages/fdrtool/index.html
gplots      http://cran.r-project.org/web/packages/gplots/index.html
matrixStats http://cran.r-project.org/web/packages/matrixStats/index.html
RCurl       https://cran.r-project.org/web/packages/RCurl/index.html
=========== ================================================================

Usage and Options
=================

USAGE:

./patternCNV_wrapper.sh [options] -c config.txt > patternCNV.log 2>&1

OPTIONS:

-c config.txt config file (required)

-b 10 Bin size used to determine resolution of coverage. Default: 10

-m 20 Minimum mapping quality of reads to use for coverage

calculation. Default: 20

-z 1000 Size of exons that should be split into multiple exons.

Default: 1000

-x 100 Extension buffer size defining size each exon should be

extended on both sides. Default: 100

-s Run patternCNV in serial mode, not submitting any jobs to

an sge cluster. Default: Parallel mode

-n Don't merge overlapping exons. Default: Merge

-v Verbose logs for debugging

-j Optional comma separated list of job IDs for PatternCNV to

wait on (qsub -hold_jid).

-w Optional prefix to use in job names (qsub -N)

-u Optional suffix to use in job names (qsub -N)

-l Optional path to logs folder if user doesn't want to use

the default location

-d Debug mode. Keeps exon bed and bam2wig intermediate files.

-h print out this help message


Input Files
===========

config.txt
----------

Config.txt is a text file containing the following variables:

OUTPUT_DIR=/path/to/output/dir/

SAMPLE_INFO=/path/to/sample_info.txt

CAPTUREKIT_BED=/path/to/capture_kit_regions.bed

EXON_BED=/path/to/exon_regions.bed

GENOME_SIZE=/path/to/contig/sizes/human_37.1.genome

GENOME_REF=/path/to/reference/sequence/hg19.fa

PATTERNCNV=/path/to/patterncnv/code/

SAMTOOLS=/path/to/samtools

BEDTOOLS=/path/to/bedtools/bin

R=/path/to/R/bin

EMAIL=email@email.com

QUEUE=1-day

QSUB_EXONKEY_MEMORY=-l h_vmem=4G -l h_stack=10M

QSUB_BAM2WIG_MEMORY=-l h_vmem=2G -l h_stack=10M

QSUB_CALLCNVS_MEMORY=-l h_vmem=4G -l h_stack=10M


sample_info.txt
---------------

The sample_info.txt file is a tab delimited text file defining sample
names, group names for tumor/normal pairs, whether a sample is Germline
or Somatic, and paths to BAM files. The header line is required:

sample.name subject.ID sample.type batch.ID BAM.file

sampleid1 sampleid1 Germline 1 /path/to/sampleid1.bam

sampleid2 sampleid2 Germline 1 /path/to/sampleid2.bam

sampleid3 sampleid3 Germline 1 /path/to/sampleid3.bam

sample1_blood pair1 Germline 1 /path/to/sample1_blood.bam

sample1_tumor pair1 Somatic 1 /path/to/sample1_tumor.bam


Capture kit BED file
--------------------

A 3 column BED file defining the regions targeted by the capture kit:

chr1 10000 10200

chr1 11000 11200

...


Exon BED file
-------------

A 4 column BED file defining the exon regions, with the 4\ :sup:`th`
column being the gene name. PatternCNV will use a union of the capture
kit BED and the exon BED when calling CNVs:

chr1 24737 24891 WASH7P

chr1 29320 29370 WASH7P

chr1 34610 35174 FAM138A

chr1 34610 35174 FAM138F

...


BAMs
----

BAM files for each sample are listed in the sample_info.txt file. Each
BAM files must be aligned and sorted.