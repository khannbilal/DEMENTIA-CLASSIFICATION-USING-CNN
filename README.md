# Dementia Classification Using CNN

# Overview
This project focuses on leveraging deep convolutional neural networks (CNNs) for automated classification of dementia stages from MRI brain scans. The objective is to enable early diagnosis and support personalized treatment planning by distinguishing between nondemented, mild, and moderate dementia conditions. The system enhances diagnostic accuracy while minimizing reliance on manual clinical interpretation, contributing to scalable and objective neuroimaging analysis.

# Framework
Models: CNN (Custom 2D & 3D variants), ResNet18 (Transfer Learning Baseline)
Libraries: Python, PyTorch, NumPy, OpenCV, Scikitlearn, Matplotlib

# Scope
 Develop and train CNN architectures for dementia stage classification.
 Evaluate model performance across multiple MRI datasets (ADNI, OASIS).
 Apply preprocessing techniques for skull stripping, normalization, and augmentation.
 Compare baseline CNN with finetuned ResNet model.
 Visualize activation maps to interpret neural attention patterns.

# Dataset
Name: ADNI (Alzheimer’s Disease Neuroimaging Initiative) / OASIS1 MRI Dataset
Link: [https://adni.loni.usc.edu/](https://adni.loni.usc.edu/) | [https://www.oasisbrains.org/](https://www.oasisbrains.org/)
Description: Structural MRI scans categorized into nondemented, mild cognitive impairment (MCI), and moderate dementia stages.

# Preprocessing Steps:
 Skull stripping using FSLBET.
 Intensity normalization (Zscore).
 Slice extraction from 3D MRI volumes.
 Data augmentation: rotation, horizontal flip, brightness variation.
 Stratified data split (70% train, 15% validation, 15% test).

 # Methodology
 1. Data Loading & Preprocessing

 Implemented custom PyTorch dataset class for efficient loading of MRI slices.
 Automated labeling pipeline for dementia stage classification.

 2. Model Loading / Training

 Baseline CNN: 5 convolutional blocks with ReLU and dropout regularization.
 ResNet18 finetuned on MRI data for enhanced spatial feature extraction.
 Crossentropy loss with Adam optimizer and learning rate scheduler.

 3. Inference

 Predictions generated on unseen test data using majority voting across MRI slices.
 Confidence visualization via GradCAM heatmaps for interpretability.

 4. Evaluation Metrics

 Accuracy, Precision, Recall, F1score.
 ROCAUC per class for multistage classification.
 Confusion matrix for stagelevel error analysis.

 5. Project Architecture Diagram (Textual)

        ┌────────────────────────┐
        │ MRI Brain Scans (ADNI) │
        └──────────┬─────────────┘
                   │
        ┌──────────▼────────────┐
        │ Preprocessing Pipeline │
        │ (Normalization, Aug.)  │
        └──────────┬────────────┘
                   │
        ┌──────────▼────────────┐
        │ CNN / ResNet Backbone │
        │ (Feature Extraction)  │
        └──────────┬────────────┘
                   │
        ┌──────────▼────────────┐
        │ Fully Connected Layer │
        │ (Classification Head) │
        └──────────┬────────────┘
                   │
        ┌──────────▼────────────┐
        │  Dementia Stage Output │
        │ (3Class Prediction)   │
        └────────────────────────┘

#  Results
| Model                  | Accuracy | F1Score  | ROCAUC  | Precision | Recall   |
| Baseline CNN           | 0.88     | 0.87     | 0.91    | 0.86      | 0.88     |
| ResNet18 (Finetuned)   | 0.93     | 0.92     | 0.95    | 0.93      | 0.92     |

# Qualitative Results:
 GradCAM visualizations confirmed focus on hippocampal and cortical regions linked to cognitive decline.
 The finetuned ResNet demonstrated superior sensitivity in mildstage dementia detection.

# Conclusion
The CNNbased system achieved 93% classification accuracy in distinguishing dementia progression stages using MRI scans. The integration of transfer learning enhanced feature discrimination, supporting earlystage detection with clinical relevance.
Limitations: Model performance depends on MRI quality and dataset balance; further validation on multiinstitutional cohorts required.

# Future Work
 Extend framework with 3D CNNs for volumetric learning.
 Integrate multimodal data (MRI + PET + cognitive scores).
 Apply explainable AI techniques for clinicianfriendly interpretability.
 Deploy as a cloudassisted diagnostic tool for healthcare professionals.

# References
1. Jack, C. R. et al. (2008). The Alzheimer’s Disease Neuroimaging Initiative (ADNI): MRI Methods. Journal of Magnetic Resonance Imaging.
2. Marcus, D. S. et al. (2007). Open Access Series of Imaging Studies (OASIS): Crosssectional MRI Data. Journal of Cognitive Neuroscience.
3. He, K. et al. (2016). Deep Residual Learning for Image Recognition. CVPR.
4. Selvaraju, R. R. et al. (2017). GradCAM: Visual Explanations from Deep Networks via Gradientbased Localization. ICCV.

# Closest Research Paper:
> “A Deep Learning Framework for Early Detection of Alzheimer’s Disease from Structural MRI” — NeuroImage: Clinical, 2022.
> This work closely parallels the project’s objective of CNNbased dementia stage classification and interpretability through medical imaging analysis.
