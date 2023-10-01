# Project 3 ReadMe

---
## Problem Statement

With the advance of LLM being put on public display largely in part thanks to OpenAI via the advent of chatgpt we wanted to put to the test just how helpful some of their responses to everyday practical questions would fair. The scope of this project focuses on questions and responses gathered from Reddit, which provides a diverse collection of conversational text which will then be asked of OpenAI. Once we ask the question to OpenAI we will pull down the response the AI produces and compare it to top ranked human generated response on reddit and compare to see if our NLP model can identify which response came from a human and which one came from chatgpt. The goal is to get a model be as accurate as possible in making this disinction amongst the two option, essentailly making an optimal binary classification model to achieve this. Success will be evaluated based on the model's accuracy in correctly classifying the responses, as well as its ability to generalize to unseen data. In an era where AI-generated content is becoming ubiquitous, distinguishing between human and machine-generated text is crucial. Our stakeholders come from a variety of sources such as reddit platform/users, journalist, media, and end users of user generated content and AI content. 

---
## Data Collection

We gathered over 5000 unqiue question-answer pairs of top answers from reddit and then gathered the same question-answer pair from OpenAI. This dataset is also comprised of 5 unique question subreddit forums on various unique topics to provide distinct text diversity. The key here is that the dataset asked the same questions of everyday users on reddit and of OpenAI word for word. To ensure efficient data gathering we built a custom PRAW pipeline for reddit quetion answer pairs. The pipeline also was used to gather data from OpenAI as well with the OpenAI's API. A lot of thought and consideration was given towards server load in both our and the two platforms servers. While this data could have probably been obtained at a faster and more expensive rate, we opted to keep things running a bit manual and slow for both reddit and OpenAI to keep our cost down, keep server load down, and not crash our machine. I am pretty confident we were not a DDOS risk.

---

## Data Cleaning and EDA

We did a lot investigative work in exploring the data and did a bit of initial inspection when cleaning as well. When it came to handling missing data and rows we had to drop them. Initially we attempted to try and fill those rows with the appropiate data which majority was due to mising response from OpenAI as we feed the questions into the platform. However after several attempts the API wasnt returning any results. The cost of investigating why those specific cells was high and led to no answers. This left us with about 3700 rows. 

When it came to distribution analysis I would say we went into great depths. We analyzed reddit questions text, reddit answer text, and chatgpt text in the following segments: word frequency with and without stopwords, overlap of words at various sample sizes, n-gram analysis at various lengths, sentence length, sentence variety, unique words, unque word usage, clause count, clause usage, slang usage, and punctuation usage. After each segment we provided analysis and insight. Outliers were not addressed due to not being sure how to classify an outlier properly without removing too many additional rows.

Every segment in EDA was done so with the project objective in mind. Everything we analyzed help us understand what features and statistics would be most beneficial to us when it came time to model and give us a decent understanding of where bias and variance may occur. It ultimately helped us understand how to approach building our classification model and what direction it should most likely lean towards.

After a thorough investigation of the data we realized that the initial 5000 may get the job done but ideally at least 20,000 rows would of been ideal just because we know with language how much diversity is possible and the most amount possible would of course lead to better results. Nonetheless we had enough data to move forward and begin preprocessing and modelling. We would be able to adress the problem statement with little doubt. 

---

## Preprocessing and Modeling

In all of the models text data is put into matrix representations for us to see how well the models performed on the unseen data. Stopwords usage was explored in the previous section and was removed due to how prevalent it was in the text. 

The data was properly created into a proper dataframe and then train test split into a decent size and stratified the y as well. We had enough a training size to work with in our models. In all of our models we explained what we liked and didnt like and why we preferred some models over others and defended our reasoning for choosing the model we chose. We take a careful look at the performance of the models and properly evaluated success and failures.

---

## Conclusion and Reccomendations

When we look back at our main goal and what we trying to achieve I believed we address it well. This was a classfication model to determine whether a piece of text was human or ai. There wasnt any added significance on whether the model correctly predicted one more than the other. In fact it was expected it can do well at guessing either at a similar level. With that in mind we looked for a balanced model and optimized it based on its f1 score. We didnt have to worry about imbalanced data as we had a 50 50 split. Even with our train data it was effectively a 50 50 split. I believe our Logistic Regression model with the high paramters that we tuned it for did the best on the unseen data and performed well on its f1 score. I would reccomend as a base to carry forward with Logistic Regression if we learn new models. I would also give a bit of credit to rf classifier as well. If we had the needed compute and time we could have probably explored that as well. 


