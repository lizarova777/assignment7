# Diagnostic Metrics

## Project Objective:

In the following project, you will be looking at data from an one level of an online geography tutoring system used by 5th grade students. The game involves a pre-test of geography knowledge (pre.test), a series of assignments for which you have the average score (av.assignment.score), the number of messages sent by each student to other students about the assignments (messages), the number of forum posts students posted asking questions about the assignment (forum.posts), a post test at the end of the level (post.test) and whether or not the system allowed the students to go on to the next level (level.up). The purpose of this project is to build some classification trees and then generate a diagnostic metrics about these trees.


## Dataset:
  
  * online.data.csv

The description of the variables is provided above. 

## Procedure:

First, the data was wrangled and a scatterplot was generated to visualize the relationship between variables. Then, a classfication tree was built using the following model:

```
rp<- rpart(level.up~forum.posts+post.test.score+messages, method="class", data=D3) 
```

The next step was to generate the ROC for the model and calculate the Area Under the Curve (AUC). The same procedure was applied to the second model for a classification tree but with different variables, which is:

```
rp2<- rpart(level.up~av.assignment.score+pre.test.score, method="class", data=D3)
```
Then, AUC of the first model was compared with the AUC of the second model. The second to last step was to choose two probability thresholds for the chosen model that balances capturing the most correct predictions against false positives, generate table of comparisons displaying true positives, false positives, true negatives, and false negatives, and calculate three diagnistic metrics (i.e. accuracy, precision, and recall). The final step was to calculate the kappa value.

## Results and Interpretation:

### First Classification Tree:

![tree1](https://github.com/lizarova777/assignmen7t/blob/master/tree1.png)

### Second Classificaition Tree:

![tree2](https://github.com/lizarova777/assignment7/blob/master/tree2.png)

The second model is better in regards to prediction than the first model since its area under the ROC (AUC) is greater than that of the first model. In particular, AUC for the second  model is 0.977 whereas the AUC for the first model is 0.855. This suggests that the second is better at predicting that the system will allow the student to go to the next level since it has a higher true positive rate (sensitivity). Also, for both models, different threshold values produced the same results. However, the second model is better than the first model when it comes to the diagnostic metrics. This indicates that not only the second model is better at predicting that the system will allow the student to go to the next level, it produces more accurate and relevant predictions. Likewise, there is a higher reliability betweeen the data and the model. This is indicated by higher accuracy, precision, recall, and kappa values. 
