Movie Recommendation System Using Genetic Programming
This project implements a movie recommendation system using genetic programming (GP) with the MovieLens dataset. It leverages collaborative filtering and genre-based features to recommend movies for users, optimizing recommendations with a GP-based approach.
Table of Contents

Overview
Dependencies
Dataset
Setup Instructions
Code Structure
Running the Code
Output
Evaluation Metrics
Notes

Overview
The system uses the DEAP library to evolve a recommendation function via genetic programming. It processes user ratings and movie genres to generate personalized movie recommendations. The system employs parallel processing for efficiency and includes early stopping to prevent overfitting.
Dependencies
The following Python libraries are required:

numpy
pandas
scikit-learn
deap
pickle
logging
multiprocessing

Install dependencies using:
pip install numpy pandas scikit-learn deap

Dataset
The code uses the MovieLens dataset, specifically:

movies.csv: Contains movie IDs, titles, and genres.
ratings.csv: Contains user IDs, movie IDs, and ratings.

Download the dataset (e.g., MovieLens 100K or 1M) from GroupLens and place movies.csv and ratings.csv in the project directory.
Setup Instructions

Download the dataset:

Obtain movies.csv and ratings.csv from the MovieLens dataset.
Place them in the project directory or update the file paths in the load_data function.


Install dependencies:

Run the pip command above to install required libraries.


Environment:

The code is designed to run in a Python environment (e.g., Jupyter Notebook, Google Colab, or local Python setup).
For Colab, ensure the dataset files are uploaded or accessible (e.g., via Google Drive).



Code Structure

Data Loading:
load_data: Loads movies.csv and ratings.csv using pandas.


Data Splitting:
user_train_test_split: Splits ratings into training and test sets per user, with caching for efficiency.


Feature Engineering:
build_feature_maps: Creates user and item features, including average ratings and genre-based scores, with caching.


Recommendation Function:
recommend: Generates top-N movie recommendations for a user using a GP-evolved function.


Fitness Evaluation:
evaluate_individual: Computes precision, recall, and F1 score for recommendations.


Genetic Programming Setup:
Uses DEAP to define primitives (e.g., add, subtract, multiply, safe_div, tanh, abs) and evolve a recommendation function.


Early Stopping:
Implements an EarlyStopping class to halt evolution if no improvement occurs after a specified number of generations.


Main Execution:
Orchestrates data loading, splitting, feature building, and GP evolution, with parallel evaluation for efficiency.







The script will:
Load and preprocess the dataset.
Split data into training and test sets.
Build feature maps (user/item averages, genre scores).
Evolve a recommendation function using GP.
Output the best GP individual, its F1 score, and recommendations for a specified user (default: user ID 1).
Display evaluation metrics (precision, recall, F1 score).



Output
The script produces:

Best GP Individual: The evolved recommendation function.
Best F1 Score: The average F1 score across test users.
Total Runtime: Execution time in seconds.
Recommendations: Top-10 movie recommendations for a specified user (e.g., user ID 1), including titles and genres.
Evaluation Metrics: Average precision, recall, and F1 score across all test users, plus metrics for the specified user.

Evaluation Metrics
The system evaluates recommendations using:

Precision: Proportion of recommended movies that are relevant (in the test set).
Recall: Proportion of relevant movies that are recommended.
F1 Score: Harmonic mean of precision and recall, used as the fitness function for GP.

