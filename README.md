# CST-MT: Cross-scale Transformer based integration of MRI and RNA sequencing data in Parkinson's disease(PD) diagnosis

In order to conduct reliable disease diagnosis for neurodegenerative disorder, the CST-MT method conduct multimodal learning about RNA-seq and neuroimages. Two types of data modalities have suitable computational methods. Specifically, the M<sup>2</sup>CNN module and MLP module are used to extracts representations of neuroimaging and transcriptomics data, respectively. In addition, the CMC fusion module is designed to extract consensus components between heterogeneous modalities. And modal Dynamic Balance Mechanism (MDB) mechanism was applied to balance consensus and unique components between various modalities, alleviating the issue of modal imbalance.

## Architecture

![](figures\Fig1_CST-MT-Framework.png)

## Install

We train the CST-MT model under the Ubuntu22.04, and graphics card is RTx3090.

```bash
conda create -n CST-MT python==3.8
conda activate CST-MT
```

## Requirements

```bash
pip install -r requirements.txt
```

## Data availability

Whole-blood RNA-seq datasets that are related with PD were downloaded from the AMP-PD platform(\href{https://amp-pd.org/}{https://amp-pd.org/}) and is subject to access control. Individuals are required to register in order to access the benchmark datasets. Two group of MRI image data were obtained from Parkinson's Progression Markers Initiative (PPMI)(\href{https://www.ppmi-info.org/}{https://www.ppmi-info.org/}) and Parkinson's Disease Biomarkers Program (PDBP)(\href{https://pdbp.ninds.nih.gov/}{https://pdbp.ninds.nih.gov/}), respectively.

## Usage

First, download the required data sets from the PPMI, PDBP, and AMP-PD platforms respectively. Place the files in the corresponding folder.

### MRI-processing

1、Using FSL tools to decranialize MRI brain images.

2、Run MRI-preprocessing/datasets/process_MRI_nobrain.ipynb

### Data-processing

1、Run the processing/datasets/over_aligned.ipynb file to generate a sample-aligned data set and split the training set, validation set, and test set.

2、Run the processing/datasets/process_transpot.ipynb file to make full use of the data set that cannot be sample aligned as a single-modal training set.

2、Run the processing/datasets/split_imagedata_nobrain.ipynb file to make full use of the data set that cannot be sample aligned as a single-modal training set.

The obtained files are located under processed_data/datasets/

### Training

1、Run the training/datasets/evaluation_transpot.ipynb file to get the blood transcriptomics model.

2、Run the training/datasets/evaluation_2D_3slice.ipynb file to get the MRI model.

3、Run the training/datasets/evaluation_aligned_balanced.ipynb file to get the Multi-modal model.

The obtained files are located under models/datasets/