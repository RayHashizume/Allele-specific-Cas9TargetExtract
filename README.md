# Allele-specific-SpCas9 Targets Extract

This simple shell script code detects allele-specific SpCas9 recognition sequences on chromosome 21 in trisomy 21 cells. Four whole genome sequencing (WGS) bam files will be used as inputs: a trisomy 21 cell bam file, and bam files of three strains of induced disomy 21 with each chromosome 21 eliminated (delta-P, delta-M1, and delta-M2). In addition, a working directory and a reference sequence (fasta-formatted) must be specified. All the above should be specified with full paths. It is assumed that GRCh38 is used as the reference sequence. 

## 1.	System Requirements:
 - macOS 13.4.1 (Apple Silicon M1)
 - zsh (v5.9)

## 2.	Dependencies:
- [pv (v1.6.20)](http://www.ivarch.com/programs/pv.shtml)
- [ripgrep (v13.0.0)](https://github.com/BurntSushi/ripgrep)
- [BSD awk (v20200816)](https://www.freebsd.org)
- [samtools (v1.18)](https://github.com/samtools/)
- [blastn (v2.14.0+)](https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/)
- [gsed (v4.9)](https://formulae.brew.sh/formula/gnu-sed)

## 3.	Input:

- Full path ot the aligned/sorted WGS BAM files for the trisomy 21, delta-P disomy 21, delta-M1 disomy 21, and delta-M2 disomy 21 cells.
- Full path to the working directory
- Full path to the reference fasta file (build GRCh38)
- Target allele subject to the extraction of specific Cas9 recognition sequences (specified by P, M1, or M2)


## 5.	Output: 
The result is a text file with 13 columns. Each column means the following; SpCas9_recognition_seq
| Column | Contents |
|:-----:|---------------|
|     1|SpCas9_recognition_seq|
|     2|Number_of_reads_in_the_trisomy.bam|
|     3|Number_of_reads_in_the_dP.bam|
|     4|Number_of_reads_in_the_dM1.bam|
|     5|Number_of_reads_in_the_dM2.bam|
|     6|Minimal_number_of_reads_in_target_allele-included_bam.file|
|     7|Number_of_1_mismatch_reads_in_target-allele-excluded_bam.file|
|     8|Contig_in_the_reference|
|     9|Position|
|     10|Strand_direction|
|     11|Bit_score|
|     12|Reference_name|
|     13|Location_category|



## 6. Modification for personalized runs:
Open the shell script in a text editor and replace the required fields with the full path.  
Save changes before run.
 

#====================================================================================  
T21bam=`Absolute_path_to_trisomy21_bam_file`  
dPbam=`Absolute_path_to_deltaP_bam_file`  
dM1bam=`Absolute_path_to_deltaM1_bam_file`  
dM2bam=`Absolute_path_to_deltaM2_bam_file`  
Dir=`Absolute_path_to_working_directory`  
Ref=`Absolute_path_to_genome_reference_fasta_file`  
Allele=`Target_allele_(P,M1,M2)`  
#====================================================================================  


## 7.	Run script
```
sh ./TargetExtract.sh
```
