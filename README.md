# Improving-CNN-Performance-Using-Regularization---04

Colab link: https://colab.research.google.com/drive/1HcYmwQxecMeKVaIolZwmyZF3umjMkp8K?usp=sharing

# A. Model Evaluation Analysis 

## 1. What were the weakest-performing classes based on the confusion matrix?
### Ans. Ambulia

## 2. How did Precision, Recall, and F1-score vary across classes?
### Ans.  
LOWEST PRECISION (Most False Positives):
    LimnobiumLaevigatum - 0.95 (LOWEST)
    HygrophilaPolysperma - 0.96
    EloDeaDensa - 0.97
    
LOWEST RECALL (Most False Negatives):

Moneywort - 0.96 (LOWEST)
Ambulia - 0.97
BacopaCaroliniana - 0.97
DwarfSagittaria - 0.97

LOWEST F1-SCORE (Overall Weakest):

HygrophilaPolysperma - 0.97
LimnobiumLaevigatum - 0.97
Moneywort - 0.97

RANGE OF VARIATION:

Precision: 0.95 to 1.00 (5% variation)
Recall: 0.96 to 1.00 (4% variation)
F1-Score: 0.97 to 1.00 (3% variation)

all classes perform well between 95-100% across all 20 aquatic plant species

## 3. What does a low recall indicate in your model?
### Ans. Despite having the lowest recall in my model, only 96% of actual Moneywort samples are identified correctly, with an additional 4% being misidentified as other plants. This also applies to Ambulia, BacopaCaroliniana, and DwarfSagittaria (0.97 recall each). Low recall indicates that the model is too conservative and cannot accurately identify all authentic examples of these visually similar aquarium plants.


## 4. How does AUC score reflect model performance compared to accuracy?
### Ans. Based on my model's AUC and Accuracy metrics, which are almost identical and near-perfect, the results were positive. By assessing the model's ability to differentiate between all 20 plant classes across all probability thresholds, the AUC score is more significant than accuracy since it is not solely a matter of accuracy and can vary widely. The fact that both metric are 0.99 implies that my model has both discriminative power and classification performance.


# B. Model Improvement
## 5. How did data augmentation affect validation accuracy?
### Ans. While the data increase decreased validation accuracy from 99% to 51.97%, it also made a significant improvement in generalization. Despite the baseline model's 99% validation accuracy and minimal regularization, its heavy augmentation (RandomFlip, RandomRotation 0.2, randomZoom 0.3, and RandomContrast 0.1) dropped to 51.97% validation precision. Nonetheless, it gave rise to an exceptional trend where validation accuracy (51.97%) outperformed training accurate (41.22%), which is the hallmark of effective regularization. The upgrade made training more difficult as the model had to learn robust, generalizable features instead of relying on memorizing training data.

## 6. Why is Batch Normalization important in CNNs?
### Ans. To achieve stability, batch normalization is necessary for accelerating CNN training. I implemented BatchNormalization after every Conv2D layer, including 32, 64, and 128 filters, to create stable training curves that spanned 20 epochs. BatchNorm normalizes layer inputs to ensure that the activation distributions do not change due to internal covariate shift during training, resulting in a mean=0 and variance=1 value. My ability to use learning_rate=0.0001 was able to prevent any instability or vanishing gradients.

## 7. What role did Dropout play in improving your model?
### Ans.
## 8. How did Early Stopping prevent overfitting?
### Ans.
