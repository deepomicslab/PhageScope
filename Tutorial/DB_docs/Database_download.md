# How to download PhageScope datasets

## Phage sequence download
<div align=center><img src="https://github.com/deepomicslab/PhageScope/blob/main/Tutorial/DB_docs/DB_figures/phage_list_download.png" width="800"></div>

Users could be directed to the ``Phage List`` interface by clicking ``Database`` on the navigation bar. On the ``Phage List`` interface, users could scroll through the list of phages or use the ``sequence filter`` to find specific phages.  
 
<div align=center><img src="https://github.com/deepomicslab/PhageScope/blob/main/Tutorial/DB_docs/DB_figures/sequence_filter.png" width="600"></div>

After selecting the phages, please click on the ``Download`` button. A popup would appear, allowing users to choose the desired format for download. Phage sequences and information are provided in **FASTA**, **GFF3**, **GBK**, and **tabular** (Meta data) format. The phage sequences and information will be saved to users' device in the chosen format.  

<div align=center><img src="https://github.com/deepomicslab/PhageScope/blob/main/Tutorial/DB_docs/DB_figures/datatype_selection.png" width="600"></div>

## Batch download 
PhageScope also provides a batch download interface for users to retrieve data, including the phage metadata, protein metadata, transcription terminator metadata, tRNA & tmRNA gene metadata, anti-CRISPR protein metadata, CRISPR array metadata, transmembrane protein metadata, phage sequences in fasta format, protein sequences in fasta format, phage annotations in gbk/gff3 file. Users could click ``Download`` on the navigation bar to enter the download interface.  

<div align=center><img src="https://github.com/deepomicslab/PhageScope/blob/main/Tutorial/DB_docs/DB_figures/download_interface.png" width="1000"></div>

### Meta data download
#### Phage meta data download
+ ``All Phage Meta Data``: The metadata for all the 441,637 phages. Each row gives the information for a phage; The columns give information about phage ID (Phage\_ID), phage genome length (Length), phage GC content (GC\_content), the taxonomy decided by homology (Taxonomy), genome completeness (Completeness), phage host taxonomy (Host), phage lifestyle (Lifestyle), cluster ID (Cluster), subcluster ID (Subcluster), and the phage source dataset (Phage\_source).
+ ``RefSeq Phage Meta Data``: The metadata for the 4,637 phages from RefSeq. 
+ ``Genbank Phage Meta Data``: The metadata for the 2,086 phages from Genbank. 
+ ``EMBL Phage Meta Data``: The metadata for the 156 phages from EMBL. 
+ ``DDBJ Phage Meta Data``: The metadata for the 290 phages from DDBJ. 
+ ``PhagesDB Meta Data``: The metadata for the 3,754 phages from PhagesDB. 
+ ``GPD Phage Meta Data``: The metadata for the 142,809 phages from GPD. 
+ ``GVD Phage Meta Data``: The metadata for the 31,402 phages from GVD. 
+ ``MGV Phage Meta Data``: The metadata for the 189,680 phages from MGV. 
+ ``TemPhD Phage Meta Data``: The metadata for the 66,823 phages from TemPhD. 

#### Annotated protein meta data download
+ ``All Phage Annotated Protein Meta Data``: The metadata for all the 23,424,959 annotated proteins. Each row gives the information for a protein; The columns give information about phage ID (phage\_ID), the annotation source (Protein\_source), the protein start site on the genome (Start), the protein stop site on the genome(Stop), the strand encoding the protein (Strand), protein ID (Protein\_ID), protein product (Product), protein classification with keyword search (Protein\_classification), the molecular mass of protein (Molecular\_weight), the aromaticity value (Aromaticity), the instability index (Instability\_index), the isoelectric point (Isoelectric\_point), the fraction of helix (Helix\_fraction), the fraction of turn (Turn\_fraction), the fraction of sheet (Sheet\_fraction), the molar extinction coefficient assuming cysteines reduced (Reduced\_coefficient), the molar extinction coefficient assuming cystines residues Cys-Cys-bond (Oxidized\_coefficient), and the phage source dataset (Phage\_source).
+ ``RefSeq Phage Annotated Protein Meta Data``: The metadata for the 481,897 annotated proteins from RefSeq.
+ ``Genbank Phage Annotated Protein Meta Data``: The metadata for the 217,870 annotated proteins from Genbank.
+ ``EMBL Phage Annotated Protein Meta Data``: The metadata for the 11,116 annotated proteins from EMBL.
+ ``DDBJ Phage Annotated Protein Meta Data``: The metadata for the 17,391 annotated proteins from DDBJ.
+ ``PhagesDB Phage Annotated Protein Meta Data``: The metadata for the 351,898 annotated proteins from PhagesDB.
+ ``GVD Phage Annotated Protein Meta Data``: The metadata for the 746,146 annotated proteins from GVD.
+ ``GPD Phage Annotated Protein Meta Data``: The metadata for the 7,616,044 annotated proteins from GPD.
+ ``MGV Phage Annotated Protein Meta Data``: The metadata for the 10,517,011 annotated proteins from MGV.
+ ``TemPhD Phage Annotated Protein Meta Data``: The metadata for the 3,465,586 annotated proteins from TemPhD.

#### Transcription terminator meta data download
+ ``All Phage Transcription Terminator Meta Data``: The metadata for all the 3,912,546 transcription terminators. Each row gives the information for a transcription terminator; The columns give information about phage ID (phage\_ID), transcription terminator (Terminator), the terminator start site on the genome (Start), the terminator stop site on the genome (Stop), strand sense (Sense), type of region the terminator is in (Loc) ('G' = in the interior of a gene (at least 50bp from an end), 'F' = between two +strand genes, 'R' = between two -strand genes, 'T' = between the ends of a +strand gene and a -strand gene, 'H' = between the starts of a +strand gene and a -strand gene, 'N' = none of the above (for the start and end of the DNA)), confidence score (Confidence), and the phage source dataset (Phage\_source).
+ ``RefSeq Phage Transcription Terminator Meta Data``: The metadata for the 68,049 transcription terminators from RefSeq.
+ ``Genbank Phage Transcription Terminator Meta Data``: The metadata for the 27,598 transcription terminators from Genbank.
+ ``EMBL Phage Transcription Terminator Meta Data``: The metadata for the 1,728 transcription terminators from EMBL.
+ ``DDBJ Phage Transcription Terminator Meta Data``: The metadata for the 1.638 transcription terminators from DDBJ.
+ ``PhagesDB Phage Transcription Terminator Meta Data``: The metadata for the 36,638 transcription terminators from PhagesDB.
+ ``GVD Phage Transcription Terminator Meta Data``: The metadata for the 130,092 transcription terminators from GVD.
+ ``GPD Phage Transcription Terminator Meta Data``: The metadata for the 1,189,436 transcription terminators from GPD.
+ ``MGV Phage Transcription Terminator Meta Data``: The metadata for the 1,838,272 transcription terminators from MGV.
+ ``TemPhD Phage Transcription Terminator Meta Data``: The metadata for the 619,095 transcription terminators from TemPhD.

#### tRNA & tmRNA gene meta data download
+ ``All Phage tRNA & tmRNA Gene Meta Data``: The metadata for all the 397,896 tRNA & tmRNA genes. Each row gives the information for a t(m)RNA gene; The columns give information about the phage ID (phage\_ID), t(m)RNA ID (t(m)RNA\_ID), the binding amino acid (t(m)RNA), the t(m)RNA start site on the genome (Start), the t(m)RNA stop site on the genome (Stop), the strand (Strand), the length of t(m)RNA (Length), the permuted information (Permuted), the t(m)RNA sequence (Sequence), and the phage source dataset (Phage\_source).
+ ``RefSeq Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 11,821 tRNA & tmRNA genes from RefSeq.
+ ``Genbank Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 4,542 tRNA & tmRNA genes from Genbank.
+ ``EMBL Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 258 tRNA & tmRNA genes from EMBL.
+ ``DDBJ Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 87 tRNA & tmRNA genes from DDBJ.
+ ``PhagesDB Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 10,544 tRNA & tmRNA genes from PhagesDB.
+ ``GVD Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 10,152 tRNA & tmRNA genes from GVD.
+ ``GPD Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 147,068 tRNA & tmRNA genes from GPD.
+ ``MGV Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 196,688 tRNA & tmRNA genes from MGV.
+ ``TemPhD Phage tRNA & tmRNA Gene Meta Data``: The metadata for the 16,736 tRNA & tmRNA genes from TemPhD.

#### Anti-CRISPR protein meta data download
+ ``All Phage Anti-CRISPR Protein Meta Data``: The metadata for all the 251,994 anti-CRISPR proteins. Each row gives the information for an anti-CRISPR protein; The columns give information about the phage ID (phage\_ID), protein ID (Protein\_ID), annotation source (Source), and the phage source dataset (Phage\_source).
+ ``RefSeq Phage Anti-CRISPR Protein Meta Data``: The metadata for the 115,648 anti-CRISPR proteins from RefSeq.
+ ``Genbank Phage Anti-CRISPR Protein Meta Data``: The metadata for the 54,849 anti-CRISPR proteins from Genbank.
+ ``EMBL Phage Anti-CRISPR Protein Meta Data``: The metadata for the 2,807 anti-CRISPR proteins from EMBL.
+ ``DDBJ Phage Anti-CRISPR Protein Meta Data``: The metadata for the 4,803 anti-CRISPR proteins from DDBJ.
+ ``PhagesDB Phage Anti-CRISPR Protein Meta Data``: The metadata for the 48 anti-CRISPR proteins from PhagesDB.
+ ``GVD Phage Anti-CRISPR Protein Meta Data``: The metadata for the 5,260 anti-CRISPR proteins from GVD.
+ ``GPD Phage Anti-CRISPR Protein Meta Data``: The metadata for the 30,617 anti-CRISPR proteins from GPD.
+ ``MGV Phage Anti-CRISPR Protein Meta Data``: The metadata for the 30,125 anti-CRISPR proteins from MGV.
+ ``TemPhD Phage Anti-CRISPR Protein Meta Data``: The metadata for the 7,837 anti-CRISPR proteins from TemPhD.

#### CRISPR array meta data download
+ ``All Phage CRISPR Array Meta Data``: The metadata for all the 32,472 CRISPR arrays. Each row gives the information for a CRISPR array; The columns give information about the Phage\_ID, Duplicated\_Spacers, CRISPR\_ID, CRISPR\_Start, CRISPR\_End, CRISPR\_Length, Potential\_Orientation (AT%), CRISPRDirection Consensus\_Repeat, Repeat\_ID (CRISPRdb), Nb\_CRISPRs\_with\_same\_Repeat (CRISPRdb), Repeat\_Length, Spacers\_Nb, Mean\_size\_Spacers, Standard\_Deviation\_Spacers, Nb\_Repeats\_matching\_Consensus, Ratio\_Repeats\_match/TotalRepeat, Conservation\_Repeats (% identity), EBcons\_Repeats, Conservation\_Spacers (% identity), EBcons\_Spacers  Repeat\_Length\_plus\_mean\_size\_Spacers, Ratio\_Repeat/mean\_Spacers\_Length, CRISPR\_found\_in\_DB (if sequence IDs are similar), Evidence\_Level, and Phage\_source.
+ ``RefSeq Phage CRISPR Array Meta Data``: The metadata for the 523 CRISPR arrays from RefSeq. 
+ ``Genbank Phage CRISPR Array Meta Data``: The metadata for the 245 CRISPR arrays from Genbank. 
+ ``EMBL Phage CRISPR Array Meta Data``: The metadata for the 17 CRISPR arrays from EMBL. 
+ ``DDBJ Phage CRISPR Array Meta Data``: The metadata for the 30 CRISPR arrays from DDBJ. 
+ ``PhagesDB Phage CRISPR Array Meta Data``: The metadata for the 294 CRISPR arrays from PhagesDB. 
+ ``GVD Phage CRISPR Array Meta Data``: The metadata for the 1,373 CRISPR arrays from GVD. 
+ ``GPD Phage CRISPR Array Meta Data``: The metadata for the 9,448 CRISPR arrays from GPD. 
+ ``MGV Phage CRISPR Array Meta Data``: The metadata for the 16,096 CRISPR arrays from MGV. 
+ ``TemPhD Phage CRISPR Array Meta Data``: The metadata for the 4,446 CRISPR arrays from TemPhD. 

#### Transmembrane protein meta data download
+ ``All Phage Transmembrane Protein Meta Data``: The metadata for all the 2,189,636 transmembrane proteins. Each row gives the information for a transmembrane protein; The columns give information about the Phage\_ID, Protein\_ID, Length, PredictedTMHsNumber, ExpnumberofAAsinTMHs, Expnumberfirst60AAs, TotalprobofNin, POSSIBLENterm, Insidesource, Insidestart, Insideend, TMhelixsource, TMhelixstart, TMhelixend, Outsidesource, Outsidestart, Outsideend, and Phage\_source.
+ ``RefSeq Phage Transmembrane Protein Meta Data``: The metadata for the 43,567 transmembrane proteins from RefSeq. 
+ ``Genbank Phage Transmembrane Protein Meta Data``: The metadata for the 20,549 transmembrane proteins from Genbank. 
+ ``EMBL Phage Transmembrane Protein Meta Data``: The metadata for the 1,023 transmembrane proteins from EMBL. 
+ ``DDBJ Phage Transmembrane Protein Meta Data``: The metadata for the 1,559 transmembrane proteins from DDBJ. 
+ ``PhagesDB Phage Transmembrane Protein Meta Data``: The metadata for the 32,227 transmembrane proteins from PhagesDB. 
+ ``GVD Phage Transmembrane Protein Meta Data``: The metadata for the 80,967 transmembrane proteins from GVD. 
+ ``GPD Phage Transmembrane Protein Meta Data``: The metadata for the 741,785 transmembrane proteins from GPD. 
+ ``MGV Phage Transmembrane Protein Meta Data``: The metadata for the 830,363 transmembrane proteins from MGV. 
+ ``TemPhD Phage Transmembrane Protein Meta Data``: The metadata for the 437,596 transmembrane proteins from TemPhD.

## FASTA file download
### Phage FASTA file download
+ ``RefSeq Phage FASTA File``: Phage sequences from RefSeq in FASTA format.
+ ``Genbank Phage FASTA File``: Phage sequences from Genbank in FASTA format.
+ ``EMBL Phage FASTA File``: Phage sequences from EMBL in FASTA format.
+ ``DDBJ Phage FASTA File``: Phage sequences from DDBJ in FASTA format.
+ ``PhagesDB Phage FASTA File``: Phage sequences from PhagesDB in FASTA format.
+ ``GPD Phage FASTA File``: Phage sequences from GPD in FASTA format.
+ ``GVD Phage FASTA File``: Phage sequences from GVD in FASTA format.
+ ``MGV Phage FASTA File``: Phage sequences from MGV in FASTA format.
+ ``TemPhD Phage FASTA File``: Phage sequences from TemPhD in FASTA format.

### Protein FASTA file download 
+ ``RefSeq Protein FASTA File``: Protein sequences from RefSeq in FASTA format.
+ ``Genbank Protein FASTA File``: Protein sequences from Genbank in FASTA format.
+ ``EMBL Protein FASTA File``: Protein sequences from EMBL in FASTA format.
+ ``DDBJ Protein FASTA File``: Protein sequences from DDBJ in FASTA format.
+ ``PhagesDB Protein FASTA File``: Protein sequences from PhagesDB in FASTA format.
+ ``GPD Protein FASTA File``: Protein sequences from GPD in FASTA format.
+ ``GVD Protein FASTA File``: Protein sequences from GVD in FASTA format.
+ ``MGV Protein FASTA File``: Protein sequences from MGV in FASTA format.
+ ``TemPhD Protein FASTA File``: Protein sequences from TemPhD in FASTA format.

## GBK file download
### Phage GBK file download
+ ``RefSeq Phage GBK File``: Phage annotations from RefSeq in GBK format.
+ ``Genbank Phage GBK File``: Phage annotations from Genbank in GBK format.
+ ``EMBL Phage GBK File``: Phage annotations from EMBL in GBK format.
+ ``DDBJ Phage GBK File``: Phage annotations from DDBJ in GBK format.
+ ``PhagesDB Phage GBK File``: Phage annotations from PhagesDB in GBK format.
+ ``GPD Phage GBK File``: Phage annotations from GPD in GBK format.
+ ``GVD Phage GBK File``: Phage annotations from GVD in GBK format.
+ ``MGV Phage GBK File``: Phage annotations from MGV in GBK format.
+ ``TemPhD Phage GBK File``: Phage annotations from TemPhD in GBK format.

## GFF3 file download
### Phage GFF3 File Download
+ ``RefSeq Phage GFF3 File``: Phage annotations from RefSeq in GFF3 format.
+ ``Genbank Phage GFF3 File``: Phage annotations from Genbank in GFF3 format.
+ ``EMBL Phage GFF3 File``: Phage annotations from EMBL in GFF3 format.
+ ``DDBJ Phage GFF3 File``: Phage annotations from DDBJ in GFF3 format.
+ ``PhagesDB Phage GFF3 File``: Phage annotations from PhagesDB in GFF3 format.
+ ``GPD Phage GFF3 File``: Phage annotations from GPD in GFF3 format.
+ ``GVD Phage GFF3 File``: Phage annotations from GVD in GFF3 format.
+ ``MGV Phage GFF3 File``: Phage annotations from MGV in GFF3 format.
+ ``TemPhD Phage GFF3 File``: Phage annotations from TemPhD in GFF3 format.

## Database API download
PhageScope also allows API download with ``phage_ID``, ``protein_ID``, and ``data source``.
