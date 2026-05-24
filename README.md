# Capstone-project

A repository focused on what factor affect the number of user interactions on the Trivago website.

# About the dataset

The dataset contains information about the sessions of users of the Trivago website. The dataset has 988681 rows and 10 columns. 

# Data preparation

In the dataset, the hits column contains 369446 missing values. Since this is the target column, I removed these rows. There were also 5559 missing values in other columns, namely the path_id_set and session_duration columns. Since there are so few, I removed these columns as well. 

Since the row_num row is just to identify the row and does not contain any information about the session, I dropped this row. The other columns contain information that can be used in the machine learning models to predict the number of hits. 

# Exploratory data analysis



# Modeling



# Results

The final random forest tree model that I made that includes all the columns has the session duration as the most important factor in determining the number of hits, with an importance of 0.52 and from SHAP analysis, an average SHAP value of +13.74, showing that an increase in session duration increases the number of interactions. The other features with an importance over 0.05 and SHAP value over +1 are the entry page, the number of entries in the path_id_set column and the first entry in the path_id_set column. While spending longer on the website increasing the number of interactions is expected and can't easily be acted on, identifying the best pages for interactions and using this to help decide what the website should look like and where links to the website go to could help increase the number of interactions.

# Next steps

The next steps with these results would be to look at how the amount of interactions affects the number and size of transactions through the website. It would also be useful to look at sessions which go over multiple days, since that appears to be missing in the dataset.
