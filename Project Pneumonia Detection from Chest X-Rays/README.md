# Project: Pneumonia Detection from Chest X-Rays

## Project Overview

In this project, you will leverage the skills gained in this 2D medical imaging course to analyze data from the NIH Chest X-ray Dataset and train a CNN to classify chest X-rays for the presence or absence of pneumonia. The goal is to develop a model capable of detecting pneumonia with accuracy comparable to that of human radiologists, with the potential for submission to the FDA for 510(k) clearance as a software-based medical device. As part of the submission process, you will formally document your model, including details of the training dataset and a validation plan that meets FDA requirements. You will be provided with medical images labeled with clinical diagnoses extracted from corresponding radiology reports. Additionally, the project includes access to a GPU for efficient deep-learning model training and a dataset of 112,000 chest X-rays with disease annotations from 30,000 patients.

## Chest X-ray Examinations and Pneumonia Diagnosis: A Deep Learning Perspective

Chest X-ray examinations are among the most common and cost-effective medical imaging procedures. However, interpreting these images for clinical diagnosis can be challenging, even for experienced radiologists. Pneumonia diagnosis relies heavily on chest X-rays, the most effective imaging method for detecting the disease. Each year, more than one million adults in the U.S. are hospitalized due to pneumonia, with approximately 50,000 fatalities. Given its high prevalence, pneumonia is a strong candidate for deep-learning applications in medical imaging. There are two key reasons for this:

1. The availability of large datasets suitable for training deep learning models in image classification.
2. The potential to enhance clinical accuracy and efficiency by improving diagnostic precision and reducing radiologist workload through automated image interpretation.

Diagnosing pneumonia from chest X-rays presents several challenges:

* The visual presentation of pneumonia can vary significantly depending on the infection stage.
* Pneumonia often coexists with other conditions, complicating interpretation.
* It can mimic benign abnormalities, leading to diagnostic uncertainty.

To address these challenges, clinical diagnostic validation typically involves multiple approaches. These include sputum cultures to detect bacterial or viral pathogens, a thorough review of the patient's medical history and demographic factors, and comparative analysis with previous chest X-rays, if available. By integrating deep learning models into this diagnostic workflow, the accuracy and efficiency of pneumonia detection could be significantly improved.

## Project Dataset Overview

The dataset provided for this project was curated by the National Institutes of Health (NIH) to address the challenge of limited large-scale X-ray datasets with ground truth labels. These labels are essential for developing disease detection Algorithms. The dataset is pre-mounted in the Udacity Jupyter GPU workspace, along with code for data loading. Alternatively, you can download it from [Kaggle](https://www.kaggle.com/datasets/nih-chest-xrays/data) to run it locally. However, it is strongly recommended to use the Udacity workspace due to the dataset’s large size and the need for GPU acceleration during training.

## Dataset Summary
* Total Images: 112,120 frontal-view chest X-ray images
* Unique Patients: 30,805
* Resolution: 1024 × 1024 pixels
* File Format: PNG
* Metadata File: ````Data_Entry_2017.csv```` (includes Image Index, Finding Labels, Patient ID, Age, Gender, View Position, and Image Properties)

## Disease Labels
The dataset includes 14 common thoracic pathologies, derived using Natural Language Processing (NLP) from radiology reports:

* Atelectasis
* Consolidation
* Infiltration
* Pneumothorax
* Edema
* Emphysema
* Fibrosis
* Effusion
* Pneumonia
* Pleural Thickening
* Cardiomegaly
* Nodule
* Mass
* Hernia
* Limitations
  
The biggest limitation of this dataset is that labels were extracted using NLP, meaning there may be some inaccuracies. However, the estimated accuracy of the NLP-based labeling exceeds 90%. The original radiology reports are not publicly available, but additional details on the labeling process can be found [here](https://arxiv.org/abs/1705.02315) (provide the actual link).

## Algorithm Description
