# Session 5: Mapping and variant calling
## Exercise 1
### 1.1 Note that there are 2 FASTQ files with the same name but different numeric suffix, why?
There are two FASTQ files because the sequencing was performed using paired-end sequencing.
The file ending with _1.fastq.gz contains the forward reads (read 1), while the file ending with _2.fastq.gz contains the reverse reads (read 2) from the same DNA fragments.
Each pair of reads corresponds to opposite ends of the same fragment, which improves alignment accuracy and variant detection.

### 1.2 Check first SAMEA2569438.chr10_1.fastq.gz and then SAMEA2569438.chr10_2.fastq.gz, can you spot * the difference? Do you recognize the typical FASTQ format of these files?
When comparing SAMEA2569438.chr10_1.fastq.gz and SAMEA2569438.chr10_2.fastq.gz, the main difference is that they contain reads from opposite ends of the same DNA fragments (read 1 and read 2).
The read identifiers are similar but indicate whether the read is the first or second in the pair.
Both files follow the standard FASTQ format, where each sequencing read is described using four lines: a header line, the nucleotide sequence, a plus sign line, and a line containing the quality scores.

### 1.3 Are read starts and ends similar in terms of error rate?
We can clearly observe in the figure below that the error rate is low at the beginning of the reads and increases toward the end of the reads. The quality scores are high at the start and gradually decrease as the read position increases, indicating a higher error rate near the end of the reads. This pattern is typical of Illumina sequencing data.
<img width="867" height="388" alt="image" src="https://github.com/user-attachments/assets/fbd695e0-3a7e-4535-bf02-edd8db7d4886" />
