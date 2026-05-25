# Capstone-project

A repository focused on what factor affect the number of user interactions on the Trivago website.

# About the dataset

The dataset contains information about the sessions of users of the Trivago website. The dataset has 988681 rows and 10 columns. 

# Data preparation

In the dataset, the hits column contains 369446 missing values. Since this is the target column, I removed these rows. There were also 5559 missing values in other columns, namely the path_id_set and session_duration columns. Since there are so few, I removed these columns as well. 

Since the row_num row is just to identify the row and does not contain any information about the session, I dropped this row. The other columns contain information that can be used in the machine learning models to predict the number of hits. With the path_id_set column, I split this into two columns, on with the number of entries in that row to represent the number of locations visited, and one with the first entry in this row.

# Exploratory data analysis

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/32671487-41bf-4a37-9717-9e5117aa4e55" />
The most common number of hits per session is 3, with about 100000 sessions having 3 hits. The number of hits then decreases and has a long tail, with the highest number of hits in a session being 4174.

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/04707502-e33a-4d1e-b307-650caa8358f2" />
This graph shows that the device used for the session can have a large impact on the average number of interactions per session. Devices with an agent ID of 3, 4 or 5 have a average number of hits of about 2, whereas most other devices have an average number of hits of 15 to 25. 

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/7e2bf911-eac5-4388-9314-7a0e47f66a43" />
Most entry pages have a average number of interactions less than 50, but there are some with over 100. There doesn't seem to be a pattern with the numbers given to the different entry pages. It appears that this could have a large impact. 

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/a36c58d3-0548-486c-809d-c1131468e6b1" />
This graph looks at the channel the user came to the website through, for example search engine or email. There appears to be a lot of variation in the average number of interactions depending on the channel the user entered through.

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/9947810c-77c1-4671-afbe-ed15ab793b29" />
The average number of interactions depending on the time of day appears to vary between about 17 and 20, with it being higher at the start and lower at the end, but staying fairly conisitant in the middle.

<img width="580" height="455" alt="image" src="https://github.com/user-attachments/assets/784bdaca-c9a3-4990-bf9c-0d5d1cd5e923" />
The largest number of hits occur when the session length is less than 20000 seconds, which is about 5.5 hours. The lowest amount of interactions gradually increases as the session duration increases.

<img width="589" height="455" alt="image" src="https://github.com/user-attachments/assets/2faed5f7-5aad-4882-a656-edcc461e5591" />
The session duration and the hour of the day of the session appears to have a limit which decreases linearly. The highest duration of a session in the dataset is 86219 seconds, which is 23.9 hours, and the limit decreases of if there was another column for the hour of the day, the limit would be zero. This suggests to me that the dataset only contains sessions that were enclosed within one day and did not pass through midnight, which leaves some of the data that could change some the results to do with longer sessions starting later missing.

# Modeling

The best model was a random forest model. As shown below, the best result for the test root mean square error was when the max depth was 11.

<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/467084d9-de76-428d-a60f-6c1044ea518e" />

<img width="946" height="568" alt="image" src="https://github.com/user-attachments/assets/b47f6d57-6e93-448e-9c20-385b4dc5dc36" />

As shown in the SHAP analysis, the factors with the largest impact on the number of interactions were session duration, the entry page and number of entries in path_id_set, or the number of locations visited on the website during the session. 

# Results

The final random forest tree model that I made that includes all the columns has the session duration as the most important factor in determining the number of hits, with an importance of 0.52 and from SHAP analysis, an average SHAP value of +13.74, showing that an increase in session duration increases the number of interactions. The other features with an importance over 0.05 and SHAP value over +1 are the entry page, the number of entries in the path_id_set column and the first entry in the path_id_set column. While spending longer on the website increasing the number of interactions is expected and can't easily be acted on, identifying the best pages for interactions and using this to help decide what the website should look like and where links to the website go to could help increase the number of interactions.

# Next steps

The next steps with these results would be to look at how the amount of interactions affects the number and size of transactions through the website. It would also be useful to look at sessions which go over multiple days, since that appears to be missing in the dataset.
