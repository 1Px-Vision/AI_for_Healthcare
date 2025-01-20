# Project: Hippocampal Volume Quantification in Alzheimer's Progression

## Alzheimer's Disease (AD) and Its Progression

Alzheimer's disease (AD) is a progressive neurodegenerative disorder that impairs neuronal function and ultimately leads to cell death. It is the most common cause of dementia and is clinically characterized by memory loss, difficulty acquiring new information, language impairment, and other cognitive deficits. For patients displaying early symptoms, monitoring disease progression over time is essential for guiding therapy and managing the condition effectively. MRI-based radiological studies represent one of the most advanced methods for quantifying disease progression. In particular, hippocampal volume measurement has proven to be a valuable biomarker for diagnosing and tracking the progression of various brain disorders, especially AD. Research has consistently shown a reduction in hippocampal volume among AD patients. The hippocampus is a crucial brain structure in humans and other vertebrates, playing a key role in consolidating short-term memories into long-term storage.

![DICOM](https://github.com/1Px-Vision/AI_for_Healthcare/blob/main/Project%3A%20Hippocampal%20Volume%20Quantification%20in%20Alzheimer's%20Progression/DICOM.jpg)

Humans possess two hippocampi, one in each hemisphere of the brain, situated in the medial temporal lobe. Interestingly, the term *hippocampus* originates from Greek and roughly translates to "horselike," reflecting its resemblance to a seahorse—an observation first noted by early anatomists who illustrated the structure.

![Hippo](https://github.com/1Px-Vision/AI_for_Healthcare/blob/main/Project%3A%20Hippocampal%20Volume%20Quantification%20in%20Alzheimer's%20Progression/Hippocampus_small.gif)

## Dataset Overview
We are utilizing the Hippocampus dataset from the [Medical Decathlon](http://medicaldecathlon.com/) competition. This dataset consists of **NIFTI files**, where each volume has a corresponding segmentation mask. The original images are **T2-weighted** MRI scans of the full brain. For this study, we use cropped volumes, focusing only on the hippocampal region. This preprocessing step significantly reduces the dataset size, simplifies the machine learning task, and ensures reasonable training times. However, this should not be mistaken for a "toy" problem—cropping regions of interest is a common practice in medical imaging. Despite the reduction in scope, segmentation remains a challenging task.
