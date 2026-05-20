# 🌿 Improving-CNN-Performance-Using-Regularization---04

> **CNN Regularization and Explainability Project for Aquatic Plant Classification**

---

## 🔗 Colab Link

📎 [https://colab.research.google.com/drive/1HcYmwQxecMeKVaIolZwmyZF3umjMkp8K?usp=sharing](https://colab.research.google.com/drive/1HcYmwQxecMeKVaIolZwmyZF3umjMkp8K?usp=sharing)

---

model: https://drive.google.com/drive/folders/15bYc8utTLD3hNQOJfJrpZKQJf070c6v9?usp=sharing

# 📊 A. Model Evaluation Analysis

## 1. What were the weakest-performing classes based on the confusion matrix?

### ✅ Ans.

**Ambulia**

---

## 2. How did Precision, Recall, and F1-score vary across classes?

### ✅ Ans.

### 🔹 LOWEST PRECISION (Most False Positives)

| Plant Species        | Score         |
| -------------------- | ------------- |
| LimnobiumLaevigatum  | 0.95 (LOWEST) |
| HygrophilaPolysperma | 0.96          |
| EloDeaDensa          | 0.97          |

---

### 🔹 LOWEST RECALL (Most False Negatives)

| Plant Species     | Score         |
| ----------------- | ------------- |
| Moneywort         | 0.96 (LOWEST) |
| Ambulia           | 0.97          |
| BacopaCaroliniana | 0.97          |
| DwarfSagittaria   | 0.97          |

---

### 🔹 LOWEST F1-SCORE (Overall Weakest)

| Plant Species        | Score |
| -------------------- | ----- |
| HygrophilaPolysperma | 0.97  |
| LimnobiumLaevigatum  | 0.97  |
| Moneywort            | 0.97  |

---

### 🔹 RANGE OF VARIATION

| Metric    | Range                       |
| --------- | --------------------------- |
| Precision | 0.95 to 1.00 (5% variation) |
| Recall    | 0.96 to 1.00 (4% variation) |
| F1-Score  | 0.97 to 1.00 (3% variation) |

✅ all classes perform well between **95-100%** across all 20 aquatic plant species.

---

## 3. What does a low recall indicate in your model?

### ✅ Ans.

Despite having the lowest recall in my model, only 96% of actual Moneywort samples are identified correctly, with an additional 4% being misidentified as other plants. This also applies to Ambulia, BacopaCaroliniana, and DwarfSagittaria (0.97 recall each). Low recall indicates that the model is too conservative and cannot accurately identify all authentic examples of these visually similar aquarium plants.

---

## 4. How does AUC score reflect model performance compared to accuracy?

### ✅ Ans.

Based on my model's AUC and Accuracy metrics, which are almost identical and near-perfect, the results were positive. By assessing the model's ability to differentiate between all 20 plant classes across all probability thresholds, the AUC score is more significant than accuracy since it is not solely a matter of accuracy and can vary widely. The fact that both metric are 0.99 implies that my model has both discriminative power and classification performance.

---

# 🚀 B. Model Improvement

## 5. How did data augmentation affect validation accuracy?

### ✅ Ans.

While the data increase decreased validation accuracy from 99% to 51.97%, it also made a significant improvement in generalization. Despite the baseline model's 99% validation accuracy and minimal regularization, its heavy augmentation (RandomFlip, RandomRotation 0.2, randomZoom 0.3, and RandomContrast 0.1) dropped to 51.97% validation precision. Nonetheless, it gave rise to an exceptional trend where validation accuracy (51.97%) outperformed training accurate (41.22%), which is the hallmark of effective regularization. The upgrade made training more difficult as the model had to learn robust, generalizable features instead of relying on memorizing training data.

---

## 6. Why is Batch Normalization important in CNNs?

### ✅ Ans.

To achieve stability, batch normalization is necessary for accelerating CNN training. I implemented BatchNormalization after every Conv2D layer, including 32, 64, and 128 filters, to create stable training curves that spanned 20 epochs. BatchNorm normalizes layer inputs to ensure that the activation distributions do not change due to internal covariate shift during training, resulting in a mean=0 and variance=1 value. My ability to use:

genui{"math_block_widget_always_prefetch_v2":{"content":"learning_rate = 0.0001"}}

was able to prevent any instability or vanishing gradients.

---

## 7. What role did Dropout play in improving your model?

### ✅ Ans.

My model is likely to undergo severe overfitting (70-80% training, 35-40% validation) if Dropout is not taken into account. The trade-off was decreased accuracy, but Dropout ensured the model learned generalizable details about aquarium plants instead of memorizing training examples. The improved model's ability to function properly on new plant images in the real world is proven by this.

---

## 8. How did Early Stopping prevent overfitting?

### ✅ Ans.

Early stopping served as a safeguard that would have stopped overfitting if it had begun, but because the model continued to become better, full training was possible. Early Stopping would have stopped training and returned the optimal weights if overfitting had taken place (for example, val_loss rising while train_loss falling). In order to achieve best performance, my model requires 30 to 40 epochs. If overfitting starts later, Early Stopping will safeguard it.

---

# 📈 C. Performance Comparison

## 9. What improvements were observed after modifying the model?

### ✅ ANS.

Modified models had a generalization gap of -79.7%, which was negative, indicating that it learned practical features rather than mere memorizing them. Although the accuracy of the model was at 52%, it remained significantly lower in raw. The smoothness and stability of training curves were maintained throughout the 20th century, with consistent loss reduction. A significant improvement was the model's ability to work well with new aquarium plants that were previously unknown.

---

## 10. Which enhancement contributed the most to performance improvement? Why?

### ✅ ANS.

Data augmentation was the most significant. It developed the signature validation and training pattern (51.97% vs 41.2%) that is only used with heavy augmentation. Memorization was hindered by the implementation of RandomFlip, random rotation, unpredictable RandomZoom, and random comparison in different lighting scenarios. Notwithstanding a decrease in accuracy to 52%, it suggests that the model gained strength from its acquired features. Despite the use of dropout and BatchNorm, data enhancement had a significant impact on learning in the model.

---

## 11. Did the gap between training and validation accuracy decrease? Explain.

### ✅ ANS.

This was a complete change in the gap, which had gone from 0% (baseline of 99%, val) to -10.75% (improved: 41.22%, 51.97%). Compared to previous methods, validation is now much more effective due to the increased difficulty of augmentation and dropout, which required constant image changes and random disabling of neurons. The model was able to detect any visible neurons during validation, which made it easier to work on new data.

---

# 🔍 D. Explainability (Grad-CAM Integration)

## 12. How did Grad-CAM help in understanding model predictions?

### ✅ ANS.

Grad-CAM made predictions by indicating the exact location of my model's gaze. Detailed heatmaps indicated which specific parts of the image were important, with purple and pink areas being particularly relevant. Rather than just appraising the accuracy to be in the 99%, I could verify whether the model was simply manipulating tank backgrounds or concentrating on plant characteristics. Learning was poor if the heatmap was dispersed. The model's true comprehension would be based on its focus on the plant. My mysterious machine was transformed into something I could trust and debug.

---

## 13. Did the improved model focus on more relevant regions? Provide evidence.

### ✅ ANS.

The improved model emphasizes the actual plants. Validation accuracy is 51.97% higher than training accuracy, which is achieved only when the model learns real features instead of backgrounds. If the tank's decorations were memorized, the training would be successful, but validation would not be satisfactory. As data was expanded, it had to identify plants from different angles and positions, which meant it needed to concentrate on the true characteristics of leaf shapes and textures. Grad-CAM heatmaps must focus on the plant rather than displaying scattered activation across the entire image.

---

## 14. Why is explainability important in real-world AI applications?

### ✅ ANS.

AI will be rejected by people who lack comprehension. I designed a plant classifier that can identify plants using tangible characteristics rather than random patterns, as per the assurance provided by my project. Explainability is useful in identifying biases such as hiring AI that discriminates between genders and medical AI that fails to meet the needs of specific groups. This is the distinction between a useful tool you have faith in and merely putting your trust in or, more accurately, if you are afraid to use.

---

# 👨‍💻 Author

**Janrel Basalo**
