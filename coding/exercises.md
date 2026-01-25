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
## Exe 6: Hidden Markov Model (HMM) Analysis
I constructed a Profile HMM to identify homologs within the Arabidopsis proteome.

### 1. Methodology
- **Selection**: I filtered the initial BLAST hits for high-confidence sequences with a bit score > 200.
- **MSA**: These sequences were aligned using Clustal Omega to identify conserved domains.
- **Model Building**: I used `hmmbuild` to create a statistical profile (`arf6.hmm`) and `hmmpress` to prepare it for scanning.
- **Scanning**: I ran `hmmscan` against the `uniprot_Atha.fasta` database.

### 2. Results and Analysis
- **Significant Hits**: The scan identified multiple Auxin Response Factors (ARFs) with very low E-values (e.g., ARFN at 4.4e-34 and ARFW at 4.2e-34).
- **Comparison**: While BLAST uses a flat substitution matrix (BLOSUM62), HMMER uses a position-specific approach. This means it weights each position in the alignment differently based on how conserved it is.
- **Conclusion**: The low E-values and high scores in the `exe6_hmm_results.txt` file confirm that the Profile HMM is a robust tool for identifying members of the same protein family, as it captures the "evolutionary signature" of the ARF family better than a standard pairwise search.
- ## Exe 7: 
Based on the HHpred analysis for the Arabidopsis protein AT1G30330.2 (Auxin Response Factor 6, ARF6), the protein contains distinct functional domains and shows high structural similarity to other plant transcription factors and structural models from the Protein Data Bank (PDB)
Domain and Structural Similarity Table
The table below summarizes the domains identified from Pfam and PDB matches, as well as highly similar sequences from the Arabidopsis thaliana proteome as found in the HHpred results.
<img width="848" height="195" alt="image" src="https://github.com/user-attachments/assets/b288b260-9304-4358-ab35-f470c70a0abc" />
## Exe 8: 
What are the GO terms and eggNOG orthology groups of this 
protein? 
The GO of this protein are : 
<img width="479" height="595" alt="image" src="https://github.com/user-attachments/assets/b7e3c3f8-65d7-4669-8b94-60bf0a8f62ce" />

<img width="594" height="461" alt="image" src="https://github.com/user-attachments/assets/f5771053-8775-4608-98a3-60f1fa422018" />

The best taxonomy level found is Brassicales because we get an  e-value of 0 and a score of 
1692.6. That gives us the orthologs below:
<img width="880" height="469" alt="image" src="https://github.com/user-attachments/assets/7790e13e-c13e-47a9-b09d-f4ccd459674b" />

