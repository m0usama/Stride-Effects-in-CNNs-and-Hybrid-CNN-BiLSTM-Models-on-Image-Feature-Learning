# Stride Effects in CNNs and Hybrid CNN–BiLSTM Models on Image Feature Learning

This project investigates how convolution stride settings influence feature extraction in CNNs, and how these changes affect the behaviour of a hybrid CNN–Bi-LSTM model. Fashion-MNIST is used as the test dataset, and three different architectures are compared. The work aims to show how stride changes the detail captured in early layers, how this influences generalisation, and why more complex architectures do not always perform better.

---

## 📘 Project Summary

This study compares the following models:

### **Model A — CNN with stride = 2**
- Larger jumps during convolution  
- Coarser feature maps  
- More stable generalisation  
- **Test Accuracy: 0.8795**

### **Model B — CNN with stride = 1**
- Overlapping windows retain more detail  
- Strongest classification performance  
- Mild overfitting but excellent generalisation  
- **Test Accuracy: 0.8999**

### **Model C — CNN + Bi-LSTM Hybrid**
- CNN encoder followed by a Bidirectional LSTM  
- Adds sequential modelling, but not ideal for spatial image data  
- More complex and more prone to overfitting  
- **Test Accuracy: 0.8297**

The results confirm that stride affects what the network learns in the early layers, and that the hybrid CNN–BiLSTM model does not improve performance on Fashion-MNIST.

---

## 📂 Repository Contents

| File / Folder | Description |
|---------------|-------------|
| **Individual_Assignment_Machine_Learning_Tutorial_11_Dec.ipynb** | Full Colab notebook with model training, evaluation, and visualisations |
| **tutorial.pdf** | Final written tutorial document |
| **figures/** | Saved output images: accuracy/loss curves, confusion matrices, feature maps |
| **README.md** | Project documentation and summary |


---

## 🧪 Notebook Workflow

The notebook is structured into clear sections:

### **1. Data Preparation**
- Load Fashion-MNIST  
- Normalise and reshape images  
- Create training, validation, and test splits  

### **2. Model Construction**
Models are created using functionalised builders:
- `buildCnnModel(stride=2)`
- `buildCnnModel(stride=1)`
- `buildHybridModel()` for the CNN–BiLSTM model  

### **3. Training**
All models are trained for **8 epochs** using identical settings, allowing direct comparison.

### **4. Evaluation**
Outputs include:
- Test accuracy and loss  
- Classification reports  
- Predictions for confusion matrices  

### **5. Visualisation**
The notebook automatically produces:

- Training and validation accuracy curves  
- Training and validation loss curves  
- Confusion matrices (normalised)  
- Per-class accuracy comparison  
- Bar chart of test accuracies  
- Feature maps demonstrating stride effects  

These visualisations form the basis of the written interpretation in the tutorial.

---

## 📊 Key Findings

### ✔ Stride = 1 Performs Best
The overlapping windows capture fine textures such as small edges and subtle shape changes.  
This leads to the highest accuracy: **0.8999**.

### ✔ Stride = 2 Provides Stability
Skipping cells forces the network to rely on broader patterns.  
Generalisation is stable, but detail-sensitive classes perform slightly worse.  
Final accuracy: **0.8795**.

### ✔ CNN–Bi-LSTM Underperforms
With **0.8297 test accuracy**, the hybrid model is:

- More complex  
- More prone to noise  
- Less aligned with spatial image structure  
- Overfitting more easily than both CNN baselines  

This reinforces a key ML principle:  
**Architecture must match the structure of the data.**  
Sequence models add unnecessary complexity when the data does not have natural temporal structure.

---

## 📈 Generated Visuals (From Notebook)

Included visual outputs:

- `training_accuracy.png`  
- `training_loss.png`  
- `model_comparison_bar_chart.png`  
- `confusion_matrix_stride2.png`  
- `confusion_matrix_stride1.png`  
- `confusion_matrix_hybrid.png`  
- `feature_maps_stride2.png`  
- `feature_maps_stride1.png`  

Each visual reinforces how stride and architecture affect the learning process.

---

## ⚖️ Ethical and Practical Considerations

- More complex models can worsen fairness by overfitting minority classes.  
- Simpler architectures (stride-1 CNN) show more balanced performance.  
- Model choice should consider generalisation, not just depth or parameter count.

---

## 💡 Skills Demonstrated

- Neural network implementation with TensorFlow/Keras  
- Model comparison and hyperparameter analysis  
- Visual explanation of feature extraction  
- Application of sequence models (Bi-LSTM)  
- Critical interpretation of ML behaviour  
- Reproducible and well-structured notebook development  

---

## 📚 References

Graves, A., 2005. Framewise phoneme classification with bidirectional LSTM and other neural network architectures. *Neural Networks*, 18(5–6), pp.602–610.

Hochreiter, S. and Schmidhuber, J., 1997. Long short-term memory. *Neural Computation*, 9(8), pp.1735–1780.

LeCun, Y., Bengio, Y. and Hinton, G., 2015. Deep learning. *Nature*, 521(7553), pp.436–444.

Xiao, H., Rasul, K. and Vollgraf, R., 2017. Fashion-MNIST: A Novel Image Dataset for Benchmarking Machine Learning Algorithms. *arXiv preprint* arXiv:1708.07747.

Zeiler, M.D. and Fergus, R., 2014. Visualizing and understanding convolutional networks. In: Fleet, D. et al. (eds.) *European Conference on Computer Vision*. Springer, pp.818–833.

---

## 📄 License

Released under the **MIT License**.

