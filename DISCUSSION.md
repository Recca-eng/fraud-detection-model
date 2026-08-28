# Discussion: Limitations and Ethical Considerations

## Limitations

- **Dataset limitations.** This is a simulated dataset, not real financial transaction data, and does not confirm representation of any particular real world card issuer, region, or customer population. Patterns found here may not generalize to real transaction data without further validation.

- **Class imbalance.** Fraud makes up roughly 0.5 percent of the dataset. Even after stratified sampling and evaluation focused on recall rather than accuracy, the model has still seen relatively few real fraud examples compared to legitimate ones, which limits how confidently its behavior on rare or unusual fraud patterns can be trusted.

- **Recall is not perfect.** The final model correctly identified approximately 75 percent of fraudulent transactions in the test set, meaning roughly one in four fraud cases was still missed. In a real deployment, this gap would need to be weighed carefully against the cost of false positives and the operational capacity to review flagged transactions.

- **High cardinality features were frequency encoded, not eliminated.** Columns like job, merchant, and city were converted into frequency values rather than dropped, which preserves useful signal but also means the model is partly relying on how common or rare something is, not necessarily on a deeper causal reason why it relates to fraud.

## Ethical Considerations

- **False positives carry real cost to legitimate customers.** A transaction flagged as fraud when it is not can mean a declined purchase, a frozen card, or an unnecessary investigation for someone who did nothing wrong. This cost should be weighed seriously against the benefit of catching fraud, not treated as a minor tradeoff.

- **This model should support human review, not replace it.** A prediction here is a signal for further investigation, not a final determination of guilt or fraud. Automatic action based solely on a model prediction, without human review, is not an appropriate use of this work.

- **Demographic and location based features require caution.** Features such as customer age, gender, and city frequency contributed to the model's predictions. Any real world use of a model like this would need careful review to ensure it is not systematically disadvantaging any group of legitimate customers based on where they live or who they are, rather than genuine fraud risk.

- **Data privacy.** Real world fraud detection systems handle sensitive financial and personal data. Any deployment beyond this research context would need to meet appropriate data protection and financial regulatory standards, which are outside the scope of this project.
