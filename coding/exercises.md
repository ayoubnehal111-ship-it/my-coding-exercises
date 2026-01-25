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
## Exe 5: PSI-BLAST Profile Analysis
I ran PSI-BLAST for 3 iterations to generate a sequence profile (PSSM).

- **Observation:** The search **CONVERGED** after 2 rounds. This indicates that no additional significant sequences were found in the database that weren't already included in the profile model.
- **Results:** - Round 1 Score: 159 bits (E-value: 1e-58).
  - Round 2 Score: 152 bits (E-value: 8e-56).
- **Explanation of profile.out (PSSM):**
  The generated `profile.out` file contains the **Position-Specific Scoring Matrix**. Unlike a standard BLOSUM62 matrix, this PSSM is specifically tailored to the ARF6 sequence. It assigns scores to each of the 20 amino acids at every position of the 77-residue sequence based on the evolutionary conservation observed during the iterations.
