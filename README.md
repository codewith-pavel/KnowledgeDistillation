# NSCLC Detection via Knowledge Distillation with Teaching Assistant

![License](https://img.shields.io/badge/license-MIT-green)
![Python](https://img.shields.io/badge/python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.6+-orange)
![PyTorch](https://img.shields.io/badge/PyTorch-1.9+-red)

## Overview
This repository implements the research from the paper:
**"Non-small cell lung cancer detection through knowledge distillation approach with teaching assistant"** by *Mahir Afser Pavel et al.*

It presents a novel three-phase knowledge distillation (KD) framework for classifying Non-Small Cell Lung Cancer (NSCLC) from CT scan images. The model pipeline reduces computational complexity while maintaining high classification accuracy.

## Key Features
- Three-phase knowledge distillation: ViT (Teacher), Resnet152v2 (Teaching Assistant), CNN (Student)
- Efficient student model with reduced training time
- Cost-sensitive learning to handle class imbalance
- SHAP-based explainability for medical interpretability
- Streamlit web app for real-time NSCLC classification


## Dataset
**NSCLC-Radiomics**: 51,215 CT images from 422 patients, labeled into 5 classes.

| Class                     | Number of Images | Percentage |
|---------------------------|------------------|------------|
| Adenocarcinoma            | 6,018            | 11.75%     |
| Large Cell Carcinoma      | 13,655           | 26.66%     |
| Normal                    | 5,130            | 10.01%     |
| Not Otherwise Specified   | 7,643            | 14.92%     |
| Squamous Cell Carcinoma   | 18,769           | 36.64%     |

**Preprocessing**: Resize to 80x80, normalize, apply cost-sensitive weighting.

## Model Architecture
- **Teacher**: ViT (378M parameters)
- **Teaching Assistant**: ResNet152v2 (147M parameters)
- **Student**: Custom CNN (25M parameters)

All models trained with KD (alpha = 0.7, temperature = 7).

## Results
| Model         | Test Accuracy | Training Time per Epoch | Parameters  |
|---------------|---------------|--------------------------|-------------|
| ViT (Teacher) | 93.31%        | 65.3s                    | 378M        |
| Resnet (TA)   | 90.99%        | 5.09s                    | 147M        |
| CNN (Student) | **94.53%**    | **5.01s**                | **25M**     |

✅ **Insight**: Student outperforms teacher with 5.02x reduction in training time.

## Web Application
- Built using **Streamlit**
- Upload CT scan image and receive classification output
- Run locally or deploy via **Ngrok**

## Explainable AI
- Integrated **SHAP** explainability with `PartitionExplainer`

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for more information.

## Citation
```bibtex
@article{pavel2025nsclc,
  title={Non-small cell lung cancer detection through knowledge distillation approach with teaching assistant},
  author={Pavel, Mahir Afser and others},
  journal={PLOS ONE},
  year={2025},
  publisher={Public Library of Science}
}
```
