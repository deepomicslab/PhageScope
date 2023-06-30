# Welcome to PhageScope analysis

![image](https://github.com/deepomicslab/PhageScope/blob/main/Figures/analysis.png)

## Analysis description
PhageScope analysis module includes **single genome annotation** and **multiple genome comparison**. Genome annotation includes **completeness assessment**, **phenotype annotation** (host assignment and lifestyle prediction), **structural annotation** (ORF prediction, protein classification, and transcription terminator annotation), **functional annotation** (tRNA & tmRNA gene annotation, anti-CRISPR protein annotation, CRISPR array annotation, and transmembrane protein annotation). Genome comparison includes **sequence clustering**, **sequence alignment**, and **phylogenetic tree construction**.

### Input
The only inputs users need to provide are phage sequences in **FASTA format**. Users could choose to upload a FASTA file (with single or multiple phage sequences), enter the phage ID from PhageScope database, or paste the sequences in the text field.

### Genome annotation
Users have the flexibility to perform either **single** or **multiple** analyses based on their specific research needs and objectives. 

#### Completeness assessment
Phage completeness refers to the extent of sequencing and assembly achieved for a phage genome. This module utilizes **CheckV** [1] with default hyperparameters to estimate the sequence completeness of phage genomes based on the reference genome length. The module returns the phage sequence completeness as complete, **high-quality**, **medium-quality**, **low-quality**, or **not-determined**. This information provides insights into the quality and completeness of the submitted phages.

#### Phenotype annotation
+ Host assignment: Host information reveals the organisms that phages infect or interact with. This module uses **BLASTN** [2] to align phage sequences with a local nucleotide database consisting of phages with annotated host information, along with **DeepHost** [3], a tool predicting phage host with a convolutional neural network, to deal with those sequences without BLAST hits. The module outputs the **host information with its full taxonomy rank** [4].
+ Lifestyle prediction: This module is performed via **Graphage** [5] and outputs **the predicted lifestyle** (temperate or virulent).
These annotations enable researchers to identify potential targets for phage therapies and study the coevolution between phages and hosts.

#### Structural annotation
+ ORF prediction & protein classification: This module focuses on the prediction and annotation of genetic elements within phage genomes. Open Reading Frames (ORFs), areas of DNA with the potential to be translated into proteins, are identified using **Prodigal** [6]; Protein functions are then assigned using **eggNOG-mapper** [7] and categorized into ten types, including **lysis**, **integration**, **replication**, **tRNA-related**, **regulation**, **packaging**, **assembly**, **infection**, **immune**, and **hypothetical**, via keyword searches. The module output the annotated sequences in gff format, the protein sequences in fasta format, and the protein metadata.
+ Transcription terminator annotation: This module predicts transcription terminators using **TransTermHP** [8] and returns the predicted terminators with their location information and confidence score.

These annotations provide valuable insights into the genome structure, genetic content, and functional diversity encoded in phage genomes.  

#### Functional annotation
+ tRNA & tmRNA genes: tRNA and tmRNA genes, essential for protein synthesis and quality control, respectively, are detected using **ARAGORN** [9].
+ Anti-CRISPR protein annotation: The presence and diversity of anti-CRISPR proteins, viral proteins that inhibit CRISPR-Cas systems, are identified using a combination of **BLASTP** [2] and **AcRanker** [10]. For BLASTP, we gathered the anti-CRISPR proteins from the **Anti-CRISPRdb** [11] to create a nucleotide database. The module returns the proteins with an e-value below 1e-5 and a coverage of over 90%. For Acranker, only candidate proteins that ranked higher than at least 50% of the proteins from Anti-CRISPRdb are considered as anti-CRISPR proteins.
+ CRISPR array annotation: CRISPR arrays, characteristic features of bacterial genomes, are identified using **CRISPRCasFinder** [12].
+ Transmembrane protein annotation: Transmembrane proteins, which span cell membranes, are detected using **TMHMM** [13].

These modules return the identified items, along with their related information, such as locations, confidence scores, and molecular types. The annotations reveal crucial information about phage-host interactions, potential mechanisms of phage evasion, and exploitation of host cellular processes.  

### Genome comparison
The genome comparison analysis module of PhageScope allows users to compare and analyze multiple phage genomes. It provides various analysis and visualization functions to explore the genetic variations and evolutionary relationships among these genomes.  

#### Sequence clustering
This module groups phage genomes based on their sequence similarity with **MMseqs2** [14], identifying clusters of phages that share common genetic characteristics. ``min-seq-id 0.9`` and ``-c 0.9`` are required to form **subclusters**, and the representative sequences for subclusters are grouped into **clusters** with the hyperparameters ``min-seq-id 0.6`` and ``-c 0.75``.

#### Sequence alignment
This module compares the protein sequences of multiple phage genomes to identify regions of similarity. The **protein sequences from the annotation files** are extracted and compare with each other with **BLASTP** [2]. The **alignment identity and coverage** are returned for visualization. This analysis helps in locating conserved regions, detecting sequence variations, and finding potential functional elements.

#### Phylogenetic tree construction
This module constructs a phylogenetic tree that represents the evolutionary relationships between the phage genomes. **Alfpy** [15] is applied to calculate the genome distance between the input sequences and **neighbor joining algorithm** [16] is applied for phylogenetic reconstruction. The module returns the phylogenetic tree in **newick format**. The tree provides a visual representation of their genetic relatedness, allowing researchers to study the phage's evolutionary history and track the divergence and convergence of different phage lineages.

## Citation
[1] Nayfach S, Camargo A P, Schulz F, et al. CheckV assesses the quality and completeness of metagenome-assembled viral genomes[J]. Nature biotechnology, 2021, 39(5): 578-585.  
[2] Altschul S F, Gish W, Miller W, et al. Basic local alignment search tool[J]. Journal of molecular biology, 1990, 215(3): 403-410.  
[3] Ruohan W, Xianglilan Z, Jianping W, et al. DeepHost: phage host prediction with convolutional neural network[J]. Briefings in Bioinformatics, 2022, 23(1): bbab385.   
[4] Federhen S. The NCBI taxonomy database[J]. Nucleic acids research, 2012, 40(D1): D136-D143.  
[5] WANG R, Ng Y K, Zhang X, et al. A graph representation of gapped patterns in phage sequences for graph convolutional network[J]. bioRxiv, 2022: 2022.08. 22.504727.   
[6] Hyatt D, Chen G L, LoCascio P F, et al. Prodigal: prokaryotic gene recognition and translation initiation site identification[J]. BMC bioinformatics, 2010, 11(1): 1-11.  
[7] Cantalapiedra C P, Hernandez-Plaza A, Letunic I, et al. eggNOG-mapper v2: functional annotation, orthology assignments, and domain prediction at the metagenomic scale[J]. Molecular biology and evolution, 2021, 38(12): 5825-5829.  
[8] Ermolaeva M D, Khalak H G, White O, et al. Prediction of transcription terminators in bacterial genomes[J]. Journal of molecular biology, 2000, 301(1): 27-33.  
[9] Laslett D, Canback B. ARAGORN, a program to detect tRNA genes and tmRNA genes in nucleotide sequences[J]. Nucleic acids research, 2004, 32(1): 11-16.  
[10] Eitzinger S, Asif A, Watters K E, et al. Machine learning predicts new anti-CRISPR proteins[J]. Nucleic acids research, 2020, 48(9): 4698-4708.  
[11] Dong C, Hao G F, Hua H L, et al. Anti-CRISPRdb: a comprehensive online resource for anti-CRISPR proteins[J]. Nucleic acids research, 2018, 46(D1): D393-D398.  
[12] Couvin D, Bernheim A, Toffano-Nioche C, et al. CRISPRCasFinder, an update of CRISRFinder, includes a portable version, enhanced performance and integrates search for Cas proteins[J]. Nucleic acids research, 2018, 46(W1): W246-W251.  
[13] Krogh A, Larsson B, Von Heijne G, et al. Predicting transmembrane protein topology with a hidden Markov model: application to complete genomes[J]. Journal of molecular biology, 2001, 305(3): 567-580.  
[14] Steinegger M, S?ding J. MMseqs2 enables sensitive protein sequence searching for the analysis of massive data sets[J]. Nature biotechnology, 2017, 35(11): 1026-1028.  
[15] Zielezinski A, Vinga S, Almeida J, et al. Alignment-free sequence comparison: benefits, applications, and tools[J]. Genome biology, 2017, 18: 1-17.  
[16] Saitou N, Nei M. The neighbor-joining method: a new method for reconstructing phylogenetic trees[J]. Molecular biology and evolution, 1987, 4(4): 406-425.  
