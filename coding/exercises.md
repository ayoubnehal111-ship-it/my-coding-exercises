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
