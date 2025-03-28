## Project Overview
Goal: Use OMDB Movie Dataset to attempt to predict IMDB Ratings of movies. 
Method: Extract data from OMDB via API, transform the data for preprocessing, and run different Machine Learning models to see if meaningful prediction can occur given the existing data (75% Accuracy or better)
Definition of “Movie Success”:  One standard deviation above the average IMDB rating, which is a rating of 7.4 out of 10. This puts a “good movie” by our definition in the top 15% of movies by rating. 

Parameters In Training Data
Date
Genre
Actors/Actresses
IMDB/MetaCritic/Rotten Tomatoes
Box Office
Oscars/Awards

## Installation Instructions
* Download project files or type `git clone https://github.com/Brendan838/Movie_Prediction.git` in bash/terminal.
* To view/run Each individual model's script can be found in their respective folders named for each model used. They can be loaded in your code viewer/editor of choice (we used Jupyter Notebook to create these scripts, but other programs such as VSCode also work).
* The `ETL.ipynb` file shows our work in extracting and cleaning data from the [OMDB API]( https://www.omdbapi.com/). Please note, our first step was extracting IMDB Ids from their [available datasets](https://datasets.imdbws.com/). We have provided this file as a reference, but don't recommend rerunning due to the volume of APIs (will required paid tier). Should you like to re-run, please add the .tsv files in the code to the `Resources` folder from IMDB data set referenced. 
* `Resources/cleaned.csv` contains our cleaned data that was used in data models. 
* `Predicting Movie Success Group #4.pdf` contains our google slides presentation summarazing the project and analysis. 
* `Visualizations/MoviePredictionsAnalysis.twb` contains a tableau visualization of our cleaned dataset. This can be opened in tableau/tableau public on your local machine or in a web browser.


## Summary of Files and Directories
1. **Sam's Tableau**
   * Some parameters our models consider are things like box office revenue, genre, director, IMDB score, etc. To give an overview of our dataset and an idea of potential considerations the models take, we created a tableau file to visualize these considerations to provide a better idea of how they'll work. A example screenshot of the first dashboard in the tableau file can be seen here: ![movie_prediction_vis_preview](https://github.com/user-attachments/assets/a8f1495f-d959-4dbb-a0c6-54c1053f9f76)
2. **Brendan's Logistic Regression Model**
    * Scikit.learn LogisticRegression model was used on our Resources/Cleaned.csv to predict IMDB ratings of 7.4 or higher with an accuracy of 87.6%. 
    * Details on process and results can be found in slides 9-12 of `Visualizations/MoviePredictionsAnalysis.twb`
    * The most accurate updated and accurate model using box office values in this directory is `Logistic Regression/Logistic_Regression Attempt 3.ipynb`
    
3. **Mee's Decision Tree Model**

I used Brendan’s “model_data” data frame as we wanted to see and compare how a Decision Tree Model would perform vs the Logistic Regression Model and the K-Nearest Neighbor Model using the same data set. I used the week 20 supervised learning day 2 activity 3 to help me with my model.

Steps

1. I imported the libraries needed for the decision tree 
2. Created the standard StandardScaler instance
3. Fit Standard Scalar
4. Scaling the data
5. Created the decision tree classifier instance
6. Fit the model
7. Make predictions using the testing data
8. Calculate the confusion matrix
9. And then displayed the results

Conclusion for Decision Tree

This confusion matrix is producing an overall accuracy of 85% but because the precision for false positives is 90% and the recall for false negatives is 92%, which is higher than the true precision and recall percentages, I conclude that the decision tree model suggests that the model’s performance is unbalanced favoring False. So it mirrors Brandon’s results.


4. **Susan's KNN Model**
   
I used Brendan’s “model_data” data frame as we wanted to see and compare how a K-Nearest Neighbor would perform vs the Logistic Regression Model and the Decision Tree using the same data set. I used the week 20 supervised learning day 2 activity 7 to help me with my model.

Steps 

1. Scaling the Data:
•	Simple Explanation: First, I create a tool that will adjust the data to a standard scale (removing any extreme values). Then, I use this tool to scale both our training and testing data.
2. Training the Model:
•	Simple Explanation: I set up the model and train it using the scaled training data. The model learns how to predict what each piece of data belongs to, based on its neighbors.
3. Making Predictions:
•	Simple Explanation: The model now predicts the labels for the test data. It uses the information it learned from the training data to make these predictions.
4. Evaluating the Model:
•	Simple Explanation: The confusion matrix shows how many predictions were correct and how many were wrong. The classification report gives us more details, like how many positive and negative predictions were correct.

Sample Results:
•	False (Negative) Predictions: The model was good at predicting negatives (82% precision and 88% recall).
•	True (Positive) Predictions: The model was not as good at predicting positives (30% precision and 21% recall).
•	Accuracy: Overall, the model was correct 75% of the time.
Evaluating the Model: We check how well the model did with tools like the confusion matrix and classification report. The model works well for predicting negative outcomes, but it struggles with positive ones.

5. **Mai Houa's Random Forest Model**

To run the Random Forest classifier model, go to the Random Forest folder and select the Randomforest2025.ipynb file.

To create this model, I load the dataset from the Resources folder’s Cleaned.csv file and convert date columns to a datetime format. I then converted categorical data, like the director, actors, and genres, to dummy variables. I perform data cleaning such as filling in the missing values, dropping columns, and transforming columns to numerical values.

For this model, I decided to use the Rotten Tomatoes score to define success. So, a movie with a score of 70% or higher is considered a success (1), and anything below that is a failure (0). I split the dataset into training and testing sets based on movie release year. Movies released before 2025 were for training and movies released in 2025 were for testing. I then defined a Random Forest model with hyperparameters to prevent overfitting.

To test the model, I performed a cross-validation to estimate the model performance. It achieved an accuracy of 90.67% with low variance of ± 0.0049. I then trained the model using the training data and evaluated the model on the test data displaying the confusion matrix, accuracy, and a classification report. As I was curious which columns helped to identify if a movie was considered successful or not, I used the feature importances attribute to analyze and display the top 10 most important features for the model's predictions.

Lastly, I created a DataFrame linking movie titles with the model's predictions for success.

Outcome:
The classification report indicates that the model performs well in predicting movie success with an overall accuracy of 82%. For not successful movies (class 0), it has a high precision of 91%, meaning it correctly identifies most movies as not successful when it predicts that. For successful movies (class 1), the model has a 70% precision and 86% recall, meaning it is a bit less accurate in predicting successful movies, but it does a good job of identifying most of them.
   
## Data Sources
OMDb API. OMDb API. OMDb API, www.omdbapi.com/. Accessed 17 Mar. 2025. Accessed 18 Mar. 2025. Accessed 20 Mar. 2025. Accessed 22 Mar. 2025

Mee's resoucse for Decision Tree

Bootcamp:UofM-VIRT-DATA-PT-09-2024-U-LOLC-MTTH. Supervised Learning, Week 20: Day 2 Activity 3. Data Science Course, Week 20, Day 2, Activity 3. UofM University, 25 Mar. 2025.

Susan's resources for K-Nearest Neighbor
Bootcamp:UofM-VIRT-DATA-PT-09-2024-U-LOLC-MTTH. Supervised Learning, Week 20: Day 2 Activity 7. Data Science Course, Week 20, Day 2, Activity 7. UofM University, 25 Mar. 2025.

University of Minnesota. (2024). UofM-VIRT-DATA-PT-09-2024-U-LOLC/20-Supervised-Learning/2/Activities/05-Ins_Random_Forest [GitHub repository]. Accessed on March 2025. I, Mai Houa Hang, used this repository for help with the Randomforest2025.ipynb on how to use the Random Forest classifer.

OpenAI. (2023). ChatGPT (Mar 14 version) [Large language model]. Accessed on March 2025. I, Mai Houa Hang, used this website for help with the Randomforest2025.ipynb step 34 (adding hyperparameters to the random forest model), step 35 (help on how to code the cross-validation) and step 38 (for help with the feature importance analysis).


