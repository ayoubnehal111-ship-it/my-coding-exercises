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
The default format is **Pairwise** (Option 0). It shows the amino acid sequences of the Query and Subject aligned on top of each other

For example : 

 <img width="862" height="357" alt="image" src="https://github.com/user-attachments/assets/16468ddd-de10-4535-8c1d-63f3055c96d4" />


## Exe4: Differences in Results
- **blastp hits:** 100
- **blastx hits:** 95
- **Observation:** `blastp` found more hits in this specific search. This is expected as `blastx` must translate the DNA query into 6 frames, which can affect the alignment sensitivity.
## Exe 5: PSI-BLAST Profile Analysis
The profile.out file contains the Position-Specific Scoring Matrix (PSSM), a mathematical "fingerprint" that identifies the evolutionary patterns of the ARF6 protein family. Each row represents a sequence position where positive scores, like the 8 for Histidine at position 13, highlight highly conserved amino acids essential for biological function. The matrix uses log-odds scores to show which residues are favored or penalized at each spot across the 136,324 sequences in your database. Because your search yielded a 100% identity match, the scores are currently very specific to your query sequence. Finally, statistical parameters like Lambda and K at the bottom allow BLAST to calculate the statistical significance of your matches, such as your extremely low 4e-48 E-value. 
<img width="742" height="378" alt="{0F2B72E1-291F-4603-BC5A-CB212DCAD982}" src="https://github.com/user-attachments/assets/dbd81c33-df94-43be-9b53-62b11faf1567" />





















<img width="735" height="354" alt="{5E744658-0DCD-4D0D-968C-1BA84549AF01}" src="https://github.com/user-attachments/assets/35ff8883-efa6-47eb-95ea-07957d246e7c" />


































<img width="751" height="390" alt="{6C518B7E-1116-4F72-9691-2345681CE78C}" src="https://github.com/user-attachments/assets/93a9d850-8da0-45b3-a2ce-ffe5b07759ca" />



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
## Exe 9: Annotating function with Gene Ontology (GO) terms
### 1.Search for the GO terms and the functional categories of the following GO IDs GO:0009414, GO:0035618, GO:0016491. Tip : For multiple search GO IDs needs to be separated by a space.

<img width="908" height="261" alt="image" src="https://github.com/user-attachments/assets/375021df-0e80-4bbe-8871-d47ccf0c42b9" />



<<<<<<< Updated upstream


<img width="403" height="92" alt="{38EA3CA8-2B35-4F03-82D6-9DF34C726431}" src="https://github.com/user-attachments/assets/70a463e5-dd8d-4f2f-a9a1-58c5f20ff48e" />









### 2.What are the GO ID and the functional category corresponding to photosynthesis?
For photosynthesis we found  the GO id : GO:0015979 which the functional category is biological process.

### 3.What are the immediate parent(s) and children of the photosynthesis GO term?
#### Immediate Parents (Ancestors)
The Ancestor Chart indicates that photosynthesis is a direct descendant of one primary term:
metabolic process (GO:0008152)


<img width="814" height="656" alt="image" src="https://github.com/user-attachments/assets/9138addc-a157-4b53-9c5f-26aea22c99a3" />













#### Immediate Children (Descendants)
The Child Terms table lists seven direct descendants of the photosynthesis term:

<img width="1171" height="622" alt="image" src="https://github.com/user-attachments/assets/8c5d6f50-a6d9-4320-8c83-e58e2fe0785a" />
















### 4.Search for the GO annotation terms of the following protein A0A068LKP4,A0A097PR28, A0A059Q6N8? What do you observe?


<img width="727" height="88" alt="{3C67776D-934C-40A4-8ED2-80BAF105F782}" src="https://github.com/user-attachments/assets/10c3a9cf-7e1f-47e8-9706-c3ea65b2d4ba" />






By comparing the annotations of these three proteins, several important points become clear:

#### 1. Functional Conservation Across Species
Even though Arabidopsis (a model weed), Prunus (a fruit tree), and Zea (a cereal crop) are separated by large evolutionary distances, their corresponding proteins carry almost identical functional annotations. This strongly supports the idea that they are true orthologs—genes that have retained the same biological role, in this case auxin‑related signaling and transcriptional regulation, across very different plant lineages.

#### 2. Evidence Code Patterns (IEA)
Looking at the “Evidence” column, you’ll notice that most annotations for peach and maize rely on the IEA code (Inferred from Electronic Annotation). This means their functions are predicted computationally based on similarity to experimentally validated proteins—typically those from well‑studied model species—rather than on direct experimental work in these crops.

#### 3. Consistent GO Namespace Coverage
All three proteins map to the same three Gene Ontology categories:

Molecular Function: DNA binding, consistent with their role as transcription factors.

Biological Process: Auxin response and transcriptional regulation.

Cellular Component: Localized to the nucleus, where transcription factors operate.


### 5. How many gene products are involved in leaf development? Give the GO ID corresponding to this term.



<img width="696" height="136" alt="image" src="https://github.com/user-attachments/assets/10684e41-9a61-4d57-966b-0ab3a3d2b57c" />






### 6.How many proteins of Arabidopsis thaliana, Prunus perisca and Zea mays are assigned to the leaf development GO term. Tip : Zea mays. Taxonomy ID=4577

Arabidopsis thaliana ID= 3702: 127 proteins 

<img width="347" height="51" alt="{529A5C7C-DC91-4692-99B9-240EA4FB2025}" src="https://github.com/user-attachments/assets/5722486d-04a1-497d-9a14-fd2ba29fd301" />


Prunus persica ID=3760: 19 proteins

<img width="324" height="76" alt="image" src="https://github.com/user-attachments/assets/21dce6a3-ade0-4887-bc85-4a17a68fe44e" />





Zea mays ID= 4577: 45 proteins 

<img width="701" height="168" alt="image" src="https://github.com/user-attachments/assets/416e7a84-ad88-4698-8bd6-308070fcd0f9" />


###  Check the total number of BP annotations and proteins supported by the experimental evidence codes in both Arabidopsis thaliana and Prunus persica. (see the evidence codes) Tip : check the ‘Statistics’ box.
<img width="591" height="73" alt="image" src="https://github.com/user-attachments/assets/6343eaef-1261-4425-b198-2020b96eea95" />















Exe 10 : Predicting 3D structure
<img width="745" height="639" alt="image" src="https://github.com/user-attachments/assets/6c45d97d-ab9e-4853-8dd2-7f9a1f0e53a9" />
=======
**Observation**: Although the average score is low, the key domains identified in earlier exercises show high structural confidence, validating the functional annotation.
### Exercise 4.1.1 Results
- Database successfully formatted in the coding directory.
- Total sequences: 136,324
>>>>>>> Stashed changes
