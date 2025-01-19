# Project: Pneumonia Detection from Chest X-Rays

## Project Overview

In this project, you will leverage the skills gained in this 2D medical imaging course to analyze data from the NIH Chest X-ray Dataset and train a CNN to classify chest X-rays for the presence or absence of pneumonia. The goal is to develop a model capable of detecting pneumonia with accuracy comparable to that of human radiologists, with the potential for submission to the FDA for 510(k) clearance as a software-based medical device. As part of the submission process, you will formally document your model, including details of the training dataset and a validation plan that meets FDA requirements. You will be provided with medical images labeled with clinical diagnoses extracted from corresponding radiology reports. Additionally, the project includes access to a GPU for efficient deep-learning model training and a dataset of 112,000 chest X-rays with disease annotations from 30,000 patients.

In this project:

* Distill data that are useful for training algorithms to detect pneumonia from a giant set of chest X-ray images taken from actual patients.
* Build a CNN model to detect the presence or absence of pneumonia.
* Build wrappers that read medical images from their real-world clinical formats (DICOM).
* Write up a documentation & validation plan of your algorithm for FDA 510(k) submission.

![Chest_X_Ray](https://github.com/1Px-Vision/AI_for_Healthcare/blob/main/Project%20Pneumonia%20Detection%20from%20Chest%20X-Rays/Chest_X_Ray.jpg)

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

### 1. General Information
**Intended Use Statement:**
This system is designed to assist radiologists in detecting pneumonia in chest X-ray images, specifically in PA/AP views.

**Indications for Use:**
The device is suitable for both male and female patients aged 1 to 100 years. It can also analyze cases where pneumonia coexists with other conditions, including Atelectasis, Cardiomegaly, Consolidation, Edema, Effusion, Emphysema, Fibrosis, Hernia, Infiltration, Mass, Nodule, Pleural Thickening, and Pneumothorax.

**Device Limitations:**
A high-performance GPU is required to run the Algorithm efficiently.

### 2. Algorithm Design and Function

#### DICOM Verification and Preprocessing Steps
DICOM Checking Steps
Perform three verification checks on the DICOM image:

* **Patient Position:** Only images in the AP (Anteroposterior) or PA (Posteroanterior) view will be processed.
* **Modality Check:** Only DX (Digital Radiography) images will be accepted.
* **Body Part Examined:** Only chest X-ray images will be processed.

#### Preprocessing Steps:

1. Rescale the image by dividing pixel values by 255.0.
2. Normalize the image using the mean and standard deviation obtained from the training dataset.
3. Resize the image to (1, 224, 224, 3) to match the network input requirements.

### 3. Algorithm Training

#### Model Parameters:

##### Data Augmentation:

* Horizontal Flip
* Height Shift Range: 0.1
* Width Shift Range: 0.1
* Rotation Range: 20°
* Shear Range: 0.1
* Zoom Range: 0.1

##### Training Configuration:

* Batch Size: 32
* Optimizer Learning Rate: 3e-4

##### Pre-trained Model Adjustments:

* Frozen Layers: First 20 layers
* Fine-Tuned Layers: None

##### Additional Layers:

* Flatten
* Dropout (0.5)
* Dense (1024, Activation: ReLU)
* Dropout (0.5)
* Dense (512, Activation: ReLU)
* Dropout (0.5)
* Dense (256, Activation: ReLU)
* Dense (1, Activation: Sigmoid)

![Result_P](https://github.com/1Px-Vision/AI_for_Healthcare/blob/main/Project%20Pneumonia%20Detection%20from%20Chest%20X-Rays/Result_P.jpg)

![Result_F1](https://github.com/1Px-Vision/AI_for_Healthcare/blob/main/Project%20Pneumonia%20Detection%20from%20Chest%20X-Rays/Model_Precision_Recall_F1_vs_Thresholds.jpg)

### 4. Databases

The dataset consists of 112,120 X-ray images, with only 1,430 (1.27%) identified as Pneumonia Positive. To ensure an effective training and validation split, the following approach will be taken:

* **Positive Case Selection:** Include all 1,430 Pneumonia-positive images.
* **Training and Validation Split:** Allocate 80% of the positive cases for training and 20% for validation.
* **Training Dataset:** Balance the number of negative and positive cases to create a well-proportioned training set.
* **Validation Dataset:** Maintain a 4:1 ratio of negative to positive cases to better reflect real-world clinical conditions.

### 5. Ground Truth
The ground truth consists of labels derived from NLP processing. However, at this stage, NLP is not advanced enough to capture all the information present in the reports, resulting in an accuracy of approximately 90%.

### 6. FDA Validation Plan

**Patient Population Description for FDA Validation Dataset**

The dataset includes male and female patients ranging in age from 1 to 100 years. The gender distribution is slightly skewed toward male patients, with an approximate male-to-female ratio of 1.2. Patients in the dataset may present with pneumonia and one or more of the following comorbid conditions:

* Atelectasis
* Cardiomegaly
* Consolidation
* Edema
* Effusion
* Emphysema
* Fibrosis
* Hernia
* Infiltration
* Mass
* Nodule
* Pleural Thickening
* Pneumothorax

#### X-Ray DICOM File Requirements
* **Patient Position:** AP or PA
* **Image Type:** DX
* **Body Part Examined:** CHEST

#### Ground Truth Acquisition Methodology
A silver standard for radiological interpretation will be established based on expert radiologist readings.

## Included in this repository
The project introduces the following modified files:

* Build and train model.ipynb
* EDA.ipynb
* Inference.ipynb
* my_model.json
