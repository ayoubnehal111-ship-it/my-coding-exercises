# Session 3 – Transcriptome analysis
##3.1)How many samples & isoforms are included in TPM_counts_Drought_W_dataset.csv?
The TPM_counts_Drought_W_dataset.csv file was loaded into R using the read.csv() function, and the dataset dimensions were initially examined using the dim() function.
At first inspection, the dataset appeared to contain 9,940 isoforms and 40 columns; however, this result was misleading because the target_id column was included among the columns.
To obtain the correct numbers, the script was slightly modified by adding two lines that explicitly display the dimensions of the reformatted expression matrix. While the initial output referred to the original table (W_dataset), the modified code reports the dimensions of the processed matrix (datExprW), which excludes the target_id column and is used for downstream analyses.
As a result, the final expression matrix used for downstream analyses consists of 39 RNA-seq samples and 9,940 isoforms.
The script used to load, verify, and reformat the dataset, as well as the corresponding results, is presented in the figure below.
<img width="784" height="489" alt="image" src="https://github.com/user-attachments/assets/dead7d4a-2905-4809-822d-25f0e3faad31" />
<img width="1001" height="522" alt="image" src="https://github.com/user-attachments/assets/7bac0102-1e49-4f1f-adf7-06fd03c1d6a0" />


##3.2) How many samples are discarded after outlier analysis?
The detection of outlier samples was performed using the goodSamplesGenes() function from the WGCNA package. This function assesses the quality of the expression matrix by identifying samples and genes with excessive missing values, which could potentially bias downstream network construction.
The analysis was applied to the reformatted expression matrix (datExprW), which contains only expression values and excludes the identifier column. The output of goodSamplesGenes() indicated that all samples and genes passed the quality control step, as reflected by the allOK = TRUE result.
Consequently, no RNA-seq samples were identified as outliers and no samples were removed from the dataset at this stage. The script used for this analysis was not modified, and the corresponding results are shown in the figure below.
<img width="1129" height="694" alt="image" src="https://github.com/user-attachments/assets/e8c47dc0-4389-466f-bcc3-210b070a20c9" />

##3.3) What power value have you set as appropriate for calculating adjacency?
To construct a weighted gene co-expression network, an appropriate soft-thresholding power was selected using the pickSoftThreshold() function from the WGCNA package. This function evaluates network topology across a range of candidate power values by assessing the scale-free topology fit index (R²) and the mean connectivity.
The scale-free topology fit index was examined as a function of the soft-thresholding power, and a threshold of R² ≥ 0.80 was used as a criterion to approximate scale-free network topology. The results indicate that power = 6 is the smallest power value at which the scale-free topology fit index exceeds this threshold. Beyond this value, the fit index increases only marginally, indicating that higher power values do not substantially improve the scale-free topology of the network.
In addition, the scale independence and mean connectivity plots shown in the figures confirm that power = 6 represents an optimal compromise between achieving scale-free topology and preserving sufficient network connectivity. The plots clearly demonstrate that this power value provides a stable network structure without excessively reducing connectivity.
Therefore, a soft-thresholding power of 6 was selected for adjacency calculation in the W dataset. The results of the soft-threshold selection procedure are presented in the figure below
<img width="1098" height="323" alt="image" src="https://github.com/user-attachments/assets/4df56024-0490-4492-a3ea-adaacc522aec" />
<img width="913" height="232" alt="image" src="https://github.com/user-attachments/assets/51f369d6-2a24-43b4-adba-11a6cbe71ca3" />
<img width="903" height="518" alt="image" src="https://github.com/user-attachments/assets/3b9b015a-9714-4cda-bb4c-d773f9d38503" />

3.4) How many co-expression modules are established before and how many after the module merging process?

3.5) What is the hub isoform (or hub gene) of the cyan module?

3.6) According to the module-trait association heat map, which module has the highest positive correlation with the "blwgrd (below ground biomass)" trait?




