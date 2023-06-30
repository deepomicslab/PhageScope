# Welcome to PhageScope database

![image](https://github.com/deepomicslab/PhageScope/blob/main/Figures/database.png)

## Data description
PhageScope database contains **441,637** phage sequences from various sources, including **4,637** sequences from **RefSeq** [1], **2,086** sequences from **Genbank** [2], **156** sequences from **EMBL** [3], **290** sequences from **DDBJ** [4], **3,754** sequences from **PhagesDB** [5], **31,402** sequences from **GVD** [6], **142,809** sequences from **GPD** [7], **189,680** sequences from MGV [8], and **66,823** sequences from **TemPhD** [9].   

Applying multiple state-of-the-art tools to analysing the phage sequences, we obtained **comprehensive annotations** for the phages.

### Phage completeness
Phage completeness refers to the extent to which a phage genome has been sequenced and assembled. The quality and completeness of the collected phages vary considerably.  

We applied **CheckV** [10] to the phage sequences, which estimates the sequence completeness according to the reference genome length. According to the CheckV results, 39,133 sequences are **complete** (100% completeness), 135,684 sequences with **high-quality** (>90% completeness), 162,196 sequences with **medium-quality** (50-90% completeness), 90,048 sequences with **low-quality** (0-50% completeness), with the remaining 14,576 sequences not-determined.

### Host information
Host information indicates the organism(s) that a phage is known to infect or interact with. Knowing the host range of phage can help researchers identify potential targets for phage therapies or study the coevolution between phages and their hosts.  

Among the 441,367 phages, the host information of **297,768** phages is available from the data submitters. We used these phage sequences to create a local nucleotide database and aligned other phages with the database via **BLASTN** [11], adhering to a stringent e-value threshold of less than 1e-5 to narrow down the matches to the most reliable results. The host taxonomy of the hit with the lowest e-value was returned as the predicted taxonomy for **110,201** phages. For the rest **33,668** phages, we employed **DeepHost** [12], a tool predicting phage host via a convolutional neural network, with the model retrained from phages with given host annotation. We provided the whole taxonomy ranks for the host with the information from **NCBI taxonomy database** [13]. 

### Phage lifestyle
Phage lifestyle refers to the way in which a phage interacts with its host organism. It can be classified as either lytic or temperate. Lytic phages infect and rapidly lyse (destroy) the host cells to release progeny phages, while temperate phages can switch between a lytic and a lysogenic cycle, integrating their genetic material into the host genome. Understanding the phage lifestyle helps in predicting the potential impact of phages on their host organisms and studying the mechanisms underlying their interactions.  

The phages from the TemPhD dataset are temperate phages according to their phage mining pipeline. As for the remaining phages, we utilized **Graphage** [14], which integrates sequence information and 206 lysogeny-associated proteins to predict their phage lifestyle. Overall, the PhageScope database consists of **268,879 virulent phages** and **172,758 temperate** phages.

### ORF & annotated protein
ORF stands for Open Reading Frame and represents a region of DNA that has the potential to be translated into a protein. In PhageScope, Information about ORFs and annotated proteins provides insights into the predicted genes and their corresponding proteins within the phage genomes. These annotations are crucial for understanding the genetic content of phages, identifying potential virulence factors, and exploring the functional diversity encoded in their genomes.  

The phage sequences from RefSeq, Genbank, EMBL, and DDBJ come with these genetic features annotated. For the phages sourced from PhagesDB, GVD, GPD, MGV, and TemPhD, we first applied **Prodigal** [15] to identify the ORFs and obtained **23,424,959** proteins, and then employed **eggNOG-mapper** [16] to annotate the protein functions by assigning orthology. The proteins were categorized into ten types, including **lysis (643,820)**, **integration (575,847)**, **replication (1,271,047)**, **tRNA-related (38,305)**, **regulation (674,983)**, **packaging (706,058)**, **assembly (1,796,929)**, **infection (1,129,476)**, **immune (210,687)**, and **hypothetical (5,388,986)**, based on key word searches.

### Terminators
Terminators are specific DNA sequences that indicate the end of a gene or a functional genetic region. The annotation of terminators provides information about the locations where the genes or functional regions within the phage genomes end. This information is valuable for accurately determining the boundaries of genes, regulatory regions, or other functional elements in the phage genomes.  

We employed **TransTermHP** [17] to predict transcription terminators within the phage genomes, resulting in a comprehensive collection of **3,912,546** terminators derived from the phage sequences.

### tRNA & tmRNA genes
tRNA and tmRNA genes encode RNA molecules that play essential roles in protein synthesis and quality control, respectively. The identification and annotation of tRNA and tmRNA genes indicate the presence of these functional elements within the phage genomes. By studying these genes, users can gain insights into the phage's ability to manipulate the host's protein synthesis machinery and potentially identify mechanisms to evade host defenses or manipulate host cellular functions.  

We applied **ARAGORN** [18] to detect tRNA and tmRNA genes in phage sequences, leading to the delineation of **391,743 tRNA** genes (**329** different tRNA molecules) and **6,153 tmRNA genes**. 

### Anti-CRISPR proteins
Anti-CRISPR proteins are viral proteins that can inhibit the activity of CRISPR-Cas systems, which are bacterial defense mechanisms against phage infections. The annotation of anti-CRISPR proteins provides information on the presence and diversity of such proteins within the phage genomes. Understanding these proteins can shed light on the coevolutionary arms race between phages and bacteria and potentially offer insights into the development of strategies to overcome bacterial CRISPR-mediated immunity.  

To obtain comprehensive Anti-CRISPR annotations, we incorporate multiple tools to identify anti-CRISPR proteins from the PhageScope database. We first collected the anti-CRIPSR proteins from **Anti-CRISPRdb** [19] to create a local nucleotide database and aligned phage protein sequences with the database via **BLASTP** [11], with stringent criteria for reliable alignment (e-value < 1e-5 and coverage > 90%) employed to identify anti-CRISPR proteins.  

To expand the search for novel anti-CRISPR proteins, we also incorporated **AcRanker** [20], a machine learning tool, to predict novel anti-CRISPR proteins. AcRanker assigns a rank to candidate proteins based on their likelihood of being an anti-CRISPR protein. To ensure confidence in the annotations, only candidate proteins ranking higher than at least 50% of the proteins from Anti-CRISPRdb were considered as annotated anti-CRISPR proteins.  

By integrating these methodologies, a total of **251,994** anti-CRISPR proteins were identified within the phage genomes. Among these, **21,987** proteins were identified through the alignment-based method, **229,851** proteins were identified using AcRanker, and the remaining proteins were identified satisfying both criteria. 

### CRISPR arrays
CRISPR array is a characteristic feature of bacterial genomes and acts as an adaptive immune system against phages and other foreign nucleic acids. The annotation of CRISPR arrays indicates the presence of these arrays within the phage genomes associated with bacteria. This information helps in understanding the interplay between phages and bacterial immune systems, identifying potential sources of phage resistance, and studying the dynamics of phage-bacteria coevolution.  

In order to investigate the CRISPR array contained within the PhageScope database, **CRISPRCasFinder** [21] was employed with the objective of identifying the clustered regularly interspaced short palindromic repeats (CRISPRs) present in the phage sequences. The resulting collection of **32,472** CRISPR arrays, accompanied by their **corresponding spacer information**, has been made available within the PhageScope database.

### Transmembrane proteins
Transmembrane proteins are proteins that span the lipid bilayer of cell membranes. The annotation of transmembrane proteins provides information on the presence and characteristics of such proteins within the phage genomes. These annotations offer insights into the potential interactions between phages and host cell membranes, their roles in phage infection and release, and the exploitation of host cellular processes by phages.  

We applied **TMHMM** [22] to the phage protein sequences from the PhageScope database. A total of **2,189,636** proteins were identified as helical membrane proteins, exhibiting **1-48 transmembrane helices**. The resultant set of transmembrane proteins, coupled with their corresponding **topology information**, has been made accessible through the PhageScope database.

## Citation
[1] O'Leary N A, Wright M W, Brister J R, et al. Reference sequence (RefSeq) database at NCBI: current status, taxonomic expansion, and functional annotation[J]. Nucleic acids research, 2016, 44(D1): D733-D745.  
[2] Benson D A, Cavanaugh M, Clark K, et al. GenBank[J]. Nucleic acids research, 2018, 46(Database issue): D41.  
[3] Kanz C, Aldebert P, Althorpe N, et al. The EMBL nucleotide sequence database[J]. Nucleic acids research, 2005, 33(suppl\_1): D29-D33.  
[4] Ogasawara O, Kodama Y, Mashima J, et al. DDBJ Database updates and computational infrastructure enhancement[J]. Nucleic acids research, 2020, 48(D1): D45-D50.  
[5] Russell D A, Hatfull G F. PhagesDB: the actinobacteriophage database[J]. Bioinformatics, 2017, 33(5): 784-786.  
[6] Gregory A C, Zablocki O, Zayed A A, et al. The gut virome database reveals age-dependent patterns of virome diversity in the human gut[J]. Cell host & microbe, 2020, 28(5): 724-740. e8.   
[7] Camarillo-Guerrero L F, Almeida A, Rangel-Pineros G, et al. Massive expansion of human gut bacteriophage diversity[J]. Cell, 2021, 184(4): 1098-1109. e9.  
[8] Nayfach S, Paez-Espino D, Call L, et al. Metagenomic compendium of 189,680 DNA viruses from the human gut microbiome[J]. Nature microbiology, 2021, 6(7): 960-970.  
[9] Zhang X, Wang R, Xie X, et al. Mining bacterial NGS data vastly expands the complete genomes of temperate phages[J]. NAR Genomics and Bioinformatics, 2022, 4(3): lqac057.  
[10] Nayfach S, Camargo A P, Schulz F, et al. CheckV assesses the quality and completeness of metagenome-assembled viral genomes[J]. Nature biotechnology, 2021, 39(5): 578-585.  
[11] Altschul S F, Gish W, Miller W, et al. Basic local alignment search tool[J]. Journal of molecular biology, 1990, 215(3): 403-410.  
[12] Ruohan W, Xianglilan Z, Jianping W, et al. DeepHost: phage host prediction with convolutional neural network[J]. Briefings in Bioinformatics, 2022, 23(1): bbab385.  
[13] Federhen S. The NCBI taxonomy database[J]. Nucleic acids research, 2012, 40(D1): D136-D143.
[14] WANG R, Ng Y K, Zhang X, et al. A graph representation of gapped patterns in phage sequences for graph convolutional network[J]. bioRxiv, 2022: 2022.08. 22.504727.  
[15] Hyatt D, Chen G L, LoCascio P F, et al. Prodigal: prokaryotic gene recognition and translation initiation site identification[J]. BMC bioinformatics, 2010, 11(1): 1-11.    
[16] Cantalapiedra C P, Hernandez-Plaza A, Letunic I, et al. eggNOG-mapper v2: functional annotation, orthology assignments, and domain prediction at the metagenomic scale[J]. Molecular biology and evolution, 2021, 38(12): 5825-5829.  
[17] Ermolaeva M D, Khalak H G, White O, et al. Prediction of transcription terminators in bacterial genomes[J]. Journal of molecular biology, 2000, 301(1): 27-33.  
[18] Laslett D, Canback B. ARAGORN, a program to detect tRNA genes and tmRNA genes in nucleotide sequences[J]. Nucleic acids research, 2004, 32(1): 11-16.  
[19] Dong C, Hao G F, Hua H L, et al. Anti-CRISPRdb: a comprehensive online resource for anti-CRISPR proteins[J]. Nucleic acids research, 2018, 46(D1): D393-D398.  
[20] Eitzinger S, Asif A, Watters K E, et al. Machine learning predicts new anti-CRISPR proteins[J]. Nucleic acids research, 2020, 48(9): 4698-4708.  
[21] Couvin D, Bernheim A, Toffano-Nioche C, et al. CRISPRCasFinder, an update of CRISRFinder, includes a portable version, enhanced performance and integrates search for Cas proteins[J]. Nucleic acids research, 2018, 46(W1): W246-W251.  
[22] Krogh A, Larsson B, Von Heijne G, et al. Predicting transmembrane protein topology with a hidden Markov model: application to complete genomes[J]. Journal of molecular biology, 2001, 305(3): 567-580.
