Chromatin State Maps in Mouse
##############################

First, we collected mapped ChIP-Seq reads of H3K4me1, H3K4me3, H3K36me3, H3K27me3, H3K27ac, CTCF and R
NA polymerase II from ENCODE http://hgdownload.cse.ucsc.edu/goldenPath/mm9/encodeDCC/wgEncodeLicrHistone/. 
This data was originally produced from mouse (C57BL/6-strain, E14 or 8 week-old) brain, heart, kidney, liver, 
small intestine, spleen, testes, thymus and embryonic stem (ES) cell line. Second, we used a Poisson-based 
multivariate hidden Markov model29 (ChromHMM) to identify regions or states enriched in specific combinations of 
histone modifications as described previously but without extension of the reads. Third, after testing models from 
a 2-state model to a 50-state model, we decided to use the 15-state model, which allowed us to interpret the 
chromatin frequency observed across various tissues and cell lines. This resulted in the six major chromatin states 
of active promoter, poised promoter, strong enhancer, poised or weak enhancer, insulator, repressed, transcribed and 
heterochromatin states. In total, 3,612,616 regions in the mouse genome were enriched with at least one of the six 
major chromatin states.

These were the following commands that were used to generate maps of chromatin states in mouse

1. java -jar ChromHMM.jar BinarizeBed CHROMSIZES/mm9.txt mm9EncodeHMM/ mm9EncodeHMM/cellmarkfile mm9EncodeHMM_BinaryOutput/

2. java -jar ChromHMM.jar LearnModel mm9EncodeHMM_BinaryOutput/ mm9EncodeHMM_Output15/ 15 mm9 