# biofilm

This repository contains the code used for to analyze the biofilm microbiota data in Tomkovich et al.

The samples were separated by mouse genotype: ApcMin IL10 KO (IL10) and ApcMin (Apc). Within each genotype, we have stool, DC tissue and inoculum. 

Within the inputTables directory,  DCMetadata.txt contains the metadata for the DC tissue samples. StoolMetadata.txt contains the metdata for the stool samples and inocula. The files in the RDP folder contain the raw counts at each taxonomic level, as determined by RDP version 2.2. The files in the qiimeClosedRef folder contain the raw counts using QIIME version 1.9.1 with the pick_closed_reference_otus function. The files in the qiimeDeNovo folder contain the raw counts using QIIME version 1.9.1 with the pick_de_novo_otus function. Files whose name starts with "rdp_" or "biofilm_" contain the raw counts for all samples at each taxonomic level. The files whose name starts with "dc_" contain the raw counts for just the DC tissue samples. The files whose name starts with "stool_" contain the raw counts for just the stool samples. RDP was run on the forward and reverse reads separately; only the forward reads are used in most analyses. QIIME was run on stitched reads. 

Use (in the Apc folder) apcDCMetadataLogNormalize or apcStoolMetadataLogNormalize to add metadata and log normalize the Apc DC or stool samples respectively, with and without the inoculum included. Like, use (in the ApcIL10 folder) il10DCMetadataLogNormalize or il10StoolMetadataLogNormalize to add metadata and log normalize the ApcIL10 DC or stool samples respectively, with and without the inoculum included. To run this code, you will need to modify the working directory to be the directory you want to write your results to, which should include DCMetadata.txt and StoolMetadata.txt. This line is the second line of code, and is currently written: setwd(""). Put the directory name in these quotes. Set rdpdatadir to be the directory where you put the files the RDP inputTables folder (fill in the quotes with the file path). Likewise, set denovodir to be the directory containing the contents of the qiimeDeoNovo inputTables folder and set closedrefdir to be the directory containing the contents of the qiimeClosedRef directory. Currently, these three directories are set to be folders in the working directory. Be sure to include the file separator at the end of the directory name for these variables (\\ for Windows or / for Linux).

For all other R code, you will also need to modify the working directory to be the same directory you wrote the log normalized results to. As above, put this directory name in the quotes in the setwd command (usually the second line of code).

############
##Analyses##
############
For each type of genotype, there were two sets of groups:
        4 groups: (BF-bx, BF+bx, BF+NF, BF+T)
        2 groups: (BF- versus BF+ (combination of all 3 BF+ groups)
Only include the following timepoints: 0 (inoculum), 1 week (stools), and 12 week  (stool & DC tissue)

Model used for stool: taxa ~ time + group + 1|cage/mouse
Model used for DC tissue: taxa ~ group + 1|cage 

Apc genotype (Apc folder):
1. apcAnalysis1_pcoa.R.txt-> generates 4 different PCoAs:
   a. Stool & inoculums from 4 groups
   b. DC tissue & inoculums from 4 groups
   c. Stool from 2* groups both timepoints (1 & 12 week) *only sequenced stool from BF-bx & BF+T Apc mice
   d. DC tissue from 4 groups
2. apcAnalysis2_OTUModel_stool.R.txt and apcAnalysis2_OTUModel_dc.R.txt-> Boxplots/p value tables of individual taxa for stool & DC tissue, respectively (4 groups)
3. apcAnalysis3_heatmap.R.txt-> Heatmap of top significant genera from inoculum, stool (1&12 week combined) & DC tissue
4. apcAnalysis4_indiv_stool_pcoa.R.txt-> 4 individual group PCoAs: Stool samples (1 & 12 week) showing how microbiotas changed over time
5. apcAnalysis5_diversity.R.txt-> Shannon diversity & richness (4 groups)
6. apcAnalysis6_pcoa_anosim_2group.R.txt-> PCoA with ANOSIM: 2 groups (BF- versus BF+ combined) for stool (1 & 12 wk) & DC tissue

ApcIl10 genotype (ApcIL10 folder):
1. il10Analysis1_pcoa.R.txt-> generates 4 different PCoAs:
   a. Stool & inoculums from 4 groups
   b. DC tissue & inoculums from 4 groups
   c. Stool from 4 groups both timepoints (1 & 12 week)
   d. DC tissue from 4 groups
2. il10Analysis2_OTUModel_stool.R.txt and il10Analysis2_OTUModel_dc.R.txt->Boxplots/p value tables of individual taxa for stool & DC tissue, respectively (4 groups)
3. il10Analysis3_heatmap.R.txt->Heatmap of top significant genera from inoculum, stool (1&12 week combined) & DC tissue
4. il10Analysis4_indiv_stool_pcoa.R.txt->4 individual group PCoAs: Stool samples (1 & 12 week) showing how microbiotas changed over time
5. il10Analysis5_diversity.R.txt->Shannon diversity & richness (4 groups)
6. il10Analysis6_pcoa_anosim_2group.R.txt->PCoA with ANOSIM: 2 groups (BF- versus BF+ combined) for stool (1 & 12 wk) & DC tissue

heatmapCombined.R.txt (in Apc folder)-> combines all of the heatmaps (Apc and IL10 inoculum, DC and stool) into one figure
