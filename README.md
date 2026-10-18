# 🗑️ Garbage Image Classification Using EfficientNet-B6

An AI-powered garbage image classification project that uses deep learning and transfer learning to classify waste images into 10 different categories. The system is built using PyTorch and Torchvision with an ImageNet-pretrained EfficientNet-B6 model and provides an interactive prediction interface using Gradio.

## 📌 Project Overview

Proper waste classification is essential for waste management and recycling. This project develops a deep learning model that automatically identifies the category of garbage from an input image.

The model is trained and fine-tuned using the **Garbage Classification V2** dataset and achieves **94.18% test accuracy** on 1,839 test images.

## ✨ Key Features

- Classification of garbage images into 10 categories.
- Transfer learning using ImageNet-pretrained EfficientNet-B6.
- Image cleaning and preprocessing.
- Data augmentation to improve model generalization.
- Training, validation, and testing with a 70:15:15 split.
- Fine-tuning for improved classification performance.
- Evaluation using accuracy, precision, recall, F1-score, and a confusion matrix.
- Interactive image prediction interface using Gradio.
- Saving trained model weights for inference.

## 🧠 Technologies Used

- **Programming Language:** Python
- **Deep Learning Framework:** PyTorch
- **Computer Vision:** Torchvision, PIL
- **Data Analysis:** Pandas, NumPy
- **Model Architecture:** EfficientNet-B6
- **Pretrained Weights:** ImageNet
- **Evaluation:** Scikit-learn
- **Deployment Interface:** Gradio
- **Development Environment:** Google Colab

## 📂 Dataset Description

The project uses the Garbage Classification V2 dataset, containing **12,259 images** across 10 garbage categories.

| Category | Number of Images |
|---|---:|
| Clothes | 1,892 |
| Glass | 1,736 |
| Plastic | 1,597 |
| Shoes | 1,449 |
| Cardboard | 1,411 |
| Paper | 1,336 |
| Metal | 930 |
| Battery | 756 |
| Biological | 699 |
| Trash | 453 |
| **Total** | **12,259** |

### Garbage Categories

1. Battery
2. Biological
3. Cardboard
4. Clothes
5. Glass
6. Metal
7. Paper
8. Plastic
9. Shoes
10. Trash

## ⚙️ Data Preprocessing

The following preprocessing steps are applied:

- Removal of unsupported and corrupted image files.
- Resizing images to 224 × 224 pixels.
- Random horizontal and vertical flipping.
- Random rotation up to 30 degrees.
- Brightness and contrast adjustment using Color Jitter.
- Conversion of images into PyTorch tensors.
- Normalization using ImageNet mean and standard deviation.

Data augmentation is applied to the training set, while validation and test images use deterministic transformations.

## 📊 Dataset Split

The dataset is divided into three subsets:

| Subset | Percentage | Number of Images |
|---|---:|---:|
| Training | 70% | 8,581 |
| Validation | 15% | 1,839 |
| Testing | 15% | 1,839 |
| **Total** | **100%** | **12,259** |

The DataLoader uses a batch size of 16.

## 🏗️ Model Architecture

This project uses **EfficientNet-B6**, a convolutional neural network pretrained on ImageNet.

Transfer learning is applied by replacing the original classification layer with a new linear layer containing 10 output neurons, one for each garbage category.

### Training Configuration

- **Initial Training:** 3 epochs
- **Fine-Tuning:** 2 additional epochs
- **Optimizer for Fine-Tuning:** Adam
- **Fine-Tuning Learning Rate:** 0.0001
- **Loss Function:** Cross-Entropy Loss
- **Training Device:** CUDA-enabled GPU (Tesla T4 in the reported experiment)

## 📈 Model Performance

### Final Evaluation Results

| Metric | Result |
|---|---:|
| Test Accuracy | 94.18% |
| Macro Average Precision | 93.19% |
| Macro Average Recall | 93.61% |
| Macro Average F1-Score | 93.37% |
| Weighted Average F1-Score | 94.21% |

The final evaluation was performed on 1,839 held-out test images.

### Training Improvement

| Stage | Accuracy |
|---|---:|
| Initial Training Accuracy | 84.47% |
| Initial Validation Accuracy | 84.61% |
| Fine-Tuned Training Accuracy | 94.87% |
| Final Validation Accuracy | 94.18% |
| Final Test Accuracy | 94.18% |

The results demonstrate that fine-tuning substantially improves the model's classification performance.

## 🖥️ Gradio Deployment

The project includes a Gradio-based interface for interactive image classification.

### How It Works

1. Upload a garbage image.
2. The image is converted to RGB format.
3. The image is resized and normalized.
4. The trained EfficientNet-B6 model processes the image.
5. The interface displays the predicted garbage category.

The deployment code loads the fine-tuned model weights from `garbage_eff_b6_finetuned.pth`.

**Note:** A persistent public deployment URL is not included in the supplied report.

## 🔄 System Workflow

```text
Dataset Acquisition
        ↓
Dataset Cleaning
        ↓
Image Preprocessing & Augmentation
        ↓
Train / Validation / Test Split
        ↓
EfficientNet-B6 Initialization
        ↓
Model Training
        ↓
Fine-Tuning
        ↓
Model Evaluation
        ↓
Model Saving
        ↓
Gradio Prediction Interface
```

## 💾 Model Files

The notebook saves the following model files:

- `garbage_eff_b6.pth` — Initial trained model weights.
- `garbage_eff_b6_finetuned.pth` — Fine-tuned model weights.
- `garbage_full_eff_b6.pth` — Full model object containing the model structure and weights.

These files are generated during model training and may need to be downloaded or added to the project repository separately.

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/Sifat049/Garbage-Classification-AI-LAB-Project.git
cd Garbage-Classification-AI-LAB-Project
```

### 2. Set Up the Python Environment

It is recommended to use Python 3.10 or another Python version compatible with the selected PyTorch and Torchvision releases.

```bash
python -m venv venv
```

Activate the environment.

**macOS / Linux:**

```bash
source venv/bin/activate
```

**Windows:**

```bash
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install torch torchvision
pip install pandas numpy pillow scikit-learn matplotlib seaborn gradio
```

### 4. Run the Notebook

Open the project notebook in Google Colab or Jupyter Notebook.

Run the cells in order to perform dataset preparation, training, fine-tuning, evaluation, model saving, and Gradio interface setup.

> **Important:** The notebook requires access to the dataset and the appropriate trained model files. The exact notebook filename and dataset setup should match the files included in the repository.

## ⚠️ Limitations

- The dataset has an imbalanced class distribution.
- The trash category has fewer images than the clothes category.
- Classification performance varies across categories.
- The experiment uses a limited five-epoch training and fine-tuning process.
- Extensive hyperparameter search and repeated cross-validation were not performed.
- A permanent public Gradio deployment URL is not provided in the report.

## 🔮 Future Improvements

- Increase the number of training images for underrepresented categories.
- Experiment with other model architectures.
- Perform more extensive hyperparameter tuning.
- Apply class-balancing techniques.
- Improve classification performance for visually similar garbage categories.
- Deploy the application through a persistent hosting service.
- Integrate the classifier into a smart waste-sorting system.

## 🏁 Conclusion

This project demonstrates the application of deep learning and transfer learning to automated garbage image classification. Using ImageNet-pretrained EfficientNet-B6, the system achieves **94.18% test accuracy** and a weighted F1-score of **0.9421** across 10 garbage categories.

The project provides an end-to-end workflow covering dataset preparation, model training, fine-tuning, evaluation, and interactive prediction using Gradio.

## 📄 Project Report

The detailed Artificial Intelligence project report describes the dataset, preprocessing pipeline, model architecture, training process, evaluation metrics, confusion matrix, classification report, and Gradio deployment.

## 👨‍💻 Author

**Sifat**

GitHub: [@Sifat049](https://github.com/Sifat049)

## 📜 License

No license information is specified in the supplied project report. Add an appropriate open-source license if you intend to distribute or reuse this project publicly.
