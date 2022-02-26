# Identifying dogs versus cats using RNN Models
The goal is to identify if a picture contains a cat or dog of various kinds and with different backgrounds. This type of identification can be extrapolated to identifying a car in an image or a pedestrian. 

## Research design and modeling methods
I utilize an 75/25 train/validate split. I train and fit 3 models using the first model as a base, adding layers in model two, and lastly adding drop-out layers in model 3. The training and test data is converted to grayscale, resized, and values standerdized prior to training the models. For each model I utilize an early stopping mechanism. If the validation loss increases after two epochs, the fitting stops. However, for the third model, since drop-out layers are added, it is raised from 2 epochs to 4 epochs. This ensures the model isn't over-fitted to the training set. I then check the model against the validation set and generate a confusion matrix and the accuracy/precision/f1-stat/ROC AUC for each of the classes.
 
## Results and evaluation
| Metric | Model 1 | Model 2 | Model 3 |
|---     | ---     | ---     | ---     |
| Validation Accuracy | 0.79 | 0.87 | 0.87 | 
| Test Log Loss | 0.77 | 0.78 | 0.76 |

While initially from the validation set it appeared Model 3 was slightly better than Model 2, in the end Model 3 was the winner, with Model 1 be slightly less good. This showed that using a drop-out layer after each pooling layer helped the model not over-fit on the training data.

## Conclusion
Something to check would be to change the early stopping to 4 straight epochs of an increase in validation loss for Model 1 and Model 2 and see if the log loss score improves. This would indicate that training was cut-off early for these models rather than the drop-out layers added in Model 3. 
