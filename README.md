# Brain-Tumor-Classification-Using-Deep-Learning-and-3D-Transformer-Integration
Brain Tumor Classification Using Deep Learning and 3D Transformer Integration
Abstract
Brain tumors are among the most serious neurological disorders and require early detection for effective treatment. Magnetic Resonance Imaging (MRI) is widely used for identifying brain abnormalities due to its ability to provide detailed images of soft tissues. This project presents a complete deep vision pipeline for brain tumor analysis using MRI images from the BraTS dataset. The proposed framework includes preprocessing, segmentation, feature extraction, classification, and transformer-based analysis. MRI images were enhanced using image processing techniques and segmented to isolate tumor regions. Statistical texture features and geometric features were extracted for analysis. Three classification approaches were evaluated: Random Forest, Convolutional Neural Network (CNN), and a 3D CNN-Transformer architecture. Experimental results showed that the Random Forest classifier achieved an accuracy of 87.5%, the CNN achieved 80%, and the Transformer-based model achieved 40%. The results demonstrate that traditional machine learning and CNN-based approaches are more effective for small medical imaging datasets, while Transformer architectures generally require larger datasets for optimal performance.

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
The CNN model was developed to classify tumor regions into High Risk and Low Risk categories. Labels were generated using the median tumor area extracted from the segmented tumor regions.

To improve model performance and reduce overfitting, the CNN architecture was enhanced through:

• Data Augmentation

• Batch Normalization

• Early Stopping

• Dropout Regularization

• Larger Convolution Filters (5×5)

The final CNN architecture consisted of:

• Data Augmentation Layer

• Conv2D (32 Filters, 5×5)

• Batch Normalization

• Max Pooling Layer

• Conv2D (64 Filters, 5×5)

• Batch Normalization

• Max Pooling Layer

• Conv2D (128 Filters, 5×5)

• Batch Normalization

• Max Pooling Layer

• Dense Layer (128 Neurons)

• Dropout Layer (0.5)

• Output Layer (Sigmoid Activation)

Data augmentation included image rotation, zooming, flipping, and translation. Early Stopping was used to prevent overfitting and restore the best-performing model weights.

4.6 3D Transformer Integration
To satisfy the advanced research challenge, a Transformer block was integrated into a 3D CNN architecture.

The complete MRI volume was used instead of a single image slice. Segmentation masks were applied to isolate tumor regions, and the resulting volumes were resized to 64×64×64.

The Transformer employed Multi-Head Self-Attention to model voxel-to-voxel relationships across the MRI volume.

This approach allowed the network to capture global spatial dependencies that may not be learned through convolutional operations alone.

Batch Normalization and Early Stopping were incorporated to improve training stability. Experiments were also conducted with different attention head configurations and dense layer sizes to evaluate the effect of model complexity on performance.

5. Experimental Results
5.1 CNN Results
Performance Metrics

Metric	Value
Accuracy	80.0%
Training Samples	20
Validation Samples	5
Correct Predictions	4
Incorrect Predictions	1

The enhanced CNN model achieved an accuracy of 80% on the validation dataset. The integration of Data Augmentation, Batch Normalization, Early Stopping, Dropout, and larger convolution filters improved model stability and reduced overfitting. Despite the limited dataset size, the CNN successfully learned meaningful tumor characteristics from MRI images.

5.2 Transformer Results
Confusion Matrix
[[0 3]
[0 2]]

Performance Metrics

Metric	Value
Accuracy	40.0%
Precision	0.40
Recall	1.00
F1 Score	0.57

The Transformer-based model classified all validation samples as High Risk, resulting in poor classification of Low Risk cases. Although the self-attention mechanism successfully captured global voxel relationships, the model was unable to generalize effectively because of the limited dataset size.


6. Discussion
Classification Performance Comparison

Model	Accuracy
Random Forest	87.5%
CNN	80.0%
3D CNN + Transformer	40.0%

The Random Forest classifier achieved the highest accuracy of 87.5%. This performance can be attributed to the effectiveness of the extracted GLCM texture features and geometric features used for classification.

The CNN achieved an accuracy of 80%. The addition of Data Augmentation, Batch Normalization, Early Stopping, Dropout, and larger convolution filters improved training stability and reduced overfitting. These enhancements enabled the network to learn discriminative tumor features despite the limited dataset size.

The Transformer-based model achieved only 40% accuracy. Although Transformers are capable of modeling global relationships through self-attention mechanisms, they generally require significantly larger datasets. With only 25 MRI cases available, the Transformer struggled to learn effective feature representations and tended to predict a single class.

These results demonstrate that increasing model complexity does not always improve performance. For small medical imaging datasets, traditional machine learning and CNN-based approaches may outperform Transformer-based architectures.


7. Conclusion
This project presented a complete brain tumor analysis pipeline using MRI images from the BraTS dataset. The framework incorporated preprocessing, segmentation, feature extraction, classification, and Transformer-based learning.

MRI images were enhanced using Gaussian filtering, mean filtering, median filtering, anti-aliasing, and resizing techniques. Tumor regions were segmented using Sobel edge detection and morphological operations. Statistical texture features and geometric features were extracted and stored for analysis.

Three classification approaches were evaluated:

• Random Forest Classifier

• Convolutional Neural Network (CNN)

• 3D CNN + Transformer

The Random Forest classifier achieved the highest accuracy of 87.5%, followed by the CNN with 80.0% accuracy. The Transformer-based model achieved 40.0% accuracy because of the limited dataset size.

The study demonstrates that traditional machine learning and CNN-based approaches remain highly effective for small medical imaging datasets, while Transformer architectures generally require larger datasets to achieve their full potential.

8. Future Work
Future improvements may include:

• Increasing the dataset size

• Using additional MRI modalities

• Implementing advanced Vision Transformers

• Applying data augmentation techniques

• Exploring hybrid CNN-Transformer architectures

• Using clinically validated labels instead of generated risk categories

• Investigating transfer learning and pretrained medical imaging models for improved performance on limited datasets.

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
