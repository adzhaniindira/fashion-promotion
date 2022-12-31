# Fashion Store Marketing Promotion

## Introduction
This is a classification problem to predict what factors contribute to the success of a store marketing promotions. The dataset given contains 21,740 observations and 48 variables. Each observation represent data about a customer (whether they use credit card or shop online), their behaviour (number of visits, amount of total spent, fraction of total spent on a certain item, number of days between visits), and whether the said customer responded to the store's marketing promotion.

## Goals
1. Create univariate EDA for different data types and multi-variate EDA using Phik (𝜙k) correlation
2. Train logistic regression, k-NN, LightGBM, Random Forest, and model stacking (logit and LightGBM) to predict the response
3. Evaluate the models and select the best model for prediction
4. Generating insight from the data

## Loss matrix
I decided to use inverse class probabilities as the loss matrix due to following reasons:
- The EDA shows that the dataset contains imbalanced proportion of the response variable; customers who did not respond to the marketing promotions make up 83% of the total data.
- It is costly to spend money for a marketing promotion to customers who were predicted to respond, but did not (false positive). But the store will lose a bigger amount of money not to give marketing promotion to customers who the store thought would not respond, but in reality they would (false negative). Therefore, it is beneficial to weight the misclassification differently.

**Loss matrix**
<table>
  <tr>
    <th>Actual/ Predicted</th>
    <th>Did not respond (0)</th>
     <th>Responded (1)</th>
  </tr>
  <tr>
    <th>Did not respond (0)</th>
    <td>0</td>
    <td>17</td>
  </tr>
  <tr>
    <th>Responded (1)</th>
    <td>83</td>
    <td>0</td>
  </tr>
</table>


## Model selection and evaluation
Area Under the Precision-Recall Curve (AUPRC) is used for model evaluation as it does not take into account the negative case, which is more suitable for imbalanced dataset. Based on the AUPRC score, model stack can predict the response variable better than any other model, followed by LightGBM with the second highest AUPRC score.

## Insight
