# compas background

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
- Received compas scores for all people in Broward County between 2013 and 2014. Used only score produced for pre-trial for 11,757 people.

- Each defendant received at least three compas scores:
  - Risk of recidivism
  - Risk of violence
  - Risk of failure to appear
- Scores are from 1 to 10. 1 to 4 is low, 5 - 7 is Medium, 8 to 10 is high.
- Combined with public court records to identify who re-offended.

Defining recidivism:
- A new offense within two years


Analysis:
- Analysed for risk of recidivism and risk of violent recidivism.
- Distributions show white defendants scored less risky than black.
- Trained a logistic regression model to predict outcome according to different factors. Race was predictive of recidivism.


Test Compas Overall Predictive Accuracy:
- Fit a cox proportional hazards model to the data (allows comparing rates of recidivism while controlling for time)
- People with high scores were 3.5 times as likely to recidivate as people in the low category. The score has predictive value.
- Concordance score of 63.6 (it two people randomly selected the COMPAS score successfully ranks 63.6% of the time)
- COMPAS unevenly predicts recidivism between genders. Result is high risk women have a much lower risk of recidivism than a high risk man.
- Examined distribution of false positive and false negative errors.
- Black defendants are more likely to be misclassified at higher risk than white defendants.
- Black defendants who do not recidivate were nearly twice as likely to be classified by COMPAS as higher risk compared to their whtie counterparts.
- White defendants more likely to be wrongly predicted that they would not commit additional crimes.

  False positive = Falsely predict to recidivate.
  Black defendants is 38.14
  White defendants is 18.46
  More black defendants were incorrectly to be predicted to recidivate. More likely to treat non-threatening black defendants as threats.

  False negative = Falsely predict not to recidivate.
  Black defendants is 38.37
  White defendants is 62.62
  More white defendants were incorrectly to be predicted not to recidivate. More likely to treat dangerous white defendants as a non-threat.

  # Analysis
identify known issue with dataset
Show bias according to fairlearn measures
apply bia correction


Retrain model with a transparent model
