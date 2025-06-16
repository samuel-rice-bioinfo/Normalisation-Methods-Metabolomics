# Metabolomics Normalisation Pipeline
### Introduction
This repository provides a complete and robust workflow for performing multiple normalisation techniques on metabolomics data and calculating the robust relative standard deviation (RSD) for each method. The workflow is written in R and Quarto, making it easy to use, reproducible, and adaptable.

### Multiple normalisation methods:

Raw (No Normalisation)

Median Normalisation

Total Area Normalisation (TAN)

Sum Normalisation

PQN (Probabilistic Quotient Normalisation) using the pmp package

Generalised Logarithm (GLOG) Transformation

![image](https://github.com/user-attachments/assets/2c345e5f-47b0-405f-824b-dad19f3a0618)
Figure 1. The effect of normalisation techniques on the RSD with metabolomic data of neuroblastoma across hypoxic and normoxic conditions. Boxplots comparing the relative standard deviation (RSD) of metabolite intensities across the raw spectra and different normalisation methods: median, median with Glog, probabilistic quotient normalisation (PQN), PQN with Glog, standard normal variate normalisation (SN), SN with Glog, total area normalisation (TAN), TAN with Glog. 

#### Robust RSD Calculation:

Utilises a robust trimmed mean method (5-95%) to exclude outliers.

#### Clear visualisation of RSD values:

Boxplot comparison of RSD for all methods.

Clipped view of RSD values between -500% to +500%.

Fully documented in a Quarto document (reproducible analysis).

Customisable and easy to extend.

#### Structure:
├── README.md                 # Project Documentation    
├── Normalisation_methods.qmd  # Main Quarto Workflow (R + Markdown)  
├── Normalised_Files/          # Output Normalised Files (Auto-Generated)  
│   ├── Raw_Normalised.csv  
│   ├── Median_Normalised.csv  
│   ├── TAN_Normalised.csv  
│   ├── Sum_Normalised.csv  
│   ├── PQN_Normalised.csv  
│   ├── Median_GLOG_Normalised.csv  
│   ├── TAN_GLOG_Normalised.csv  
│   ├── Sum_GLOG_Normalised.csv  
│   └── PQN_GLOG_Normalised.csv  
├── All_RSD_Values.csv         # Combined RSD values for all methods  
└── RSD_Comparison_Clipped.pdf # Final RSD Comparison Plot (Clipped ±500%)  

### Installation
##### Prerequisites
R (version 4.0+)

Quarto (latest version)

### Expected Outputs
Normalised Data Files (Saved in the Normalised_Files/ directory):

Raw, Median, TAN, Sum, PQN, and their GLOG transformed versions.

Combined RSD values for all methods:

All_RSD_Values.csv

Boxplot comparison of RSD (Clipped to ±500%):

RSD_Comparison_Clipped.pdf

### How It Works
##### 1. Normalisation
Multiple normalisation techniques are applied to the raw metabolomics data.

PQN is performed using the pmp package for accuracy.

Generalised Logarithm (GLOG) transformation is applied to enhance normalisation.

##### 2. Robust RSD Calculation
RSD is calculated using a robust trimmed mean method (5-95%) to avoid extreme values.

This provides a more accurate representation of data variability.

##### 3. Visualisation
Boxplot of RSD values for all methods.

Clipped view (±500%) to focus on the main RSD values.

#### Customisation
Changing the QC Group for PQN
Adjust the QC label used for PQN normalisation by editing:

r
se_pqn <- pqn_normalisation(df = se_raw, classes = samples_info$group, qc_label = "Cell21")
Adjusting the RSD Clipping Range
Modify the RSD clipping range in the final plot:

r
scale_y_continuous(limits = c(-500, 500))
Adding or Removing Normalisation Methods
Normalisation methods can be added or removed directly in the Quarto file.

## Troubleshooting
#### RSD Values All Zero
Ensure that the RSD calculation uses the robust method (5-95% trimming).

#### PQN Error
Verify that your data contains correctly defined groups (second header row).

#### Contributing
Please feel free to fork this repository and submit pull requests.

