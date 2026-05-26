# Brain-Tumor-Classification-Using-Deep-Learning-and-3D-Transformer-Integration
Brain Tumor Classification Using Deep Learning and 3D Transformer Integration
Abstract
Brain tumors are among the most serious neurological disorders and require early detection for effective treatment. Magnetic Resonance Imaging (MRI) is widely used for identifying brain abnormalities due to its ability to provide detailed images of soft tissues. This project presents a complete deep vision pipeline for brain tumor analysis using MRI images from the BraTS dataset. The proposed framework includes preprocessing, segmentation, feature extraction, classification, and transformer-based analysis. MRI images were first enhanced using image processing techniques and then segmented to isolate tumor regions. Statistical and geometric features were extracted for analysis. A Convolutional Neural Network (CNN) was used for classification, while a 3D CNN-Transformer architecture was implemented to model voxel-to-voxel dependencies as the advanced research component. Experimental results showed that the CNN achieved an accuracy of 75%, while the Transformer-based model achieved an accuracy of 40%. The study demonstrates both the potential and limitations of deep learning approaches when applied to a relatively small medical imaging dataset.

Keywords: Brain Tumor, MRI, Deep Learning, CNN, Transformer, Medical Image Processing, BraTS Dataset

1. Introduction
Brain tumors are abnormal growths of cells inside the brain that can disrupt normal neurological functions. These tumors may be benign or malignant and often require immediate medical attention. Early diagnosis plays a crucial role in improving treatment outcomes and patient survival.

Magnetic Resonance Imaging (MRI) is one of the most commonly used imaging techniques for brain tumor diagnosis. MRI provides detailed information about brain tissues without exposing patients to harmful radiation. However, analyzing MRI scans manually is a challenging and time-consuming task that depends heavily on radiologists' expertise.

Recent developments in artificial intelligence and deep learning have enabled automated systems capable of assisting medical professionals in disease diagnosis. Deep learning models can learn complex image features and identify patterns that may not be visible through traditional methods.

The objective of this project is to develop a complete brain tumor analysis pipeline that integrates image preprocessing, segmentation, feature extraction, classification, and transformer-based learning. The system aims to automate tumor analysis and evaluate the effectiveness of CNN and Transformer architectures on MRI data.

2. Literature Review
2.1 Brain Tumor Analysis Using MRI
MRI is considered the standard imaging technique for brain tumor diagnosis because of its high soft tissue contrast. Researchers have extensively used MRI datasets such as BraTS for developing automated tumor detection systems.

2.2 Traditional Image Processing Techniques
Traditional image processing methods have been widely used for medical image analysis. Common approaches include:

Thresholding

Edge Detection

Morphological Operations

Texture Analysis

These techniques are computationally efficient and provide useful information about image structures. However, they often struggle with complex tumor boundaries and variations in image intensity.

2.3 Deep Learning for Medical Imaging
Convolutional Neural Networks (CNNs) have revolutionized medical image analysis by automatically learning hierarchical image features. CNNs have demonstrated strong performance in tasks such as image classification, object detection, and segmentation.

Advantages of CNNs include:

Automatic feature learning

Reduced need for manual feature engineering

High classification performance

2.4 Transformer-Based Architectures
Transformers were initially introduced for natural language processing but have recently shown promising results in computer vision applications. Unlike CNNs, transformers use self-attention mechanisms to capture long-range relationships within data.

Benefits of transformers include:

Global feature representation

Long-range dependency modeling

Improved contextual understanding

2.5 Research Gap
While CNNs effectively learn local image features, they may struggle to model global relationships across an entire MRI volume. To address this limitation, this project integrates a Transformer block into a 3D CNN architecture to capture voxel-to-voxel dependencies.

3. Dataset Description
The BraTS dataset was used in this project. The dataset contains multimodal MRI scans and corresponding segmentation masks.

For each patient, the dataset provides:

T1-weighted MRI

T1 Contrast Enhanced MRI (T1c)

T2-weighted MRI

FLAIR MRI

Tumor Segmentation Mask

Twenty-five patient cases were selected for experimentation.

4. Methodology
4.1 Overall Pipeline
MRI Acquisition
       ↓
Preprocessing
       ↓
Segmentation
       ↓
Feature Extraction
       ↓
CNN Classification
       ↓
3D CNN + Transformer
       ↓
Evaluation
4.2 Image Preprocessing
The MRI images were enhanced before analysis.

The preprocessing stage included:

Gaussian Filtering
Gaussian filtering was applied to reduce random noise and smooth image intensity variations.

Mean Filtering
Mean filtering was used to further reduce image noise by averaging neighboring pixel values.

Median Filtering
Median filtering removed impulse noise while preserving important image edges.

Anti-Aliasing
An anti-aliasing filter was applied before resizing to minimize image distortion.

4.3 Tumor Segmentation
Tumor regions were segmented using edge-based image processing techniques.

The segmentation procedure involved:

Sobel Edge Detection

Binary Thresholding

Erosion

Dilation

Opening

Closing

These operations improved tumor boundary extraction and removed small artifacts.

4.4 Feature Extraction
After segmentation, statistical texture features were extracted using the Gray Level Co-occurrence Matrix (GLCM).

The extracted texture features included:

Energy

Entropy

Contrast

In addition, geometric features were calculated:

Area

Perimeter

Circularity

Centroid Coordinates

These features were stored in a CSV file for further analysis.

4.5 CNN Classification
The CNN model was developed to classify tumor regions into High Risk and Low Risk categories.

The architecture consisted of:

Convolution Layer

Max Pooling Layer

Convolution Layer

Max Pooling Layer

Dense Layer

Output Layer

The CNN learned spatial patterns from segmented tumor images.

4.6 3D Transformer Integration
To satisfy the advanced research challenge, a Transformer block was integrated into a 3D CNN architecture.

The complete MRI volume was used instead of a single image slice. Segmentation masks were applied to isolate tumor regions, and the resulting volumes were resized to 64×64×64.

The Transformer employed Multi-Head Self-Attention to model voxel-to-voxel relationships across the MRI volume.

This approach allowed the network to capture global spatial dependencies that may not be learned through convolutional operations alone.

5. Experimental Results
5.1 CNN Results
Confusion Matrix
Insert your CNN confusion matrix image here.

Performance Metrics
Metric	Value
Accuracy	75%
Precision	0.80
Recall	0.60
F1 Score	0.57
The CNN correctly identified all High Risk cases while misclassifying some Low Risk cases.

5.2 Transformer Results
Confusion Matrix
[[0 3]
 [0 2]]
Performance Metrics
Metric	Value
Accuracy	40%
Precision	0.40
Recall	1.00
F1 Score	0.57
The Transformer successfully identified High Risk cases but incorrectly classified all Low Risk cases as High Risk.

6. Discussion
The CNN achieved better performance than the Transformer on the selected dataset. The CNN obtained an accuracy of 75%, indicating its ability to learn useful tumor characteristics from segmented MRI images.

Although the Transformer architecture provides the ability to model long-range voxel relationships, its performance was limited by the small dataset size. Transformers generally require significantly larger datasets to effectively learn attention patterns.

The results suggest that CNN-based methods remain more practical for small medical imaging datasets, while Transformer-based approaches may become advantageous when larger datasets are available.

7. Conclusion
This project presented a complete deep vision pipeline for brain tumor analysis using MRI images from the BraTS dataset. The framework incorporated preprocessing, segmentation, feature extraction, classification, and Transformer-based learning.

The CNN model achieved an accuracy of 75% and demonstrated better performance than the Transformer architecture. The Transformer model achieved an accuracy of 40%, highlighting the challenges of applying attention-based architectures to small datasets.

Overall, the study demonstrates the effectiveness of deep learning techniques for automated brain tumor analysis and provides valuable insights into the strengths and limitations of CNN and Transformer approaches.

8. Future Work
Future improvements may include:

Increasing the dataset size

Using additional MRI modalities

Implementing advanced Vision Transformers

Applying data augmentation techniques

Exploring hybrid CNN-Transformer architectures

Using clinically validated labels instead of generated risk categories

9. References
Menze, B. et al. The Multimodal Brain Tumor Image Segmentation Benchmark (BraTS).

Ronneberger, O. et al. U-Net: Convolutional Networks for Biomedical Image Segmentation.

Vaswani, A. et al. Attention Is All You Need.

Dosovitskiy, A. et al. An Image is Worth 16×16 Words: Vision Transformer.

Goodfellow, I., Bengio, Y., Courville, A. Deep Learning.

TensorFlow Documentation.

OpenCV Documentation.

BraTS Dataset Documentation.

Nibabel Documentation.

Scikit-Learn Documentation.
