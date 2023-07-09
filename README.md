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
identify what fairness means in this context
Show bias according to fairlearn measures
apply bias correction


Retrain model with a transparent model

# Fairness and Bias in AI
While it is universally recognised that fairness is an important aspect of AI systems, There is no universally agreed definition of fairness means in the context of AI. However one commonly agreed point is that the presence of bias in AI systems can undermine fairness and that addressing these biases are a key part in ensuring AI systems are fair.

Bias in AI systems can be problematic for several reasons:
- Allocation harms: It can extend or withhold opportunities from specific groups.
- Penalty harms
- Quality of service harms
- Stereotyping
- Erasure harms

The COMPAS system made predictions about the likelihood of individuals to recidivate. This information was used by judges during pre-trial hearings to determine what should be done with defendants. An incorrect prediction made by COMPAS could result in an individual being incorrectly penalised. This is a type of penalty harm. Bias in this context would be detecting if the model correctly predicts likelihood to recidivate by certain protected groups to see if specific groups are treated without any unfair bias in this context.


# Fairness Metrics
There are a number of metrics that can be used to detect bias:
- Selection rate | shows the proportion within a group that are predicted to have a positive outcome | Tells us the proportion of each group that is predicted to recidivate
- False positive rate | Tells us how often we get it wrong that we decide someone is a recidivist. | If one group has a higher false positive rate in compas, we will more likely falsely judge them to be a recidivist
- False negative rate | Tells us how often we incorrectly predic someone will not recidivate | If one group has a higher false negative rate, we are treating them as less 'risky'
- Demographic parity | shows the difference in selection rates between groups | A difference in selection rates will means there is a difference in the likelihood the groups will be selected as recidivist 
- Equalised odds | tells us if the model performs equally well for selecting correct cases across groups | groups are being incorrectly predicted to recidivate
- Equal opportunity | the model performs equally well on the positive case | in compas this refers to the rate of being correct for positive predictions

As we are concerned with penalty harms in the context of COMPAS, we will apply false positive rate and equalised odds to detect bias.


# Detecting Bias with Fairlearn
Fairlearn is a community-driven project that provides libraries for detecting and mitigating bias. It is the first library we will use for detecting bias in the COMPAS dataset.

