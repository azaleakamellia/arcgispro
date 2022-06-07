# 🚀 Image classification using ArcGIS Deep Learning Framework

###### tags: `how-to` `spatially` `arcgis pro`
---------------------------
This note is a quick and dirty guideline to executing the **ArcGIS Deep Learning Framework** in the ArcGIS Pro platform using solely the GUI interface of the software. Although the usage of Jupyter Notebook is available, a soft introduction using the GUI is better to ensure basic understanding of the processes involved when running the framework.

The notes will continuously be updated to include the issues a user may encounter and the workaround or solutions users can implement to enable access and operation promptly. 

Before you attempt to proceed, please ensure that you have fulfill the machine specifications required to undertake the task of training a deep learning model. 

Here are the important steps to take note:

1. Installation
2. Model training
3. Model inferencing

--------------------------
## 1️⃣ Installation

Prior to committing, please ensure that your machines meet the specifications needed to train a deep learning model:

### **Step 1**
Download and setup the following softwares.
- [ ] Python 3.0 and above
    - Refer to:
        - [Python download](https://www.python.org/downloads/)
- [ ] NVIDIA driver, CUDA and cuDNN toolkit
    - Refer to: 
        - [Installing cuDNN in Windows](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#install-windows) 
        - [Setting up CUDA, CUDNN, Keras and TensorFlow on Windows 11 for GPU Deep Learning](https://youtu.be/OEFKlRSd8Ic)
- [ ] ArcGIS Pro 2.8 or 2.9
    - Refer to:
        - [Install ArcGIS Pro](https://pro.arcgis.com/en/pro-app/2.8/get-started/install-and-sign-in-to-arcgis-pro.htm)

### **Step 2**

After ensuring that the software specifications are fulfilled, you can proceed to install the framework via software or Python. Formal documentation on the procedures of installation can be accessed at their GitHub page  🔗 [Esri/deep-learning-frameworks](https://github.com/Esri/deep-learning-frameworks/blob/master/README.md?rmedium=links_esri_com_b_d&rsource=https%3A%2F%2Flinks.esri.com%2Fdeep-learning-framework-install).

> ⚡ **NOTE**
> Ensure that the **Deep Learning Framework** version matches the ArcGIS Pro version before installation or the framework won't be available for usage.


> 💀 **WARNING**
> This process is long and arduous as well as **COMPLICATED**. It is highly dependent on your machine specifications and built and is an iterative process. You are advised to take it easy and not give up. 

<br />

### **Step 3**
Proceed to check the success of the installation by running your ArcGIS Pro and search for deep learning tools as outlined below under the `Geoprocessing` tab or panel.

- **Imagery** tab > **Image Classification** group > **Classification Tools** dropdown > [**Label Objects for Deep Learning**](https://pro.arcgis.com/en/pro-app/2.8/tool-reference/image-analyst/export-training-data-for-deep-learning.htm) button
- [**Export Training Data For Deep Learning**](https://pro.arcgis.com/en/pro-app/2.8/tool-reference/image-analyst/export-training-data-for-deep-learning.htm) tool 
- [**Classify Pixels Using Deep Learning**](https://pro.arcgis.com/en/pro-app/2.8/tool-reference/image-analyst/classify-pixels-using-deep-learning.htm) tool

Proper installation of this framework will result in the enabling of the tools mentioned.

<br />

## 2️⃣ Model training
The data needed are:
- [ ]  Satellite images; Landsat 8 or Sentinel-2A
    - Browse and download them at [USGS Earth Explorer](https://earthexplorer.usgs.gov/)...creating a public account needed. 
- [ ] Shapefile of existing land use/classes
    - For fun, you can shapefiles of different country up to the regional levels at [GADM Maps and Data](https://gadm.org/index.html)

### **Step 1: Prepare training data**
1. Ensure that the features you are trying to classify are enhanced during your image processing stage; NDVI, NDBI, NDWI etc., and the image itself is factored properly. You can find compilation of interesting spectral indices and band combinations at [Awesome Spectral Indices](https://github.com/awesome-spectral-indices/awesome-spectral-indices).

2. In the case where the shapefile containing the land classes or land uses are not available, you can proceed to start labeling objects in the image that you have processed based on the classes you have created using **Label Objects for Deep Learning** tool. This is a common remote sensing procedure that is time-consuming. 

3. Please refer to the following link for more information: 
    > 🔗 [Label objects for deep learning](https://pro.arcgis.com/en/pro-app/2.8/help/analysis/image-analyst/label-objects-for-deep-learning.htm)

4. After labeling and collecting the training data, you will need to export the data into a form that can be ingested within the deep learning framework. The tool needed is the **Export Training Data for Deep Learning** geoprocessing tool. 
    > ⛔ NOTE
    > - The output from this tool are two folders containing image chips and their corresponding labels which can be used for deep learning model training in other deep learning environment that uses PyTorch or TensorFlow. 
    > - This process can take a long time dependent on your machine's specifications as well as the number of training chips/resolution.


<br />
### 3️⃣ Training a model
Once the data has been exported, you can proceed to train the deep learning model. This is the part where you will find various deep learning models that you would want to use. In this exercise, we are interested in pixel classification or semantic segmentation. Some of the models are such as the infamoust UNet and DeepNet. The tool you need to use is the **Train Deep Learning Model** geoprocessing tool. Please refer to the following link for more information:

> 🔗 [Train Deep Learning Model](https://pro.arcgis.com/en/pro-app/2.8/tool-reference/image-analyst/train-deep-learning-model.htm)
