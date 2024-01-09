## Predicting NBA draft picks of NCAA players through data mining 
# About 
Our project aimed to combine various data mining techniques to predict prospective NBA draft picks from NCAA players. Making such classifications has the potential to support NBA teams in their decision-making process for draft picks as they can easily narrow down potential players based on their past season performance, or even see what players may be outside of the typical draft selection, and thus give the team better odds of being the first to select that player in the draft. 

Beyond supporting draft decisions in the NBA, our project could also potentially provide valuable insights for players aspiring to enter the draft as it can give them the ability to weigh their own performance metrics against others who have been drafted in the past, and thus help to identify areas in that players performance that, if improved upon, may increase their chances of being drafted.

Thus, by combining various data mining techniques for this project, we aimed to assist teams in identifying promising talents, potentially reshaping conventional draft selections, and offering valuable insights for aspiring players. Through this endeavor, we strived to contribute to the evolving landscape of talent evaluation through data mining in basketball.

**1. Data Collection:**
   - https://www.kaggle.com/datasets/adityak2003/college-basketball-players-20092021
   - Includes player stats from 2009-2021

**2. Data Preprocessing:**
   1) Import and remove corrupt/inconsistant/unnecessary data
   
   2) Drop cols. with >60% missing data (nan values) 
   
   3) Remove highly corrilated features with corrilation above 70%
   
   4) Change target variable 'pick' to 1 if value is 1-60, else to 0
   
   5) Merge each individual player into 1 row/player
   
   6) Remove all players who still have >15% missing data 
   
   7) split into training and testing data
   
   8) Use KNN to fill in any remaining missing data/Nan values
   
   9) Feature selection with random forest classifier 

**3. Prediction Method:**
   - Used 2 methods for finding the best means for training on unbalanced data: k-fold and by simply balancing the data

**4. Select a Prediction Target:**
   - Looking to predict if player was drafted or not, this is represented in our data set as 'pick'
     
**5. Model Selection:**
   - using an ensamble model with 2-3 ML models (logistic regression, support vector macine and random forest)
     
**6. Model Training:**
   - k-fold and balanced data training, iterated with different feature selection and paramaters until we found the best results 

**7. Model Evaluation:**
   - Predicted/estimated preformance found by averaging the preformance with the training data
   - preformance metrics: precision, recall and f1 scores because the data was highley unbalanced 
   - method 1 with k-fold:[Validation] Average Accuracy: 0.9794260626238357, [Validation] Average Precision: 0.6096724815021355, [Validation] Average Recall: 0.38394521450172875, [Validation] Average F1 Score: 0.4663094688675241
   - Method 2 semi balanced data: Accuracy estimate for the model:  0.945050505050505, Precision estimate for the model:  0.7653563331856171, Recall estimate for the model:  0.5905555555555555, F1 Score estimate for the model: 0.6563797592198158
     
**9. Model Interpretation:**
   - Heavily unbalanced data, thus accuracy was determined to be a poor metric for measureing model preformance
   - Found aggrigated data gave the best results, final eastures used: ['porpag','adjoe','adrtg', 'bpm', 'obpm', 'dbpm', 'ogbpm', 'dgbpm', 'pts']
   - When model predicts ‘pick’==1, how likely is it that that the player was drafted: precision, greater for method 1
   - When a player is drafted, how likely is it that the model will classify the player as ‘pick’==1: accuracy higher for method 2 
   - Trade off with increasing precision or recall and decrease the other. F1-scores help to represent both values, more representative of actual model performance: Best for method 2
   - because f1 was better for method 1 and helps to represent both precision and accuracy, we chose method 1 as being the better method 

**10. Model Testing and results:**
   - Tested on players who played during 2021, no cross over/data leakage as players were merged in preprocessing 
   - Method 1: [Test] Accuracy: 0.9908982983775227, [Test] Precision: 0.44, [Test] Recall: 0.55, [Test] F1-score: 0.48888888888888893
   - Method 2: Accuracy on Test Set: 0.9810051444400475, Precision on Test Set: 0.23076923076923078, Recall on Test Set: 0.6, F1-score on Test Set: 0.33333333333333337
   - Similar to above,  f1 was better for method 1 and helps to represent both precision and accuracy, we chose method 1 as being the better method

**10. Conclusion:**
- Better performance seen with the model and k-fold cross validation
- Made significant improvements from initial performance, however precision, recall and f1 still remained relatively low for both methods
-- Unbalanced data
-- Not all players with good stats apply to the draft 
- Best predictions were made with aggregate features. All/many skills are considered and important, may be harder for a player to pinpoint one skill to improve upon aside from their average points made per game. 
- Could provide a recruiter with insight into what data to focus on when determining players to potentially pick for the draft

**10. Potential future work:**
- Improve upon the model and adjust paramaters to increase preformance 
- Work more with non agrigated stats to see if there is a way to use specific skills for helping players to improve their chances in being drafted


    
