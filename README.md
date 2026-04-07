#Cats vs Dogs Classification (PyTorch CNN)

A deep learning project that classifies images of cats and dogs using a custom Convolutional Neural Network (CNN) built with PyTorch.

---

## Overview

This project implements a **binary image classifier** trained on the Cats vs Dogs dataset. The model learns visual patterns such as edges, textures, and shapes to distinguish between the two classes.

---

## Model Architecture

Custom CNN with 3 convolutional blocks:

- Conv2D → BatchNorm → ReLU → MaxPool  
- Channel progression: `3 → 32 → 64 → 128`  

Fully connected layers:
- `Linear(16×16×128 → 512)`  
- Dropout (0.3)  
- Output: `1 neuron` (binary classification)  

---

## Tech Stack

- Python  
- PyTorch  
- Torchvision  
- Pandas  
- Kaggle API  

---

## Dataset

- Source: Kaggle Cats vs Dogs dataset  
- Automatically downloaded using Kaggle API  

Structure:
```

cats_vs_dogs/
├── train/
└── val/

````

---

## Data Preprocessing

### Training:
- Resize to **128×128**  
- Random Horizontal Flip  
- Random Rotation (±15°)  
- Color Jitter (brightness & contrast)  
- Normalization  

### Validation:
- Resize to **128×128**  
- Normalization only  

---

## Training Details

- Loss Function: `BCEWithLogitsLoss`  
- Optimizer: `Adam`  
- Batch Size: `32`  
- Epochs: `10`  

---

## Results

- **Validation Accuracy:** ~68.57%  

---

## How to Run

### 1. Install dependencies
```bash
pip install torch torchvision pandas kaggle
````

### 2. Add Kaggle API credentials

Create a file at:

```
~/.kaggle/kaggle.json
```

Add your credentials:

```json
{
  "username": "YOUR_USERNAME",
  "key": "YOUR_API_KEY"
}
```

Set permissions:

```bash
chmod 600 ~/.kaggle/kaggle.json
```

---

### 3. Run the notebook/script

* Download dataset
* Preprocess data
* Train model
* Evaluate performance

---

## Limitations

* No model saving (`.pth`)
* No inference script
* No GPU support implemented
* Weak accuracy (~68%)
* No advanced evaluation metrics

---

## Improvements

To make this project strong:

* Use **Transfer Learning (ResNet18 / MobileNetV2)**
* Save trained model:

```python
torch.save(model.state_dict(), "model.pth")
```

* Add prediction script (single image input)
* Use GPU:

```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
```

* Add metrics (confusion matrix, precision, recall)

---

## Security Warning

Do NOT expose your Kaggle API key in code.

* Regenerate your key immediately
* Delete old key
* Add this to `.gitignore`:

```
.kaggle/
```

---

## Author

**Kartik Meena**
Backend + AI/ML Engineer

```
