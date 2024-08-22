# F1L-scRNA-seq
This is part of the Figure 1 Lab (F1L) internship emulator where we dive into the Kinker paper (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8135089/) to recreate the first figure of the paper.  Through this process, I will learn the fundamentals of single-cell RNA sequencing (scRNA-seq), its use in cancer research and drug development, and how to analyze and interpret scRNA-seq data. 


## Table of Contents
- [Key Scientific Question](#the-key-scientific-question)
- [Week 1 Memo](#week-1-memo)
- [Week 2 Memo](#week-2-memo)
- [References](#references)
  

## The Key Scientific Question

**KSQ**: Using available scRNA-seq data from cancer cell lines, how would you explore the use of the following FDA-approved antibody therapies in additional cancers?

- Trastuzumab:  Targets HER2 and is used in the treatment of HER2-positive breast and gastric cancers.
- Bevacizumab:  Targets VEGF and is used for a variety of cancers, including colorectal, lung, glioblastoma, breast, liver, and kidney cancer.
&nbsp;


## Week 1 Memo

### Cancer Cell Lines
#### What are cancer cell lines?
Cancer cell lines are populations of cancer cells that have been cultured in the lab and can grow indefinitely. They are derived from tumor tissue samples from various cancer types and cultured in a laboratory under controlled conditions to allow these cancer cells to continue growing and dividing.  Since tumor cells do not go through the same cellular aging and death process as normal cells (Hayflick limit), the tumor cells are immortalized in these cell line, preserving their genetic and phenotypic traits.  Thus, these cells lines are used extensively in research.  

Some of the applications in research are as follows:
- Basic Research: Understanding cancer biology, including the genetic and molecular mechanisms of cancer development and progression.
- Drug Discovery and Testing: Screening for new anti-cancer drugs and evaluating their efficacy and toxicity.
- Genetic Studies: Manipulating genes to study their roles in cancer and identifying potential targets for therapy.
- Biomarker Discovery: Identifying and validating biomarkers for cancer diagnosis, prognosis, and treatment response.
- Mechanistic Studies: Investigating cellular processes and signaling pathways involved in cancer.
&nbsp;  
#### Why do we use cancer cell lines?
Cancer cell lines are widely used in research because of the consistency and reproducibility of source material.  Once established, cancer cells lines can be propagated indefinitely while preserving their genetic and phenotypic information.  This allows researchers to conduct experiments repeatedly using the same source and under the same conditions.  In addition, cancer cell lines allow researchers to genetically modify the cells and study the effects of specific genes for cancer development and progressions.  Techniques such as CRISPR-Cas9, RNA interference, and overexpression systems are commonly used.  Cell lines are also useful in screening potential anti-cancer drugs for efficacy and toxicity in a high-throughput fashion to identify promising therapeutic candidates.  
&nbsp;  


### scRNA-seq 
#### What is single-cell RNA sequencing (scRNA-seq)?
scRNA-seq is a genomic research technique that detects and quantitatively analyzes the mRNA  for gene expression profiles in single cells within a biological sample such as tissue or tumor.
Unlike traditional bulk RNA-seq techniques where it measures the average gene expression profiles of a many cells in a sample, scRNA-seq allows researchers to gain insights into the heterogeneity of gene expression within a cell population.   This allows researchers to understand the diversity and complexity of cellular functions and states in various biological contexts.

Advantages of scRNA-seq include high resolution which affords insights at the single-cell level and can reveal cellular heterogeneity, unbiased which allows for discovery of rare cell types and new states without prior knowledge, and can capture wide range of dynamic range of gene expression levels.

Disadvantages of scRNA-seq include high technical noise, meaning that there are variability in the technical process; the high complexity of data requires sophisticated computational tools and expertise to analyze and interpret the data; and higher cost due to the complexity of the technique.  
&nbsp;  

#### Why do we use scRNA-seq data in cancer drug development?
Given the above advantages, scRNA-seq allows deeper understanding of tumor heterogeneity, can identifying cancer stem cells, and aid investigating of mechanisms of resistance to therapies.

- Understanding tumor heterogeneity:
    - In addition to ability to identify cellular diversity, scRNA-seq can also identify tumor cells that have distinct mutations.  Researchers can use scRNA-seq to follow the evolution of these identified tumor cells and help understand how tumors develop resistance to therapies.
- Identify therapeutic targets:
    - By analyzing gene expression profiles at the single-cell level, researchers can identify specific biomarkers or molecular targets that are expressed in particular subpopulations of cancer cells, which may be missed in bulk RNA-seq analyses.
    - scRNA-seq data can also reveal activation status of signaling pathways in individual cell.  This helps researchers identify key signaling pathways that are driving cancer progression and identify points of intervention for targeted therapies.
- Drug screening and validation:
    - scRNA-seq can be used to screen the effects of drugs on different cell populations within a tumor, helping to identify compounds that target specific cancer cell subtypes or resistant cells.
    - Also, by understanding the complex interactions between different cell types and signaling pathways, scRNA-seq can help in designing combination therapies that are more effective in targeting multiple aspects of tumor biology.  
&nbsp;  

#### scRNA-seq workflow: 
1. Isolate of viable single cells from the tissue of interest using some of the following methods:  micro-dissection, flow cytometric cell-sorting, microfluidic platforms, droplet-based methods (Haque et al, 2017).
2. Lyse single-cells to preserve cellular mRNA.
3. mRNA capture using poly(T) primers that bind to poly(A) tails of mRNA.
4. Reverse-transcribe poly(T)-primed mRNA into cDNA.
5. Amplify cDNA by PCR or in vitro transcription.
6. Generate cDNA sequencing libraries for respective NGS technologies (add indexes or barcodes to identify each library).
7. Pool cDNA libraries and sequence on NGS.
8. Use bespoke bioinformatic tools to analyze scRNA-seq data.
    1. QC and filter out poor quality data such as from low quality cells, 2+ cell data mistaken as single cell.
    2. Reduce multi-dimensional data to smaller dimensions for visualization and interpretation by using methods such as Principal Component Analysis (PCA), t-distributed stochastic neighbour embedding (t-SNE), and Gaussian process latent variable modelling (GPLVM).
    3. Clustering into subpopulations by functional similarity or developmental relationships  
&nbsp;  


### Cancer Drugs
#### Trastuzumab 
It targets HER2 and is used in the treatment of HER2-positive breast and gastric cancers.

**What is trastuzumab?**
- Trastuzumab (Herceptin) is a monoclonal antibody that targets the extracellular domain of HER2 protein.  
- It binds to the extracellular domain of HER2, suppressing its intracellular signaling pathways.  
- What is the mechanism for trastuzumab treatment of HER2+ BC?  
    - Inhibition of HER2 Signaling:
        - Prevention of Dimerization:  
            - Tratsuzumab binds to the extracellular domain of HER2, which can interfere with the receptor's ability to dimerize with other HER family members.  This inhibition of heterodimerization is crucial because heterodimers (especially HER2/HER3) are highly potent activators of downstream signaling pathways that promote cell proliferation and survival.
            - Some studies have shown that tratsuzumab induces HER2 homodimerization in HER2+ BC cell lines.  This suggests that by inducing homodimerization, tratsuzumab reduces HER2 heterodimerizations, which inhibits downstream signaling.
				
    - Reduction of HER2 levels on the Cell Surface:
        - Receptor Downregulation:  Some studies have shown that trastuzumab induces the internalization and degradation of HER2 receptors.  By promoting endocytosis and subsequent lysosomal degradation, trastuzumab reduces the number of HER2 receptors available on the cell surface.  This reduces the potential for both homo- and heterodimer formation.
		    
    - Antibody-Dependent Cellular Cytotoxicity (ADCC): 
        - Immune System Activation:  Trastuzumab can recruit immune cells, such as natural killer (NK) cells, to target and kill HER2-overexpressing cancer cells through ADCC.  
				
- Trastuzumab reduces the overall amount of HER2 on the cell surface, thereby limiting the ability of HER2 to form both homodimers and heterodimers.  This reduction in dimerization potential leads to decreased activation of signaling pathways such as PI3K/AKT and MAPK pathways, that drive cell proliferation and survival in HER2+ cancers.  
&nbsp;  

**What is HER2?** 
- Human Epidermal Growth Factor 2 (HER2) is a protein encoded by the ERBB2 gene located at the human chr17 q21 region.  It is a member of the ErbB receptor tyrosine kinases, including EGFR, HER3 and HER4.
    - By binding to growth factors on the cell surface, it can activate signaling pathways promoting cell growth, division and repair.
    - Amplification of the ErbB gene can lead to over-expression of the HER2 protein, which can cause uncontrolled cell growth and division, subsequently leading to cancer, such as HER2+ breast cancer.  This subtype of breast cancer is more aggressive and can spread more quickly than HER2- cancers.
    - HER2 receptors structure contains 3 parts:
        - Ligand-Binding Domain:  Extracellular domain containing 4 subdomains on the cell surface that is responsible for binding to ligands for activation. HER2 does not have a known natural ligand, thus it is thought to be activated by dimerization with other receptors in the HER family (HER1, HER3, HER4).
		    - Transmembrane Domain:  Transmembrane domain that connects the extracellular and the cytoplasmic domains.  This domain anchors the HER2 protein in the cell membrane.  
			      - Intracellular Domain:  The C-terminal cytoplasmic domain that contains tyrosine kinase and regulatory subdomains.
				    - Tyrosine Kinase Domain:
				        - This domain has enzymatic activity that is activated upon receptor dimerization and phosphorylation.  The tyrosine kinase domain transfers phosphate groups from ATP to specific tyrosine residues on the receptor itself and on downstream signaling proteins.  This phosphorylation initiates a cascade of signaling pathways involved in cell growth, differentiation, and survival.
				    - Regulatory Regions:
					      - The intracellular part of HER2 includes various regulatory regions that control its activity and interactions with other cellular proteins.
		- These 3 domains work together to transmit signals from the extracellular environment to the cell's interior, influencing various cellular processes.   The overexpression or amplification of the HER2 gene, leading to an increased amount of HER2 protein on the cell surface, can result in the continuous activation of these signaling pathways, contributing to the development and progression of certain cancers, particularly breast cancer.  
&nbsp;  			
	
#### Bevacizumab
Targets VEGF and is used for a variety of cancers, including colorectal, lung, glioblastoma, breast, liver, and kidney cancer 

**What is bevacizumab?** 

https://www.cancer.gov/about-cancer/treatment/drugs/bevacizumab
- It is a type of targeted therapy called an angiogenesis inhibitor.  It works by blocking the VEGF protein to prevent the growth of new blood vessels that feed tumors.

<img width="225" alt="image" src="https://github.com/user-attachments/assets/77cadf72-cc88-4dc1-a607-5ec19675a385">

Fig 1:  Graphics from Labiotech showing how VEGF promotes tumor growth by forming new blood vessels and how Bevacizumab targets VEGF protein to inhibit angiogenesis (Bancroft, 2022)

<img width="384" alt="image" src="https://github.com/user-attachments/assets/5ea3bea6-72a2-41c4-a7b3-812489f5ef98">



Fig 2:  Graphic showing interactions between VEGF and VEGFR-2 and how Avastin interacts with VEGF-A to prevent angiogenesis  (Bancroft, 2022).


Bevacizumab (Avastin by Roche) is a monoclonal anti-vascular endothelial growth factor antibody that targets and inhibits the VEGF protein.  It is used as a cancer treatment to reduce the formation of new blood vessels leading to tumor cells growth.  &nbsp;  

**angiogenesis:**  The process of formation of new blood vessels from existing ones.  
- Normal angiogenesis is crucial in growth and development of vascular system in embryos and the development of organs and tissues.  It is also crucial in repairing damaged tissues such as in wound healing.  It is also involved in the development of blood vessels during menstrual cycles and placental development during pregnancies.
- Abnormal angiogenesis can result in cancer where new blood vessels help tumor cells to grow and proliferate.   Also, abnormal blood vessel formations in the retina can lead to age-related macular degeneration and diabetic retinopathy.  
&nbsp;  

**What is VEGF?** 

**VEGF-A:** This is a primary growth factor involved in angiogenesis. It binds to receptors on the surface of endothelial cells, which are the cells lining blood vessels.  

**VEGFR-2:** This is one of the main receptors through which VEGF-A exerts its effects. It is predominantly expressed on endothelial cells and plays a crucial role in mediating the angiogenic signals.  

When VEGF-A binds to VEGFR-2 on the surface of endothelial cells, it triggers several intracellular signaling pathways.  
- PI3K/Akt Pathway: This pathway promotes cell survival and proliferation, contributing to the growth of new blood vessels.
- MAPK/ERK Pathway: This pathway is involved in cell growth, differentiation, and migration, which are essential for the formation of new blood vessels.  &nbsp;  


**How does bevacizumab work?**

Bevacizumab works by binding to the VEGF-A protein.  A key driver for angiogenesis is the interaction between Vascular Endothelial Growth Factor Receptor 2 (VEGFR-2) and Vascular Endothelial Growth Factor A (VEGF-A).  

When these signaling pathways like PI3k/Akt and MAPK/ERK are activated, endothelial cells divide and proliferate, then migrate to area of signal and  form new blood vessel sprouts.  They then integrate into the existing blood vessel network and become new vessels.  

By binding to VEGF-A protein, bevacizumab prohibits VEGF-A from interacting with its receptors on the endothelial cells, hence reducing angiogenesis.  Studies have also shown that bevacizumab can also reduce size of existing microvessels and reduce tumor size over time (Mukherji, S.K., 2010).  

&nbsp;  

## Week 2 Memo

## References

Bancroft, D. (2022, June 21). Roche's patent halts an Amgen biosimilar debut. Labiotech.eu. Retrieved from  https://www.labiotech.eu/trends-news/roches-patent-halts-an-amgen-biosimilar-debut/

DrugBank. (2024, May 3). Bevacizumab. DrugBank Online. Retrieved [date], from  https://go.drugbank.com/drugs/DB00112

Haque, A., Engel, J., Teichmann, S. A., & Lönnberg, T. (2017). A practical guide to single-cell RNA-sequencing for biomedical research and clinical applications. Genome Medicine, 9(75).  https://doi.org/10.1186/s13073-017-0467-4

Mukherji, S. K. (2010, February). Bevacizumab (Avastin). American Journal of Neuroradiology, 31(2), 235-236.  https://doi.org/10.3174/ajnr.A1987

National Cancer Institute. (2023, December 8). Bevacizumab. National Cancer Institute. Retrieved [date], from  https://www.cancer.gov/about-cancer/treatment/drugs/bevacizumab





