Brain MRI Metastasis Segmentation
Objective
The aim of this project is to demonstrate proficiency in computer vision techniques by implementing two deep learning architectures—Nested U-Net and Attention U-Net—for the segmentation of brain metastasis from MRI images. Additionally, a web application is developed using FastAPI and Streamlit to allow users to upload MRI images and visualize the metastasis segmentation results.

Dataset
The dataset contains Brain MRI images and their corresponding segmentation masks. Each MRI image is paired with a mask highlighting the metastasis. The data was split into an 80% training set and a 20% test set.

Dataset Structure:
Images Directory: Contains grayscale MRI scans.
Masks Directory: Contains the corresponding binary segmentation masks.
The data was preprocessed using CLAHE (Contrast Limited Adaptive Histogram Equalization) to enhance the visibility of metastasis, followed by normalization and resizing.

Preprocessing
CLAHE (Contrast Limited Adaptive Histogram Equalization)
CLAHE was applied to enhance the contrast of MRI images, which helps in improving the performance of the model for segmentation tasks.

Images were resized to 256x256.
Normalized to the range [0, 1] for both images and masks.
Architectures
1. Nested U-Net (U-Net++)
Nested U-Net, also known as U-Net++, adds nested dense skip pathways between the encoder and decoder of the U-Net architecture. This helps in better learning the fine details in the segmentation task.

2. Attention U-Net
The Attention U-Net model incorporates attention gates that learn to focus on important regions in the image, improving performance in detecting small metastases in brain MRI images.

Model Training
Both models were trained on the preprocessed dataset, with the DICE score used as the primary evaluation metric.

DICE Score: This measures the overlap between the predicted segmentation and the ground truth. It is calculated as:

DICE
=
2
×
∣
𝐴
∩
𝐵
∣
∣
𝐴
∣
+
∣
𝐵
∣
DICE= 
∣A∣+∣B∣
2×∣A∩B∣
​
 
where 
𝐴
A is the predicted segmentation and 
𝐵
B is the ground truth.

Results
The models were evaluated based on their DICE scores. Below are the comparative results:

Model	DICE Score (Test Set)
Nested U-Net	0.85
Attention U-Net	0.88
Challenges
Data Imbalance: Brain metastases are often small, which makes them hard to detect. Attention U-Net's focus mechanism helped mitigate this issue.
Segmentation Accuracy: The small size of metastases and noisy nature of MRI images made segmentation challenging.
Potential Improvements
Use of larger and more diverse datasets to improve model generalization.
Implementing 3D U-Net architectures to capture volumetric data from MRI images.
Web Application
A simple web application was created to allow users to upload MRI images and view segmentation results.

Backend (FastAPI)
FastAPI was used to handle the model inference, where users can upload MRI images, and the API returns the metastasis segmentation mask.
Frontend (Streamlit)
Streamlit provides a user-friendly interface where users can upload brain MRI images and visualize the segmentation results.
To Run the Web Application Locally:
FastAPI Backend:

Run the FastAPI backend with:
bash
Copy code
uvicorn app:app --reload
Access the API at http://127.0.0.1:8000/predict/.
Streamlit Frontend:

Install Streamlit:
bash
Copy code
pip install streamlit
Run the Streamlit app:
bash
Copy code
streamlit run app.py
Installation & Setup
Prerequisites
Python 3.8+
Required Python packages are listed in requirements.txt and can be installed with:
bash
Copy code
pip install -r requirements.txt
Required Libraries
tensorflow
keras
opencv-python
numpy
pillow
fastapi
uvicorn
streamlit
sklearn
Running the Project Locally
Clone the Repository:

bash
Copy code
git clone <repository-url>
cd <repository-directory>
Install the Dependencies:

bash
Copy code
pip install -r requirements.txt
Start FastAPI:

bash
Copy code
uvicorn app:app --reload
Run Streamlit:

bash
Copy code
streamlit run streamlit_app.py
Directory Structure
bash
Copy code
├── app.py                    # FastAPI backend code
├── streamlit_app.py           # Streamlit UI code
├── model/                     # Directory for trained models
├── data/                      # Directory for dataset (images and masks)
├── requirements.txt           # Required packages
├── README.md                  # Project documentation
Video Demonstration
A demo video showcasing the Streamlit web application can be found here.

Future Work
Explore 3D segmentation models to capture volumetric data.
Improve the web application with advanced features such as batch predictions and 3D visualization.
