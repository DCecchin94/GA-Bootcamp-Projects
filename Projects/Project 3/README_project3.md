# Project 3 

## Defining the Problem:
**The problem that was tackled for this project was to create the best model that would be able to classify if a post was given to it and determine from which of 2 subreddits it is from.** 

I decieded to choose the 2 subreddits that I frequent the most. Apple and Nespresso became the source for my data. 

## Gathering and Cleaning the Data

Personally, I was unable to create a loop that would have allowed me to streamline the acquisition of the data. So I took the long way to get 1000 posts from each subreddit. 
I utilized the Pushshift API that was made to crawl data from subreddits. 

Once I had collected the posts from each subreddit. I combined each one into their own Dataframe. I wanted to see if there were duplicates in any of these so I used the 'drop_duplicates()' function while focusing on the utc_created feature specifically. The utc_feature is generated every time a post is submitted. It is a form of a time stamp placed onto every post. 

I then combined both of the cleaned DataFrames into one dataframe for ease of use. 

I knew that when I had to train and test my data that the when using CountVectorizor, it only took in one variable for X and Y. To fix this problem combined the title feature and the selftext feature into one column called posts.

## Exploring the data

From looking around the internet for a more fun way to display the frequency of words in each subreddit, I came across a world cloud. So I created one for Nespresso and Apple. It was rather interesting to view exactly what was being talked about but in a much more condensed form.

Below is a Data Dictionary of all the useful features to understand: 

| Features    | Description                                                                 | examples                                                                                             |
|-------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| Title       | The title that the reddit post was given                                    | Apple to launch ARM based MacBook Pro by end of 2020                                                 |
| Selftext    | The actual content of the post                                              | What do you all think about Apple's new ARM based MacBooks? From this website X, it says Y, etc etc. |
| coffeePhone | The combined data frames of Nespresso and Apple                             |                                                                                                      |
| Posts       | A column made by combining Apple and Nespresso's Title and Selftext columns |                                                                                                      |
| Subreddit   | 1 is Apple and 0 is Nespresso                                               |                                                                                                      |                                                                                                 |



## Modeling the Data

I started it off by creating my X and Y variables to put into place as I have now created my train, test, split. I then moved to feature engeinnering by instantiating CountVectorizer for my X feature which was Posts. The CountVectorizer converts a collections of text into a matrix of token counts. The parameters I choose to include were:

stop_words = 'english'
ngram_range=(1, 3)
min_df=.01 

Stop words are words used in, this case, english, that do not provide much signifance to a sentence and can be removed without losing the meaning of the message the sentence attempts to communicate across. N-gram is a string of n words in any given row. So for example is "I have an Apple iPhone". 1,3 n-gram would produce "I have an", "have an Apple", "an Apple iPhone". This helps the model to better under the context of the text that is being feed to it.

The models I choose to use are Logistic Regression, Multinomial Naive Bayes, Decision Trees and Random Forests. 

They all performed without 1% of each other. The highest being the Random Forest. By "highest" it was the most consistent. All of the results were either 85% - 86%. 


## Answering the problem

The Random Forest performed the best with limited features that it was feed. If I were to perform this again there would be 2 things to change.
1) More data, much more data.
2) Using the posts per comment on each subreddit. 

