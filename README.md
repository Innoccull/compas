# compas

https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing

https://www.propublica.org/article/how-we-analyzed-the-compas-recidivism-algorithm

Propublica findings:
- black defendants more likely than white defendants to be incorrectly judged as a higher risk of recidivism
- white defendants more likely than black defendants to be incorrectly judged as a lower risk
- done through a comparison of predicted versus actual recidivism rates 2 years later - correctly predicted recidivism 61% of the time but was only correct on violent recidivism 20% of the time
- accuracy in predicting recidivism across groups was consistent across groups (59 for white and 63 for black) but the mistakes it made within these groups was very different
- black defendants more risky than they were
- white defendants less risky than they were
- even when controlling for prior crimes, future recidivism, age and gender, black defendants were more likely to be assigned higher recidivism scores than white defendants

Compas data:
Received compas scores for all people in Broward County between 2013 and 2014. Used only score produced for pre-trial for 11,757 people.

Each defendant received at least three compas scores:
- Risk of recidivism
- Risk of violence
- Risk of failure to appear

Scores are from 1 to 10. 1 to 4 is low, 5 - 7 is Medium, 8 to 10 is high.

Combined with public court records to identify who re-offended.

Defining recidivism:
A new offense within two years


Analysis:
Analysed for risk of recidivism and risk of violent recidivism.

Distributions show white defendants scored less risky than black.

Trained a logistic regression model to predict outcome according to different factors. Race was predictive of recidivism.


Test Compas Overall Predictive Accuracy:

