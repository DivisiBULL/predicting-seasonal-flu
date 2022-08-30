# predicting-seasonal-flu

Predicting seasonal flu using multi-iterative classification models

# Repo Guide
This README will briefly describe my process and findings. For more information visit the notebook

The main work of this project takes place in [Vaccine_Classification.ipynb](https://github.com/DivisiBULL/predicting-seasonal-flu/blob/main/Vaccine_Classification.ipynb). Note: This likely will not render in github. This is an error on the side of github and I can't do anything about it. Visit [NBViewer](https://nbviewer.org/github/DivisiBULL/predicting-seasonal-flu/blob/main/Vaccine_Classification.ipynb) to be able to visit the entire notebook

There is also a presentation located under the PDFs folder [link](https://github.com/DivisiBULL/predicting-seasonal-flu/blob/main/PDFs/presentation_flatiron_phase_3_project.pdf)

# Business Understanding

I have been hired by a **fictitious** version of Costco Pharmacy (**My opinions are my own and in no way reflect that of Costco Pharmacy**). I have been hired by the pharmacy to try and gain a better understanding of what affects personal vaccination rates. Their hope is to try and encourage more of their members to visit the pharmacy for their seasonal flu vaccines. 

Due to the COVID-19 pandemic vaccination rates have never been such a talking point before. Here in the US the decision to get vaccinated has devolved into a political divide instead of a public health effort.

I will be providing Costco Pharmacy with an ability to make a prediction of which of their members have been vaccinated and which have not. To be able to create more targeted advertising to those who have not been vaccinated. This model will also be able to determine which of our features are the most important to someone getting the seasonal flu which will be able to aid in the direction of the marketing team.

# The Data

The data we will be looking at today comes from another pandemic, the H1N1 influenza pandemic. This data originally comes from a National 2009 H1N1 Flu Survey, which also included information on the seasonal flu. I brought in the data from a competition being hosted by DRIVENDATA. You can find the download page [here](https://www.drivendata.org/competitions/66/flu-shot-learning/data/) (Note: It requires you to sign up and register to the competition to be able to download, but it’s free to do so). You can also visit their benchmark notebook [here](https://drivendata.co/blog/predict-flu-vaccine-data-benchmark/). Which looks at this project as a multi classification problem for both H1N1 and the seasonal flu. I am currently looking at it only trying to predict the vaccination rate for seasonal flu.

In the future I hope to look at a similar classification problem with COVID-19 but the data acquisition required for that was outside the scope of my project. This data will still prove useful to our stakeholder to try and gain a better understanding of what affects personal vaccination rates.

I would also like to look at data streams directly from Costco Pharmacy. I could try and determine what other factors play important roles in vaccination rates from information they are already collecting.

# Evaluation

XGBoost GridSearchCV turned out to be best performing model for our case. Vanilla logistic regression also performed surprisingly well with only a .01% decrease in precision for the 0 label. Both would be appropriate choices. I decided to use the GridSearchCV XGBoost model for my evaluation.

Our overall accuracy was 79%. Meaning that 79% of the time we were able to guess correctly if someone had been vaccinated or not
for a classification problem like this that is not a bad score by any means but there is definitely room for improvement

There is also another metric called recall that we got up to 82%. It cares less if it categorizes someone as not vaccinated who has already been vaccinated. 100% recall would just be guessing that no one is vaccinated. We don’t want to guess everyone is not vaccinated but a high recall is good for us in this case. There will be a few people who the model predicts as not vaccinated who have been already but receiving advertisements to get a vaccine you already have will not be that annoying to the few “members” it miss categorizes

Caveats: 
The data is relatively old, coming in from 2009. Factors determining vaccination rates might have changed 
The data also was not specifically taken from Costco members only, so some demographics might be different

The biggest problem for our model is that it isn’t able predict vaccination status without someone filling out a long survey. It would be faster to just ask someone if they have been vaccinated or not. I discuss some options to this in future projects

Here are the classification report and confusion matrix for my final model

![alt text](https://github.com/DivisiBULL/predicting-seasonal-flu/blob/main/PNGs/classification_report_final_xgboost.PNG?raw=true)

![alt text](https://github.com/DivisiBULL/predicting-seasonal-flu/blob/main/PNGs/confusion_matrix_final_xgboost.PNG?raw=true)

As well as the feature importances from the model

![alt text](https://github.com/DivisiBULL/predicting-seasonal-flu/blob/main/PNGs/feature_importances_final_xgboost.PNG?raw=true)



# Future Projects

For a future project I would like to bring in data from internal data sources (both from Costco Pharmacy and Costco itself) to try and determine if a model can be produced from this information alone 
(members shopping habits, prescription rates, visiting rates, age, ect.)

I would also like to look at vaccination rates for COVID-19 to see what different factors play a role between the vaccines
