

# Session 1: Annotation of coding sequences

## Exe1: Database Formatting
I formatted the `uniprot_Atha.fasta` database. 
- **Results**: About 16,000 sequences were processed.
- **E-value**: As the database size increases, the E-value for a given match also increases because the probability of finding such an alignment by chance is higher.

## Exe2: Output Redirection
The BLAST results were redirected to files:
- `test.faa.blast`
- `test.fna.blast`

## Exe3: Default Format
The default format is `outfmt 0` (pairwise alignment).

## Exe4: Results Comparison
`blastp` and `blastx` produce similar results, but `blastx` allows searching with DNA by translating it into protein first.

## Exe5: PSI-BLAST Profile
The `profile.out` file contains a PSSM (Position-Specific Scoring Matrix) that reflects the conservation of amino acids at each position.
# Session 1: Annotation of coding sequences

## Exe1: Database Formatting
I formatted the `uniprot_Atha.fasta` database using `makeblastdb`
- **Number of sequences**: Approximately 16,000 sequences were formatted.
- **Impact on E-value**: The E-value is proportional to the database size. As the number of sequences in the database increases, the E-value for any given alignment also increases because the probability of finding a match by chance is higher.
## Exe2: Redirecting Output
I redirected the output to separate files called `test.faa.blast` and `test.fna.blast` using the `-out` flag.

## Exe3: Default Alignment Format
The default alignment format is **Pairwise** (`outfmt 0`). 
Example of pairwise alignment:
Query  1  MRLSSAGFNPQPHEVTGEKRVLNSELWHACAGPLVSLPPVGSRVVYFPQG  50
          MRLSSAGFNPQPHEVTGEKRVLNSELWHACAGPLVSLPPVGSRVVYFPQG
Sbjct  1  MRLSSAGFNPQPHEVTGEKRVLNSELWHACAGPLVSLPPVGSRVVYFPQG  50

## Exe4: Differences in Results
The results in both searches are essentially the same because `blastx` translates the transcript into protein before searching. The main difference is that `blastp` is faster as it skips the translation step.
## Exe 5: PSI-BLAST Profile Analysis
I used PSI-BLAST with 3 iterations to create a Position-Specific Scoring Matrix (PSSM).
- **File Content**: The `profile.out` file contains the PSSM for the ARF6 protein.
- **Explanation**: This matrix provides a score for each of the 20 amino acids at every position in the query sequence. High scores indicate conserved positions, while low scores indicate positions that vary across homologs. This profile is more sensitive than a standard BLAST search because it captures the evolutionary "signature" of the protein family.
