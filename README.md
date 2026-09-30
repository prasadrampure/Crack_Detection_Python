# Crack_Detection_Python
# Marvellous CNN - Industrial Surface Crack Detection

## 📌 Project Overview

This project implements an **Industrial Surface Crack Detection System using a Convolutional Neural Network (CNN)**.

The system takes surface images as input and classifies them into two categories:

- **Crack**
- **No Crack**

The project includes dataset preparation, image preprocessing, data augmentation, CNN model training, validation, testing, performance evaluation, confusion matrix, classification report, model saving, and single-image prediction.

## 🎯 Objectives

- Detect cracks from industrial surface images.
- Automatically classify images as **Crack** or **No Crack**.
- Build a CNN-based image classification model.
- Apply image preprocessing and augmentation.
- Evaluate the trained model using unseen test data.
- Generate a confusion matrix and classification report.
- Perform prediction on an individual image.

## 🛠️ Technologies Used

- Python
- TensorFlow
- Keras
- NumPy
- Matplotlib
- Scikit-learn
- OpenCV
- Convolutional Neural Network (CNN)

## 📂 Project Structure

```text
Marvellous_CNN_Surface_Crack_Detection/
│
├── CrackDataset/
│   ├── Positive/
│   │   ├── image1.jpg
│   │   ├── image2.jpg
│   │   └── ...
│   │
│   └── Negative/
│       ├── image1.jpg
│       ├── image2.jpg
│       └── ...
│
├── Marvellous_CNN.py
├── Marvellous_Realtime_Image_Classification.py
├── README.md
└── requirements.txt

The program automatically creates:

Processed_CrackDataset/
│
├── train/
│   ├── Crack/
│   └── NoCrack/
│
├── validation/
│   ├── Crack/
│   └── NoCrack/
│
└── test/
    ├── Crack/
    └── NoCrack/
🔄 Project Workflow
                 Original Dataset
                       │
                       ▼
                Check Dataset
                       │
                       ▼
              Positive / Negative
                       │
                       ▼
             Dataset Splitting
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
        Train      Validation      Test
          │            │            │
          ▼            ▼            ▼
       Image        Image          Image
    Augmentation  Normalization  Normalization
          │            │            │
          └────────────┼────────────┘
                       ▼
                   CNN Model
                       │
                       ▼
                 Model Training
                       │
                       ▼
                 Model Evaluation
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      Accuracy       Loss       Classification
                                  Report
                       │
                       ▼
              Crack / No Crack
📊 Dataset

The project expects two folders inside CrackDataset:

CrackDataset/
├── Positive/
└── Negative/

The folders are mapped as:

Positive → Crack
Negative → NoCrack

Supported image formats:

.jpg
.jpeg
.png
.bmp
.webp

📈 Dataset Splitting

The dataset is divided into:

70% Training
15% Validation
Approximately 15% Testing

A random seed of 42 is used for reproducibility.

🖼️ Image Preprocessing

Every image is resized to:
128 × 128

The CNN input shape is:
128 × 128 × 3

Batch size:
32

Maximum training epochs:
15

Pixel values are normalized from approximately:
0 - 255
to:
0 - 1

🔧 Data Augmentation

Training images use:

Rotation
Zoom
Width shifting
Height shifting
Horizontal flipping

Training configuration:

ImageDataGenerator(
    rescale=1.0 / 255,
    rotation_range=15,
    zoom_range=0.2,
    width_shift_range=0.1,
    height_shift_range=0.1,
    horizontal_flip=True
)

Validation and test images use pixel normalization without augmentation.

🧠 CNN Architecture

The project uses a Keras Sequential CNN model.

Convolution Block 1
Conv2D
32 Filters
3 × 3 Kernel
ReLU Activation
Batch Normalization
Max Pooling
Convolution Block 2
Conv2D
64 Filters
3 × 3 Kernel
ReLU Activation
Batch Normalization
Max Pooling
Convolution Block 3
Conv2D
128 Filters
3 × 3 Kernel
ReLU Activation
Batch Normalization
Max Pooling
Convolution Block 4
Conv2D
256 Filters
3 × 3 Kernel
ReLU Activation
Batch Normalization
Max Pooling

🔗 Fully Connected Layers

After the convolution layers:

Flatten
   ↓
Dense(256, ReLU)
   ↓
Dropout(0.5)
   ↓
Dense(128, ReLU)
   ↓
Dropout(0.3)
   ↓
Dense(1, Sigmoid)

The final sigmoid layer is used for binary classification.

⚙️ Model Compilation

The model uses:

Optimizer      : Adam
Loss Function  : Binary Crossentropy
Metric         : Accuracy

Model compilation:

model.compile(
    optimizer="adam",
    loss="binary_crossentropy",
    metrics=["accuracy"]
)

⏱️ Training Callbacks

The project uses three callbacks.

1. EarlyStopping

Monitors:
val_loss

Configuration:
patience = 4
restore_best_weights = True

2. ModelCheckpoint

The best model based on validation accuracy is saved as:

Best_Crack_Detection_Model.keras
3. ReduceLROnPlateau

Configuration:

factor = 0.2
patience = 2
min_lr = 0.00001

🚀 How to Run the Project
Step 1: Clone the Repository
git clone https://github.com/your-username/Marvellous_CNN_Surface_Crack_Detection.git
Step 2: Open the Project
cd Marvellous_CNN_Surface_Crack_Detection
Step 3: Install Dependencies
pip install tensorflow
pip install numpy
pip install matplotlib
pip install scikit-learn
pip install opencv-python

Or:

pip install -r requirements.txt
▶️ Train the CNN Model

Run:

python Marvellous_CNN.py

The program performs:

Dataset checking
Dataset splitting
Image preprocessing
Data augmentation
Sample image display
CNN model creation
Model training
Accuracy graph generation
Loss graph generation
Test evaluation
Confusion matrix generation
Classification report generation
Model saving
Single-image prediction

📈 Training Accuracy

The project generates a graph showing:

Training Accuracy
Validation Accuracy

This graph shows the change in model accuracy across training epochs.

📉 Training Loss

The project generates a graph showing:

Training Loss
Validation Loss

This graph shows the change in model loss during training.

🧪 Model Evaluation

After training, the model is evaluated on the unseen test dataset.

The program displays:

Test Loss
Test Accuracy

📊 Confusion Matrix

The model generates a confusion matrix using predictions from the test dataset.

A threshold of:
0.5

is used to convert the sigmoid prediction into a class.

📋 Classification Report

The project generates a classification report using Scikit-learn.

The two classes are:

Crack
NoCrack

The report provides:

Precision
Recall
F1-score
Support

💾 Saved Models

The best model during training is saved as:

Best_Crack_Detection_Model.keras

The final trained model is saved as:

Final_Marvellous_Crack_Detection_Model.keras

🖼️ Single Image Prediction

The project contains:

predict_single_image(image_path)

The image passes through:

Input Image
     ↓
Load Image
     ↓
Resize to 128 × 128
     ↓
Convert to Array
     ↓
Normalize
     ↓
Add Batch Dimension
     ↓
CNN Prediction
     ↓
Crack / No Crack

Example output:

======================================================================
Single Image Prediction
======================================================================
Image Path       : sample.jpg
Prediction Value : 0.87
Final Result     : Crack Detected

🏭 Applications

Potential applications include:

Industrial surface inspection
Concrete surface inspection
Infrastructure inspection
Automated defect classification
Surface maintenance systems

🔮 Future Enhancements

Possible future improvements:

Real-time camera-based crack detection
Larger and more diverse datasets
Additional surface defect categories
Crack localization using object detection
Web application deployment
Mobile application deployment
Automated inspection reports
Confidence score visualization
Database storage of inspection results

📚 Concepts Demonstrated

This project demonstrates:

Convolutional Neural Networks
Image Classification
Image Preprocessing
Image Augmentation
Batch Normalization
Max Pooling
Dropout
Binary Classification
TensorFlow
Keras
Model Training
Early Stopping
Model Checkpointing
Learning Rate Reduction
Confusion Matrix
Classification Report
Single Image Prediction

📦 Requirements

Create a requirements.txt file containing:

tensorflow
numpy
matplotlib
scikit-learn
opencv-python

Install all dependencies using:

pip install -r requirements.txt

👨‍💻 Author

Prasad Rampure

AI & Machine Learning Project

📜 License

This project is created for educational and learning purposes.
