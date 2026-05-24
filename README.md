# Capstone-project

A repository focused on what factor affect the number of user interactions on the Trivago website.

# About the dataset

The dataset contains information about the sessions of users of the Trivago website. The dataset has 988681 rows and 10 columns. 

# Data preparation

In the dataset, the hits column contains 369446 missing values. Since this is the target column, I removed these rows. There were also 5559 missing values in other columns, namely the path_id_set and session_duration columns. Since there are so few, I removed these columns as well. 

Since the row_num row is just to identify the row and does not contain any information about the session, I dropped this row. The other columns contain information that can be used in the machine learning models to predict the number of hits. 
