cat <<EOF > coding/exercises.md
# Session 1: Annotation of coding sequences

## Exe1: Database Formatting
I formatted the \`uniprot_Atha.fasta\` database.
- **Number of sequences:** 15,719 sequences were formatted.
- **Impact on E-value:** The size of the database directly affects the E-value. As the database becomes larger, the E-value for a given match increases. This is because a larger search space makes it more likely to find a high-scoring alignment by pure chance.
EOF
## Exe2: Output Redirection
I redirected the BLAST results into separate files:
- `test.faa.blast` (Protein search)
- `test.fna.blast` (Transcript search)

## Exe3: Default Alignment Format
The default format is **Pairwise** (Option 0). It shows the amino acid sequences of the Query and Subject aligned on top of each other.

## Exe4: Differences in Results
- **blastp hits:** 100
- **blastx hits:** 95
- **Observation:** `blastp` found more hits in this specific search. This is expected as `blastx` must translate the DNA query into 6 frames, which can affect the alignment sensitivity.
