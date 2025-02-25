# **Machine Learning Method for Pancreatic Cancer Detection using Naïve Bayes and Decision Tree Algorithm**  

## **Introduction**  
Pancreatic cancer is one of the most aggressive and deadliest cancers due to its **late-stage diagnosis and lack of early symptoms**. The five-year survival rate for pancreatic cancer remains **as low as 9%**, making early detection critical for improving patient outcomes. Traditional diagnostic methods rely on **MRI scans and biopsy results**, but these approaches are often time-consuming, expensive, and require expert radiologists.  

To address these challenges, this paper presents a **machine learning-based approach** that **automates pancreatic tumor detection** using MRI images. By leveraging **image processing techniques** and **classification algorithms**, we aim to enhance the **efficiency, accuracy, and speed** of pancreatic cancer diagnosis.  

## **Proposed System**  
Our proposed system focuses on **detecting pancreatic tumors in MRI images** using **machine learning techniques**. The process involves the following steps:  
1. **Preprocessing MRI images** using **Discrete Wavelet Transform (DWT)** to remove noise.  
2. **Segmenting the tumor region** using **Fuzzy C-Means Clustering (FCM)**.  
3. **Extracting texture-based features** from the images using **Gray-Level Co-occurrence Matrix (GLCM)**.  
4. **Classifying the tumor as malignant or normal** using **Naïve Bayes and Decision Tree classifiers**.  

This approach **enhances the efficiency of cancer diagnosis**, reduces **human error**, and helps in the **early detection of tumors**, which is crucial for effective treatment.  

---

## **System Architecture**  
The system architecture consists of **three main phases**:  

### **1. Preprocessing Phase**  
In this phase, the raw MRI images are **enhanced and denoised** to improve feature extraction and classification accuracy.  
- **Noise Removal using Discrete Wavelet Transform (DWT)**  
  - MRI images often contain noise due to **human error, machine limitations, or environmental factors**.  
  - **DWT decomposes the image into multiple sub-bands**, filtering out unwanted noise while preserving important features.  
  - This process improves image quality, making it easier to detect the tumor.  
  - The wavelet transform **scales and translates** the image for better segmentation.  

- **Thresholding Techniques**  
  - **Soft Thresholding**: Reduces coefficients **closer to zero** to suppress noise.  
  - **Hard Thresholding**: Eliminates coefficients **below a fixed threshold** while keeping the rest unchanged.  

---

### **2. Feature Extraction Phase**  
To analyze the texture of the MRI image, we use the **Gray-Level Co-occurrence Matrix (GLCM)**. GLCM is a powerful statistical technique that extracts **second-order texture features** from an image.  

#### **Extracted Features**  
1. **Angular Second Moment (ASM) / Energy**  
   - Measures image uniformity.  
   - Formula:  
     \[
     ASM = \sum_i \sum_j (p_{ij})^2
     \]
     \[
     Energy = \sqrt{ASM}
     \]
  
2. **Entropy**  
   - Measures randomness in pixel distribution.  
   - Formula:  
     \[
     Entropy = - \sum_i \sum_j p_{ij} \log_2 (p_{ij})
     \]

3. **Contrast**  
   - Measures the intensity variation between neighboring pixels.  
   - Formula:  
     \[
     Contrast = \sum_i \sum_j (i - j)^2 p_{ij}
     \]

4. **Homogeneity (Inverse Difference Moment)**  
   - Measures **smoothness** of the texture.  
   - Formula:  
     \[
     Homogeneity = \sum_i \sum_j \frac{1}{1 + (i - j)^2} p_{ij}
     \]

5. **Variance**  
   - Measures deviation from the mean intensity.  
   - Formula:  
     \[
     Variance = \sum_i \sum_j (i - \mu)^2 p_{ij}
     \]
     where \( \mu \) is the mean intensity.

6. **Dissimilarity**  
   - Measures the **difference in intensity values** between neighboring pixels.  
   - Formula:  
     \[
     Dissimilarity = \sum_i \sum_j |i - j| p_{ij}
     \]

---

### **3. Classification Phase**  
In this phase, the extracted features are **fed into machine learning classifiers** to determine whether the tumor is **malignant (cancerous)** or **normal**.

#### **A. Naïve Bayes Classifier**  
- Based on **Bayes’ Theorem**, which calculates the **posterior probability** of a tumor being cancerous given the observed features.  
- Works under the assumption that all features are **independent** (even though this is not always true).  
- The **likelihood** of each feature is computed, and the class with the highest probability is assigned.  

##### **Steps Involved**:  
1. Construct a **frequency table** for each feature.  
2. Create a **likelihood table** based on feature distributions.  
3. Load and preprocess the data from the **CSV dataset**.  
4. Split the dataset into **training (75%)** and **testing (25%)** sets.  
5. Calculate probabilities and classify the image as **malignant or normal**.  

---

#### **B. Decision Tree Classifier**  
- Works by **recursively splitting** the dataset based on feature values.  
- Uses **if-else conditions** at each node to determine whether an image belongs to a certain class.  

##### **Steps Involved**:  
1. **Root Node** receives the dataset.  
2. Each **node asks a question** (e.g., "Is contrast > threshold?").  
3. Data is **split into subsets** based on the answer (True/False).  
4. The process continues recursively until a **leaf node** is reached (final classification).  

##### **Key Concepts in Decision Trees**  
- **Gini Impurity**: Measures the degree of uncertainty at a node.  
  \[
  Gini = 1 - \sum p_i^2
  \]
- **Information Gain**: Measures how much uncertainty is **reduced** after a split.  
  \[
  IG = Initial\ Uncertainty - Weighted\ Average\ of\ Child\ Uncertainty
  \]

The decision tree outputs **Malignant or Normal** classification.

---

## **Results & Model Performance**  
- The **Fuzzy C-Means Clustering (FCM)** method was used for tumor segmentation.  
- The **Naïve Bayes and Decision Tree models achieved 70% accuracy**.  
- **75% of data** was used for training, and **25% was used for testing**.  
- The system successfully detected tumors in MRI images, but accuracy needs further improvements.  

---

## **Conclusion & Future Work**  
### **Conclusion**  
- **Machine learning techniques** can **automate pancreatic tumor detection**, reducing reliance on expert radiologists.  
- **Naïve Bayes and Decision Tree classifiers** effectively distinguish between **malignant and normal tumors**.  
- The **accuracy of the model was 70%**, indicating that further optimizations are needed.  
