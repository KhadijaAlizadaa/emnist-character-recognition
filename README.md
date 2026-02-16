# EMNIST Alphanumeric Recognizer

A web application that recognizes handwritten characters (digits and letters) using a CNN model trained on the EMNIST dataset.

## Project Overview

This project uses deep learning to recognize handwritten alphanumeric characters:
- **Digits:** 0-9
- **Uppercase Letters:** A-Z
- **Lowercase Letters:** a-z

**Total Classes:** 62

## Model Architecture

- **Type:** Convolutional Neural Network (CNN)
- **Framework:** TensorFlow/Keras
- **Input:** 28x28 grayscale images
- **Output:** 62 classes (digits + letters)

### Model Structure:
```
Conv2D (32 filters, 3x3) + BatchNorm + MaxPooling
Conv2D (64 filters, 3x3) + BatchNorm + MaxPooling
Conv2D (128 filters, 3x3) + BatchNorm
Flatten
Dense (256 units) + Dropout (0.5)
Dense (62 units, softmax)
```

### Performance:
- **Test Accuracy:** ~85%
- **Training Data:** 100,000 samples
- **Test Data:** 20,000 samples
- **Epochs:** 10

## Dataset

**EMNIST ByClass** - Extended MNIST with letters
- Source: [Kaggle EMNIST Dataset](https://www.kaggle.com/datasets/crawford/emnist)
- Format: 28x28 grayscale images
- Preprocessing: Transpose + Flip transformations

## Installation & Setup

### Prerequisites
```bash
Python 3.8+
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Run the Application
```bash
python app.py
```

The app will run on: `http://localhost:5000`

## Usage

1. Open the web interface in your browser
2. Draw a digit or letter on the canvas
3. Click **"Predict"** button
4. View top 3 predictions with confidence scores
5. Click **"Clear"** to draw again

## Project Structure
```
emnist-character-recognition/
│
├── app.py                 # Flask backend
├── index.html             # Frontend interface
├── emnist_model.h5        # Trained CNN model
├── label_mapping.csv      # Character mappings
├── requirements.txt       # Python dependencies
└── README.md              # Project documentation
```

## Technical Details

### Image Processing Pipeline:
1. Canvas input (280x280) → Resize to 28x28
2. Convert to grayscale
3. Invert colors (white bg → black bg)
4. Apply flip transformation
5. Normalize pixel values (0-1)
6. Reshape to (1, 28, 28, 1)
7. Feed to CNN model

### Key Challenge:
EMNIST dataset requires specific orientation (transpose + flip). The preprocessing ensures canvas drawings match the training data format.


## Technologies Used

- **Backend:** Flask
- **Frontend:** HTML5, CSS3, JavaScript
- **ML Framework:** TensorFlow/Keras
- **Dataset:** EMNIST ByClass

## License

This project is for educational purposes.

## Acknowledgments

- EMNIST Dataset: Cohen, G., Afshar, S., Tapson, J., & van Schaik, A. (2017)
- TensorFlow/Keras framework
- Flask web framework


## 🎥 Demo

[📹 Watch Demo Video](https://docs.google.com/videos/d/1_4ygrK1CS-Hz7swTLOWqkwozIaZZupp5Jin9Jk3GqxU/edit?usp=sharing)
