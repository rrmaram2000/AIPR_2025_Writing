# Wavelet Scattering Features based Colon Cancer Histology Classification

**Authors:** Ritish Raghav Maram, Elliot Levy, Murray Loew  

**Conference:** AIPR 2025

---

## Abstract

This paper presents an application of wavelet scattering transforms to colorectal cancer histopathology tissue classification. We apply a mathematically principled, training-free feature extraction method to classify eight tissue types commonly found in colorectal cancer histology images. Using a two-layer scattering network with Morlet wavelets, we extract 49 scattering coefficients from each 150×150 pixel H&E stained tissue image. These features are used to train a Support Vector Machine (SVM) classifier, achieving **85.10% accuracy** on test data with precision (85.19%), recall (85.10%), and F1-score (85.08%). The method demonstrates particular strength in classifying tumor epithelium (88.8% accuracy), a clinically essential task for cancer detection.

## Key Points

- **First application** of wavelet scattering transforms to histopathology tissue classification
- Training-free feature extraction that requires no iterative optimization
- Competitive performance (85.10% accuracy) on eight-class colorectal cancer tissue classification
- Computationally efficient: 2.42 minutes for feature extraction, 23.82 seconds for training

## Dataset

The study uses the publicly available Kather et al. colorectal cancer (CRC) histology dataset containing:
- **5,000 images** total (625 per tissue type)
- **8 tissue types**: Tumor epithelium, Simple stroma, Complex stroma, Lymphocytes, Debris, Mucosa, Adipose tissue, Background
- **Image size**: 150×150 pixels
- **Staining**: Hematoxylin and eosin (H&E)
- **Train/Test split**: 4,000 training / 1,000 test images

## Methodology

### Scattering Network Architecture
- **Two-layer network** with Morlet wavelets
- **Scaling function**: 20 pixel spatial support for translation invariance
- **Filter banks**: 2 scales × 6 orientations = 12 filters per layer
- **Feature vector**: 49 coefficients (1 zeroth-order + 12 first-order + 36 second-order)
- **Path retention**: Only paths with λ₁ < λ₂ retained based on spectral overlap

### Classification
- Support Vector Machine (SVM) with cubic polynomial kernel
- One-versus-all multiclass classification
- Z-score standardization of features

## Results

### Overall Performance
- **Test accuracy**: 85.10%
- **Cross-validation accuracy**: 81.60% (10-fold)
- **Precision**: 85.19%
- **Recall**: 85.10%
- **F1-Score**: 85.08%

### Per-Class Accuracy
| Tissue Type | Accuracy |
|-------------|----------|
| Empty (Background) | 100.0% |
| Adipose | 96.8% |
| Tumor | 88.8% |
| Lymphocytes | 84.0% |
| Stroma | 82.4% |
| Debris | 82.4% |
| Mucosa | 76.0% |
| Complex Stroma | 70.4% |

### Computational Efficiency
- Feature extraction: 2.42 minutes (all train and test images)
- Training: 23.82 seconds
- Prediction: 0.04 seconds

## Files Included

- **aipr_2025_main.tex** - Main paper in LNCS format
- **notation_guide.tex** - Comprehensive notation reference
- **notation_guide.pdf** - Compiled notation guide
- **Images/** - Directory containing figures
- **llncs.cls** - Springer LNCS document class


## Acknowledgements

I would like to thank my advisors, Prof. Murray Loew (The George Washington University) and Dr. Elliot Levy (NIH Clinical Center), whose guidance and encouragement have been instrumental throughout the development of this work. 

## Important References

- Kather, J.N., et al.: Multi-class texture analysis in colorectal cancer histology. Sci. Rep. **6**, 27988 (2016)
- Mallat, S.: Group Invariant Scattering. Commun. Pure Appl. Math. **65**(10), 1331-1398 (2012)
- Bruna, J., Mallat, S.: Invariant Scattering Convolution Networks. IEEE Trans. Pattern Anal. Mach. Intell. **35**, 1872-1886 (2013)

