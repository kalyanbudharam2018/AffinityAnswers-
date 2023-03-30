# AffinityAnswers-

1.	Imagine there is a file full of Twitter tweets by various users and you are provided a set of words that indicates racial slurs. Write a program that can indicate the degree of profanity for each sentence in the file.  Write in any programming language (preferably in Python) - make any assumptions, but remember to state them. 

Answer:

import re

# Assume that the set of racial slurs is given as a list of strings
racial_slurs = ['slur1', 'slur2', 'slur3', ...]

# Define a function to calculate the degree of profanity for a given sentence
def calculate_profanity(sentence):
    # Convert the sentence to lowercase for case-insensitive matching
    sentence = sentence.lower()
    # Count the number of racial slurs in the sentence using regular expressions
    count = sum([len(re.findall(slur, sentence)) for slur in racial_slurs])
    # Return the degree of profanity as a percentage of the sentence length
    return count / len(sentence) * 100

# Assume that the tweets are stored in a file, one tweet per line
with open('tweets.txt', 'r') as file:
    # Iterate over each tweet in the file
    for tweet in file:
        # Calculate the degree of profanity for the tweet
        profanity = calculate_profanity(tweet)
        # Print the tweet and its degree of profanity
        print(f'Tweet: {tweet.strip()}')
        print(f'Degree of Profanity: {profanity:.2f}%')
        print()






2.	Which is an interesting data set you discovered recently? Why is it your favorite? No datasets on Kaggle, please. 

Answers:

One interesting dataset that I discovered recently is the "COVID-19 World Vaccination Progress" dataset, which is available on the Our World in Data website (https://ourworldindata.org/covid-vaccinations).

This dataset provides daily updates on the number of COVID-19 vaccinations administered in different countries and regions around the world, as well as the type of vaccine used and the total number of doses administered. It also includes information on the population of each country or region, allowing for analysis of vaccination rates and coverage.

I find this dataset particularly interesting because it provides real-time information on a critical public health issue that is affecting people all over the world. It allows for analysis of the effectiveness of different vaccination strategies, and can help inform decision-making around vaccine distribution and prioritization. Additionally, as more data is added to the dataset over time, it provides a valuable resource for tracking the progress of the COVID-19 pandemic and the global vaccination effort.





3.	The following questions test your aptitude for interacting with databases. The questions are based off the following public SQL DB: https://docs.rfam.org/en/latest/database.html
a.	How many types of tigers can be found in the taxonomy table of the dataset? What is the "ncbi_id" of the Sumatran Tiger? (hint: use the biological name of the tiger)


SELECT COUNT(*) AS num_tigers, ncbi_id
FROM taxonomy
WHERE species = 'Panthera tigris'
GROUP BY ncbi_id;


SELECT ncbi_id
FROM taxonomy
WHERE species = 'Panthera tigris sumatrae';


b.	Find all the columns that can be used to connect the tables in the given database.

The columns are:

ncbi_id int(10)
rfamseq_acc varchar(20),
clan_acc varchar(20),
rfam_acc varchar(20)






4. 	This question is to test your aptitude for writing small shell scripts on Unix. You are given this URL https://www.amfiindia.com/spages/NAVAll.txt. Write a shell script that extracts the Scheme Name and Asset Value fields only and saves them in a csv file. 


Answer:

#!/bin/bash

# Download the NAVAll.txt file from the URL
curl -o NAVAll.txt https://www.amfiindia.com/spages/NAVAll.txt

# Extract the Scheme Name and Asset Value fields and save them in a CSV file
awk -F ';' '{print $4 "," $11}' NAVAll.txt > scheme_assets.csv

# Clean up the downloaded file
rm NAVAll.txt

