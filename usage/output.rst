Output Files
============

QC Reports
----------

**cnv-plot/Germline_QC_plot.pdf**

Viewing this QC report is the first step in using PatternCNV data. The
plots and heatmap make it easy to identify outliers or batch effects in
your samples. Outlier samples are automatically identified in Figure 2a.
Samples highlighted in red were removed from the PatternCNV coverage
reference. Figure 2b will identify batches within your samples. If clear
batches are identified then the samples should be separated into
different PatternCNV runs.

================================================================================================= ========
|image1|                                                                                          |image2|
================================================================================================= ========
**Figure 2. a)** PatternCNV QC report identifies outliers (left) and **b)** batch effects (right)
================================================================================================= ========

**cnv-plot/Germline_GCcovg_summary_plot.pdf**

This QC report contains various GC content plots.

=====================================================================================
|pcnv_gcplot|
=====================================================================================
**Figure 3.** Per-sample GC content plots help identify samples with strong GC biases
=====================================================================================

Other QC text files:

**cnv-plot/Germline_QC_table.txt**

**cnv-plot/Germline_GC_Covg_table.txt**

**cnv-txt/Germline_CNV_matrix.txt**

**cnv-txt/Germline_pval_matrix.txt**

**cnv-txt/Germline_raw_count_matrix.txt**

**cnv-txt/Germline_RPKM_matrix.txt**


CNV Plots
---------

**cnv-plot/*_CNV.png**

Genome-wide CNV plots are generated for each sample. Each point is an
exon.

================================================================================================================================================
|Q:\external_data\Kocher_Jean-Pierre_m026645\s116183.CNV_SV\TCGA\patternCNV\200bp_exons\cnv-plot\TCGA-29-2431-10A-01D-1526-09(Germline)_CNV.png|
================================================================================================================================================
|Q:\external_data\Kocher_Jean-Pierre_m026645\s116183.CNV_SV\TCGA\patternCNV\200bp_exons\cnv-plot\TCGA-29-2431-01A-01D-1526-09(Somatic)_CNV.png|
**Figure 4. a)** Genome-wide CNV plot for a Germline sample **b)** and its paired tumor sample
================================================================================================================================================

**cnv-plot/*_CNV_seg_.pdf**

This report contains segmentation plots from dnacopy for each sample.
Each black point is an exon.

=====================================================================================================
|image6|
=====================================================================================================
**Figure 5.** An example of a segmentation plot identifying a multi-exon deletion in this chromosome.
=====================================================================================================


CNV tables
----------

**cnv-txt/*_CNV.txt**

These per-sample text files contain CNV information for every exon and
can be used to look-up specific genes, or apply various filters to
identify CNVs:

==== ========= ========= ==== ============= ======== ========
chr  start.pos stop.pos  gene CNV.log2ratio pval     SNR.db
chr1 168510181 168510360 XCL2 -0.0516       0.82822  18.65779
chr1 168510370 168510549 XCL2 0.046209      0.985737 13.113
chr1 168511031 168511200 XCL2 0.083144      0.857714 14.98971
chr1 168511203 168511372 XCL2 0             0.846128 11.75429
chr1 168512942 168513101 XCL2 -0.67518      0.00252  19.32264
chr1 168513107 168513266 XCL2 -2.35306      5.65E-13 13.31741
chr1 168513272 168513431 XCL2 -2.36162      7.94E-10 10.61062
chr1 168545511 168545660 XCL1 0.333074      0.934181 2.005118
chr1 168545668 168545817 XCL1 0.625939      0.244194 8.486324
chr1 168545824 168545973 XCL1 0.657034      0.052004 13.8774
chr1 168545981 168546130 XCL1 0.123819      0.865983 12.20011
chr1 168549101 168549270 XCL1 -0.07947      0.734018 18.31784
==== ========= ========= ==== ============= ======== ========

**cnv-txt/*_CNV_seg_.txt**

These per-sample text files contain the segments identified by dnacopy,
including the number of bins (exons) per segment:

==== ========= ========= ========= =====
Chr  Start     Stop      log2ratio exons
==== ========= ========= ========= =====
chr1 13794     196716760 -0.0003   17302
chr1 196743763 196801446 -7.694    9
chr1 196857029 249214225 -0.0021   4693
==== ========= ========= ========= =====