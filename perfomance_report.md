# Scrap Classification Performance Report

This report summarizes the performance of the "Scrap Classification" model using ResNet18 on the scrap material dataset.

## Dataset Summary

| Class     | # Images |
|-----------|----------|
| Metal     | 200      |
| Plastic   | 200      |
| Paper     | 200      |
| Glass     | 200      |
| Trash    | 200      |
|Card Board|200        |

# Training vs Validation Loss

[Training vs Validation Loss]
<img width="640" height="480" alt="training_curves" src="https://github.com/user-attachments/assets/71fd1caa-8b37-4f14-a4d2-24c4ba5823b3" />

**Observations:**
- The model converged after 5 epochs.
- Validation loss closely follows training loss → minimal overfitting.
- Further improvement possible with deeper models or more data.


##  Confusion Matrix

![Confusion Matrix]
<img width="700" height="700" alt="confusion_matrix" src="https://github.com/user-attachments/assets/8304c031-be99-46e4-bb2b-6760d34eb037" />


**Observations:**
- High accuracy in most classes.
- Most misclassifications occur between visually similar classes (e.g., metal vs other).
- Glass and paper are predicted with high confidence consistently.

##  Performance Metrics
[classification_report.txt](https://github.com/user-attachments/files/22633148/classification_report.txt)
| Class     | Precision | Recall | F1-Score | Support | Observation                                                                            |
| --------- | --------- | ------ | -------- | ------- | -------------------------------------------------------------------------------------- |
| Cardboard | 0.79      | 0.82   | 0.81     | 38      | Good performance. High recall indicates most cardboard items are correctly identified. |
| Glass     | 0.65      | 0.73   | 0.69     | 51      | Moderate. Some glass is misclassified (low precision).                                 |
| Metal     | 0.76      | 0.81   | 0.78     | 47      | Strong performance, similar to cardboard.                                              |
| Paper     | 0.75      | 0.73   | 0.74     | 55      | Balanced precision and recall.                                                         |
| Plastic   | 0.73      | 0.70   | 0.72     | 47      | Decent, slightly lower recall → some plastics misclassified.                           |
| Trash     | 0.50      | 0.31   | 0.38     | 16      | Weak performance. Model struggles with trash, many are misclassified as other classes. |


## observation :
The model achieves a 72% overall accuracy, performing well on cardboard, metal, and paper, but struggling with trash and glass.
Imbalance and visual similarity between certain classes are likely causing misclassifications.
Improving data diversity and using advanced architectures can boost performance

##  Top-2 Predictions & Low-Confidence Cases

- Predictions with **confidence < 60%** are flagged as `low_confidence`.
- Example from simulation frames:

| Image        | Predicted | Confidence | Top-2 Predictions          |
|--------------|-----------|------------|----------------------------|
| paper1.jpg   | Paper     | 92%        | Paper (92%), Plastic (6%)  |
| plastic3.jpg | Plastic   | 57% ⚠️     | Plastic (57%), Other (40%) |

> Top-2 predictions are useful for monitoring uncertain cases in conveyor simulation.


