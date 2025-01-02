# Low-Grade-Glioma-Segmentation

## A. Business Understanding

This is a project on a real dataset related to segmenting low-grade glioma. [Here is the Jupyter Notebook] (https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Low-grade-glioma-segmentation.ipynb)

### A.1 What is the low-grade glioma?

Low-grade glioma is a type of brain tumor that is classified as a grade II and III tumor on the World Health Organization (WHO) grading scale and arises from the supporting cells of the brain called glial cells. They are generally benign but can cause significant neurological symptoms as they grow and put pressure on the surrounding brain tissue. They are most common in adults, but can also occur in children. These tumors are typically treated with surgery, radiation therapy, or a combination of both. In some cases, they may also be observed with close monitoring if the patient is asymptomatic. It is important to note that low-grade gliomas can progress over time to higher-grade tumors, so patients need to undergo regular monitoring to detect any changes in the tumor.

Low-grade glioma segmentation is the process of identifying and separating the tumor tissue from the surrounding healthy tissue in magnetic resonance imaging (MRI) scans of the brain.

### Why deep learning should be used?

Deep learning has proven to be an effective tool for this task, as it allows for the accurate identification of tumor boundaries in MRI scans. Without the use of deep learning, segmentation of low-grade gliomas can be difficult, time-consuming, and subject to inter- and intra-observer variability, as it often requires manual annotation by radiologists. However, the segmentation of low-grade glioma can be challenging due to their infiltrative nature and similarity in appearance to surrounding brain tissue. Additionally, traditional methods may not be as accurate as deep learning, leading to potential misdiagnosis and improper treatment.
    As a result, there is a need for accurate and efficient methods for low-grade glioma segmentation to improve patient outcomes. Deep learning-based solutions can improve the efficiency and accuracy of low-grade glioma segmentation, leading to better patient outcomes and cost savings for healthcare providers.


## B. Data Understanding

The Brain Magnetic Resonance Imaging (MRI) segmentation dataset is obtained from The Cancer Imaging Archive (TCIA). The dataset contains Brain MRI Images together with manual fluid-attenuated inversion recovery (FLAIR)  abnormality segmentation masks. They correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection with at least fluid-attenuated inversion recovery (FLAIR) sequence and genomic cluster data available.

| Low Grade Glioma Without Segmentation                                                                                                                                                                                             | Low Grade Glioma With Segmentation                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Glioma - Low Grade - Case 1 Without Segmentation](https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/low-grade-glioma-grade-1-without-segmentation.png?raw=true) <br/>*This image belongs to a 24-year-old man who developed focal seizures affecting the left side of his body.* | ![Glioma - Low Grade - Case 1 With Segmentation](https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/low-grade-glioma-grade-1-with-segmentation.png?raw=true) <br/>*This image belongs to a 24-year-old man who developed focal seizures affecting the left side of his body.<br/>The red area indicates low grade glioma.* |

## C. Data Preparation

This dataset is a table of 110 rows and 18 columns. Each row represents a patient, and the columns contain various information about the patient such as RNASeqCluster, MethylationCluster, miRNACluster, CNCluster, RPPACluster, OncosignCluster, COCCluster and histological_type, neoplasm_histologic_grade, tumor_tissue_site, laterality, tumor_location, gender, age_at_initial_pathologic, race, ethnicity, death. Each column has a specific data type: object, float64, and int64. The first column "Patient" is of object data type, 15 columns are of float64 data type and 2 columns are of int64 data type. There are missing values in some of the columns which are represented by a "non-null" count in the Data columns section.


<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/Information%20about%20csv%20dataset.png?raw=true">
  <br>
  <em>Figure 3- Information about csv dataset</em>
</p>


<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/the%20head%20of%20the%20csv%20dataset.png?raw=true">
  <br>
  <em>Figure 4 - The head of the csv dataset</em>
</p>

<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/the%20final%20dataframe%20to%20be%20used%20in%20the%20visualization%20and%20modeling%20part.png?raw=true">
  <br>
  <em>Figure 5 - The final dataframe to be used in the visualization and modeling part</em>
</p>

## D. visualization

The visualization part takes place in two stages. The first state involves displaying in distribution in different ways. The second stage involves the visualization of Brain MRI Images in different ways.

### D.1 Distribution

<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/Distribution%20of%20data%20grouped%20by%20diagnosis.png?raw=true">
  <br>
  <em>Figure 6 - Distribution of data grouped by diagnosis</em>
</p>

This data shows the distribution of images grouped by diagnosis. The data is split into two groups, “positive” and “negative”. The “positive” group contains 2256 images, which represents 65.05% of the total images. The “negative” group contains 1373 images, which represents 34.95% of the total images. In total, there are 3929 images in the dataset. 

<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/Distribution%20of%20data%20grouped%20by%20patient%20and%20diagnosis.png?raw=true">
  <br>
  <em>Figure 7 - Distribution of data grouped by patient and diagnosis</em>
</p>

Both distributions indicate that there are more positive images than negative images, which could have implications for the performance of any deep learning models trained on this data. For example, if the majority of the data is positive, the model may be more likely to predict a positive diagnosis even when the image is actually negative. Therefore, data augmentation does with these distributions when analyzing or interpreting the results of any deep learning models trained on this data.

### D.2 Visualization of Brain MRI Images

Original color and the hot color map  used in the visualization of brain MRI images. The main reason why this colormap is important is that it can effectively highlight different tissue types in the brain based on their MRI intensities. The hot color maps low-intensity values to dark colors (black) and high-intensity values to bright colors (red, yellow, and white). This helps to distinguish different structures in the brain such as grey matter, white matter, and cerebrospinal fluid. 

Additionally, the hot colormap is also useful in differentiating between healthy and abnormal tissue, such as tumors. Tumors often have different intensity values compared to the surrounding healthy tissue and using a colormap like hot can help to highlight these differences and make them more visible. This can be helpful for radiologists and physicians when analyzing the images and can be useful in determining the diagnosis and treatment of the patient. 

It is important to note that the choice of colormap is not only important for visualizing the data but also for the analysis of the data, for example in brain tumor segmentation tasks, the choice of colormap will be important to define the threshold values for the segmentation algorithm.

<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/Low%20Grade%20Glioma%20Detection%20on%20Brain%20MRI%20Images%20with%20original%20color%20and%20hot%20colormap.png?raw=true">
  <br>
  <em>Figure 8 - Low Grade Glioma Detection on Brain MRI Images wit original color and hot colormap</em>
</p>

This diagram shows the representation of different images, positive and negative, under two different color scales. (Original color and hot colormap) Positive images using a hot colormap show where the tumor is more black or more white.

<p align="center">
  <img src="https://github.com/Abirouk/Low-Grade-Glioma-Segmentation/blob/main/Pictures/Tumor%20location%20is%20show%20as%20segmented%20on%20one%20Brain%20MRI.png?raw=true">
  <br>
  <em>Figure 9 - Tumor location as segmented on a Brain MRI image</em>
</p>
