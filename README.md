# biofilm

This repository contains the code used for to analyze the biofilm microbiota data in Tomkovich et al.

The samples were separated by mouse genotype: ApcMin IL10 KO (referred to as IL10) and ApcMin (referred to as Apc). Within each genotype, we have stool, DC tissue and inoculum.

Groups: 4 groups: (BF-bx, BF+bx, BF+NF, BF+T)
                2 groups: (BF- versus BF+ (combination of all 3 BF+ groups)
-Only include the following timepoints: 0 (inoculum), 1 week (stools), and 12 week  (stool & DC tissue)

Model used for stool: bug~time+group + 1|cage/mouse
Model used for DC tissue: bug~group+1|cage 

Apc genotype:
1. PCoAs: 
   a. Stool & inoculums from 4 groups
   b. DC tissue & inoculums from 4 groups
   c. Stool from 2* groups both timepoints (1 & 12 week) *only sequenced stool from BF-bx & BF+T Apc mice
   d. DC tissue from 4 groups
2. Boxplots/p value tables of individual taxa for stool & DC tissue (4 groups)
3. Heatmap of top significant genera from inoculum, stool (1&12 week combined) & DC tissue
4. 4 individual group PCoAs: Stool samples (1 & 12 week) showing how microbiotas changed over time
5. Shannon Diversity & richness: 4 groups
6. PCoA with ANOSIM: 2 groups (BF- versus BF+ combined) for stool (1 & 12 wk) & DC tissue

ApcIl10 genotype:
1. PCoAs: 
   a. Stool & inoculums from 4 groups
   b. DC tissue & inoculums from 4 groups
   c. Stool from 4 groups both timepoints (1 & 12 week)
   d. DC tissue from 4 groups
2. Boxplots/p value tables of individual taxa for stool & DC tissue (4 groups)
3. Heatmap of top significant genera from inoculum, stool (1&12 week combined) & DC tissue
4. 4 individual group PCoAs: Stool samples (1 & 12 week) showing how microbiotas changed over time
5. Shannon Diversity & richness: 4 groups
6. PCoA with ANOSIM: 2 groups (BF- versus BF+ combined) for stool (1 & 12 wk) & DC tissue
