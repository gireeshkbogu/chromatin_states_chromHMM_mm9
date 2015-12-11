
Author: Gireesh Bogu

Date: Dec 1st 2013

Email: gireesh.bogu@crg.eu


### Citation: Chromatin and RNA Maps Reveal Regulatory Long Noncoding RNAs in Mouse, MCB -(In Revision)



#### How I generated chromatin state maps in mouse (mm9) in few lines:


First, I collected mapped ChIP-Seq reads of H3K4me1, H3K4me3, H3K36me3, H3K27me3, H3K27ac, CTCF and RNA polymerase II from ENCODE http://hgdownload.cse.ucsc.edu/goldenPath/mm9/encodeDCC/wgEncodeLicrHistone/. This data was originally produced from mouse (C57BL/6-strain, E14 or 8 week-old) brain, heart, kidney, liver, small intestine, spleen, testes, thymus and embryonic stem (ES) cell line as a part of mouse ENCODE project. 

Second, I used a Poisson-based multivariate hidden Markov model (ChromHMM) to identify regions or states enriched in specific combinations of histone modifications as described previously but without extension of the reads. 

Third, after testing models from a 2-state model to a 50-state model, we decided to use the 15-state model, which allowed me to interpret the chromatin frequency observed across various tissues and cell lines. 

This resulted in the six major chromatin states of active promoter, poised promoter, strong enhancer, poised or weak enhancer, insulator, repressed, transcribed and heterochromatin states. In total, 3,612,616 regions in the mouse genome were enriched with at least one of the six major chromatin states.

These were the following commands that were used to generate maps of chromatin states in mouse


1. java -jar ChromHMM.jar BinarizeBed CHROMSIZES/mm9.txt mm9EncodeHMM/ mm9EncodeHMM/cellmarkfile mm9EncodeHMM_BinaryOutput/

2. java -jar ChromHMM.jar LearnModel mm9EncodeHMM_BinaryOutput/ mm9EncodeHMM_Output15/ 15 mm9 


References:

1. A map of the cis-regulatory sequences in the mouse genome, Nature, 2012, Yin Shen,	Feng Yue,	David F. McCleary,	Zhen Ye,	Lee Edsall,	Samantha Kuan,	Ulrich Wagner,	Jesse Dixon,	Leonard Lee,	Victor V. Lobanenkov	& Bing Ren

Data source: http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE29184

2. ChromHMM: automating chromatin-state discovery and characterization, Nature methods, 2012, Jason Ernst	& Manolis Kellis

Software link: http://compbio.mit.edu/ChromHMM/


2. 
