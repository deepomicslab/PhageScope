# Welcome to PhageScope database

![image](https://github.com/deepomicslab/PhageScope/blob/main/Figures/database.png)

## Data description
PhageScope database contains **873,718** phage sequences from various sources, including **4,637** sequences from **RefSeq** [1], **2,086** sequences from **Genbank** [2], **156** sequences from **EMBL** [3], **290** sequences from **DDBJ** [4], **3,754** sequences from **PhagesDB** [5], **195,699** sequences from **GOV2** [6], **31,402** sequences from **GVD** [7], **142,809** sequences from **GPD** [8], **189,680** sequences from **MGV** [9], **44,935** sequences from **CHVD** [10], **4,065** sequences from **STV** [11], **66,823** sequences from **TemPhD** [12], **10,021** sequences from **IGVD** [13], **177,361** sequences from **IMG/VR** [14].   

Applying multiple state-of-the-art tools to analysing the phage sequences, we obtained **comprehensive annotations** for the phages.

### Phage completeness
Phage completeness refers to the extent to which a phage genome has been sequenced and assembled. The quality and completeness of the collected phages vary considerably.  

We applied **CheckV** [15] to the phage sequences, which estimates the sequence completeness according to the reference genome length. According to the CheckV results, 72,668 sequences are **complete** (100% completeness), 300,137 sequences with **high-quality** (>90% completeness), 212,175 sequences with **medium-quality** (50-90% completeness), 267,050 sequences with **low-quality** (0-50% completeness), with the remaining 21,688 sequences not-determined.

### Host information
Host information indicates the organism(s) that a phage is known to infect or interact with. Knowing the host range of phage can help researchers identify potential targets for phage therapies or study the coevolution between phages and their hosts.  

Among the 873,718 phages, the host information of **530,085** phages is available from the data submitters. We used these phage sequences to create a local nucleotide database and aligned other phages with the database via **BLASTN** [16], adhering to a stringent e-value threshold of less than 1e-5 to narrow down the matches to the most reliable results. The host taxonomy of the hit with the lowest e-value was returned as the predicted taxonomy for **124,446** phages. For the rest **219,187** phages, we employed **DeepHost** [17], a tool predicting phage host via a convolutional neural network, with the model retrained from phages with given host annotation. We provided the whole taxonomy ranks for the host with the information from **NCBI taxonomy database** [18]. 

### Phage lifestyle
Phage lifestyle refers to the way in which a phage interacts with its host organism. It can be classified as either lytic or temperate. Lytic phages infect and rapidly lyse (destroy) the host cells to release progeny phages, while temperate phages can switch between a lytic and a lysogenic cycle, integrating their genetic material into the host genome. Understanding the phage lifestyle helps in predicting the potential impact of phages on their host organisms and studying the mechanisms underlying their interactions.  

The phages from the TemPhD dataset are temperate phages according to their phage mining pipeline. As for the remaining phages, we utilized **Graphage** [19], which integrates sequence information and 206 lysogeny-associated proteins to predict their phage lifestyle. Overall, the PhageScope database consists of **553,688 virulent phages** and **320,030 temperate** phages.

### ORF & annotated protein
ORF stands for Open Reading Frame and represents a region of DNA that has the potential to be translated into a protein. In PhageScope, Information about ORFs and annotated proteins provides insights into the predicted genes and their corresponding proteins within the phage genomes. These annotations are crucial for understanding the genetic content of phages, identifying potential virulence factors, and exploring the functional diversity encoded in their genomes.  

The phage sequences from RefSeq, Genbank, EMBL, and DDBJ come with these genetic features annotated. For the phages sourced from PhagesDB, GVD, GPD, MGV, and TemPhD, we first applied **Prodigal** [20] to identify the ORFs and obtained **43,088,582** proteins, and then employed **eggNOG-mapper** [21] to annotate the protein functions by assigning orthology. For proteins that lacked hits, we iteratively applied **mmseqs** [22] to detect homology from the PHROG database [23], and then annotated the proteins with the functional information from the homology. The proteins were categorized into ten types, including **lysis**, **integration**, **replication**, **tRNA-related**, **regulation**, **packaging**, **assembly**, **infection**, **immune**, and **hypothetical**, based on key word searches.

### Terminators
Terminators are specific DNA sequences that indicate the end of a gene or a functional genetic region. The annotation of terminators provides information about the locations where the genes or functional regions within the phage genomes end. This information is valuable for accurately determining the boundaries of genes, regulatory regions, or other functional elements in the phage genomes.  

We employed **TransTermHP** [24] to predict transcription terminators within the phage genomes, resulting in a comprehensive collection of **6,462,417** terminators derived from the phage sequences.  

### Taxonomy
To determine the taxonomic classification for phages, 30,553 taxonomy-specific VOGs from eight taxonomical groups were selected as the marker genes. For each phage, we applied HMMsearch to align its encoded proteins to the VOGs and assigned it to the taxonomical group with the most HMM hits.  

### tRNA & tmRNA genes
tRNA and tmRNA genes encode RNA molecules that play essential roles in protein synthesis and quality control, respectively. The identification and annotation of tRNA and tmRNA genes indicate the presence of these functional elements within the phage genomes. By studying these genes, users can gain insights into the phage's ability to manipulate the host's protein synthesis machinery and potentially identify mechanisms to evade host defenses or manipulate host cellular functions.  

We applied **ARAGORN** [25] and **tRNAscan-SE** [26] to detect tRNA and tmRNA genes in phage sequences, leading to the delineation of **691,091 tRNA** genes and **11,516 tmRNA genes**. 

### Anti-CRISPR proteins
Anti-CRISPR proteins are viral proteins that can inhibit the activity of CRISPR-Cas systems, which are bacterial defense mechanisms against phage infections. The annotation of anti-CRISPR proteins provides information on the presence and diversity of such proteins within the phage genomes. Understanding these proteins can shed light on the coevolutionary arms race between phages and bacteria and potentially offer insights into the development of strategies to overcome bacterial CRISPR-mediated immunity.  

To obtain comprehensive Anti-CRISPR annotations, we incorporate multiple tools to identify anti-CRISPR proteins from the PhageScope database. We first collected the anti-CRIPSR proteins from **Anti-CRISPRdb** [27] to create a local nucleotide database and aligned phage protein sequences with the database via **mmseqs** [22], with stringent criteria for reliable alignment (identity > 80% and coverage > 40%) employed to identify anti-CRISPR proteins.  

To expand the search for novel anti-CRISPR proteins, we also incorporated **AcRanker** [28], a machine learning tool, to predict novel anti-CRISPR proteins. AcRanker assigns a rank to candidate proteins based on their likelihood of being an anti-CRISPR protein. To ensure confidence in the annotations, only candidate proteins ranking higher than at least 50% of the proteins from Anti-CRISPRdb were considered as annotated anti-CRISPR proteins.  

By integrating these methodologies, a total of **307,329** anti-CRISPR proteins were identified within the phage genomes.

### CRISPR arrays
CRISPR array is a characteristic feature of bacterial genomes and acts as an adaptive immune system against phages and other foreign nucleic acids. The annotation of CRISPR arrays indicates the presence of these arrays within the phage genomes associated with bacteria. This information helps in understanding the interplay between phages and bacterial immune systems, identifying potential sources of phage resistance, and studying the dynamics of phage-bacteria coevolution.  

In order to investigate the CRISPR array contained within the PhageScope database, **CRISPRCasFinder** [29] was employed with the objective of identifying the clustered regularly interspaced short palindromic repeats (CRISPRs) present in the phage sequences. The resulting collection of **56,652** CRISPR arrays, accompanied by their **corresponding spacer information**, has been made available within the PhageScope database.

### Virulent factors and Antimicrobial resistance genes
The identification of virulent factors and antimicrobial resistance genes is essential for understanding the pathogenicity and antimicrobial susceptibility patterns of microorganisms.  

We employed **mmseqs** [22] to conduct homology search for the phage proteins against **VFDB** [30] and **CARD** [31]. Virulence factor or antimicrobial resistance genes are identified on phage genomes if the match meets the thresholds of > 80% identity and > 40% coverage, which results in **41,609** virulent factors and **2,602** antimicrobial resistance genes.  

### Transmembrane proteins
Transmembrane proteins are proteins that span the lipid bilayer of cell membranes. The annotation of transmembrane proteins provides information on the presence and characteristics of such proteins within the phage genomes. These annotations offer insights into the potential interactions between phages and host cell membranes, their roles in phage infection and release, and the exploitation of host cellular processes by phages.  

We applied **TMHMM** [32] to the phage protein sequences from the PhageScope database. A total of **4,020,770** proteins were identified as helical membrane proteins, exhibiting **1-48 transmembrane helices**. The resultant set of transmembrane proteins, coupled with their corresponding **topology information**, has been made accessible through the PhageScope database.

### Comparative genomic studies
Comparative genomic studies, including sequence clustering, sequence alignment, and comparative tree construction, are also provided for the curated phages.


## Citation
[1] O'Leary N A, Wright M W, Brister J R, et al. Reference sequence (RefSeq) database at NCBI: current status, taxonomic expansion, and functional annotation[J]. Nucleic acids research, 2016, 44(D1): D733-D745.  
[2] Benson D A, Cavanaugh M, Clark K, et al. GenBank[J]. Nucleic acids research, 2018, 46(Database issue): D41.  
[3] Kanz C, Aldebert P, Althorpe N, et al. The EMBL nucleotide sequence database[J]. Nucleic acids research, 2005, 33(suppl\_1): D29-D33.  
[4] Ogasawara O, Kodama Y, Mashima J, et al. DDBJ Database updates and computational infrastructure enhancement[J]. Nucleic acids research, 2020, 48(D1): D45-D50.  
[5] Russell D A, Hatfull G F. PhagesDB: the actinobacteriophage database[J]. Bioinformatics, 2017, 33(5): 784-786.  
[6] Gregory A C, Zayed A A, Concei??o-Neto N, et al. Marine DNA viral macro-and microdiversity from pole to pole[J]. Cell, 2019, 177(5): 1109-1123. e14.  
[7] Gregory A C, Zablocki O, Zayed A A, et al. The gut virome database reveals age-dependent patterns of virome diversity in the human gut[J]. Cell host & microbe, 2020, 28(5): 724-740. e8.   
[8] Camarillo-Guerrero L F, Almeida A, Rangel-Pineros G, et al. Massive expansion of human gut bacteriophage diversity[J]. Cell, 2021, 184(4): 1098-1109. e9.  
[9] Nayfach S, Paez-Espino D, Call L, et al. Metagenomic compendium of 189,680 DNA viruses from the human gut microbiome[J]. Nature microbiology, 2021, 6(7): 960-970.  
[10] Tisza M J, Buck C B. A catalog of tens of thousands of viruses from human metagenomes reveals hidden associations with chronic diseases[J]. Proceedings of the National Academy of Sciences, 2021, 118(23): e2023202118.  
[11] Santos-Medellin C, Zinke L A, Ter Horst A M, et al. Viromes outperform total metagenomes in revealing the spatiotemporal patterns of agricultural soil viral communities[J]. The ISME journal, 2021, 15(7): 1956-1970.  
[12] Zhang X, Wang R, Xie X, et al. Mining bacterial NGS data vastly expands the complete genomes of temperate phages[J]. NAR Genomics and Bioinformatics, 2022, 4(3): lqac057.  
[13] Shah S A, Deng L, Thorsen J, et al. Expanding known viral diversity in the healthy infant gut[J]. Nature Microbiology, 2023: 1-13.  
[14] Camargo A P, Nayfach S, Chen I M A, et al. IMG/VR v4: an expanded database of uncultivated virus genomes within a framework of extensive functional, taxonomic, and ecological metadata[J]. Nucleic acids research, 2023, 51(D1): D733-D743.  
[15] Nayfach S, Camargo A P, Schulz F, et al. CheckV assesses the quality and completeness of metagenome-assembled viral genomes[J]. Nature biotechnology, 2021, 39(5): 578-585.  
[16] Altschul S F, Gish W, Miller W, et al. Basic local alignment search tool[J]. Journal of molecular biology, 1990, 215(3): 403-410.  
[17] Wang R, Zhang X, Wang J, et al. DeepHost: phage host prediction with convolutional neural network[J]. Briefings in Bioinformatics, 2022, 23(1): bbab385.  
[18] Federhen S. The NCBI taxonomy database[J]. Nucleic acids research, 2012, 40(D1): D136-D143.i 
[19] WANG R, Ng Y K, Zhang X, et al. A graph representation of gapped patterns in phage sequences for graph convolutional network[J]. bioRxiv, 2022: 2022.08. 22.504727.  
[20] Hyatt D, Chen G L, LoCascio P F, et al. Prodigal: prokaryotic gene recognition and translation initiation site identification[J]. BMC bioinformatics, 2010, 11(1): 1-11.    
[21] Cantalapiedra C P, Hernandez-Plaza A, Letunic I, et al. eggNOG-mapper v2: functional annotation, orthology assignments, and domain prediction at the metagenomic scale[J]. Molecular biology and evolution, 2021, 38(12): 5825-5829.  
[22] Steinegger M, Sding J. MMseqs2 enables sensitive protein sequence searching for the analysis of massive data sets[J]. Nature biotechnology, 2017, 35(11): 1026-1028.  
[23] Terzian P, Olo Ndela E, Galiez C, et al. PHROG: families of prokaryotic virus proteins clustered using remote homology[J]. NAR Genomics and Bioinformatics, 2021, 3(3): lqab067. 
[24] Ermolaeva M D, Khalak H G, White O, et al. Prediction of transcription terminators in bacterial genomes[J]. Journal of molecular biology, 2000, 301(1): 27-33.  
[25] Laslett D, Canback B. ARAGORN, a program to detect tRNA genes and tmRNA genes in nucleotide sequences[J]. Nucleic acids research, 2004, 32(1): 11-16.  
[26] Lowe T M, Eddy S R. tRNAscan-SE: a program for improved detection of transfer RNA genes in genomic sequence[J]. Nucleic acids research, 1997, 25(5): 955-964.  
[27] Dong C, Hao G F, Hua H L, et al. Anti-CRISPRdb: a comprehensive online resource for anti-CRISPR proteins[J]. Nucleic acids research, 2018, 46(D1): D393-D398.  
[28] Eitzinger S, Asif A, Watters K E, et al. Machine learning predicts new anti-CRISPR proteins[J]. Nucleic acids research, 2020, 48(9): 4698-4708.  
[29] Couvin D, Bernheim A, Toffano-Nioche C, et al. CRISPRCasFinder, an update of CRISRFinder, includes a portable version, enhanced performance and integrates search for Cas proteins[J]. Nucleic acids research, 2018, 46(W1): W246-W251.  
[30] Chen L, Yang J, Yu J, et al. VFDB: a reference database for bacterial virulence factors[J]. Nucleic acids research, 2005, 33(suppl\_1): D325-D328.  
[31] McArthur A G, Waglechner N, Nizam F, et al. The comprehensive antibiotic resistance database[J]. Antimicrobial agents and chemotherapy, 2013, 57(7): 3348-3357.  
[32] Krogh A, Larsson B, Von Heijne G, et al. Predicting transmembrane protein topology with a hidden Markov model: application to complete genomes[J]. Journal of molecular biology, 2001, 305(3): 567-580.  
