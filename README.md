# MNIST CNN Optimizer Comparison

##  Project Overview

This project implements a **Convolutional Neural Network (CNN)** trained on the **MNIST handwritten digit dataset**.
The objective is to evaluate and compare the performance of different optimizers:

* Adam
* Adadelta
* Stochastic Gradient Descent (SGD)

The comparison is based on:

* Training Loss
* Validation Loss
* Accuracy

---

##  Dataset

* MNIST dataset (handwritten digits 0–9)
* 60,000 training images
* 10,000 testing images
* Image size: 28 × 28 (grayscale)

---

##  Technologies Used

* Python 3.x
* TensorFlow / Keras
* NumPy
* Matplotlib

---

##  Model Architecture

The CNN architecture follows the exact assignment specification:

1. Conv2D → 64 filters, kernel=(3×3), stride=(2,2), padding='valid', activation=ReLU
2. Conv2D → 32 filters, kernel=(2×2), stride=(1,1), padding='same', activation=ReLU
3. MaxPooling2D → pool=(2×2), stride=(1,1)
4. Dropout → 0.35
5. Flatten
6. Dense → 256 units, activation=tanh
7. Dropout → 0.5
8. Dense → 10 units, activation=softmax

---

##  Methodology

### 1. Data Preprocessing

* Normalize pixel values (0–255 → 0–1)
* Reshape to (28, 28, 1) for CNN input
* Convert labels to one-hot encoding

---

### 2. Model Training

Each optimizer is trained **independently** using:

* Epochs: 10
* Loss Function: Categorical Crossentropy
* Metric: Accuracy

```python
def train_model(optimizer_name):

    model = build_model()

    model.compile(
        optimizer=optimizer_name,
        loss='categorical_crossentropy',
        metrics=['accuracy']
    )

    history = model.fit(
        x_train, y_train,
        epochs=10,
        validation_data=(x_test, y_test),
        verbose=1
    )

    return model, history
```

---

### 3. Fair Comparison

Each optimizer:

* Starts from a **fresh model (random initialization)**
* Uses the **same dataset**
* Uses the **same number of epochs**

This ensures a **fair and unbiased comparison**.

---

## 📊 Results

---

## 📈 Visualizations

The project includes:

* Training Loss curves
* Validation Loss curves
* Accuracy curves

---

##  Model Evaluation

| Optimizer | Accuracy   | Loss       |
| --------- | ---------- | ---------- |
| Adam      | **0.9922** | **0.0248** |
| SGD       | 0.9779     | 0.0706     |
| Adadelta  | 0.8115     | 0.6351     |
Best Model: Adam Optimizer

###  Observations

* **Adam** → Fast convergence, highest accuracy
* **SGD** → Slower but stable learning
* **Adadelta** → Moderate performance

Model Saving

All trained models were saved successfully:

adam_model.keras
sgd_model.keras
adadelta_model.keras

The Adam model was selected for final deployment due to highest accuracy and lowest loss.

Model Testing (Adam)

After reloading the best model:

Tested on 50 unseen samples ,
Predictions were fully correct on selected samples and 
Evaluated on full test set:
 Wrong Predictions: 102 
 High overall generalization performance

Workflow Summary

Train CNN with multiple optimizers (Adam, SGD, Adadelta)

Evaluate and compare performance

Save all trained models

Select best model (Adam)

Reload Adam model

Perform prediction and evaluation on test data

##  Project Structure

```
MNIST-CNN/
│
├── MNIST_CNN_Project.ipynb   # Main notebook
├── README.md                 # Project documentation
├── requirements.txt          # Dependencies
└── results/                  # Plots and outputs
```

##  Conclusion

The Adam optimizer CNN model achieved the best performance with 99.22% accuracy, making it the final selected model for digit classification tasks.

##  Author

**KASSAHUN TIGABU**
Data Science Student
Bahir Dar University

---

## 📜 License

This project is for academic and educational purposes.
