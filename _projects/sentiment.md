---
layout: page
title:  "Sentiment Analysis"
date:   2016-01-01 08:43:59
permalink: /sentiment/
categories: ml
desc: "A machine learning code to analysize sentiments"
---

**Technologies**: python,spark-ml,twitter

**Repo Link**: https://github.com/Gaurav-Pande/Spark_Twitter_App.git

---
### Sentiment Analysis

Sentiment Analysis refers to the use of text analysis and natural language processing to identify and extract subjective information in textual contents. There are two type of user-generated content available on the web – facts and opinions. Facts are statements about topics and in the current scenario, easily collectible from the Internet using search engines that index documents based on topic keywords. Opinions are user specific statement exhibiting positive or negative sentiments about a certain topic. Generally opinions are hard to categorize using keywords. Various text analysis and machine learning techniques are used to mine opinions from a document [1]. Sentiment Analysis finds its application in a variety of domains.

Business Businesses may use sentiment analysis on blogs, review websites etc. to judge the market response of a product. This information may also be used for intelligent placement of advertisements. For example, if product "A" and "B" are competitors and an online merchant business "M" sells both, then "M" may advertise for "A" if the user displays positive sentiments towards "A", its brand or related products, or "B" if they display negative sentiments towards "A". Government Governments and politicians can actively monitor public sentiments as a response to their current policies, speeches made during campaigns etc. This will help them make create better public awareness regarding policies and even drive campaigns intelligently. Financial Markets Public opinion regarding companies can be used to predict performance of their stocks in the financial markets. If people have a positive opinion about a product that a company A has launched, then the share prices of A are likely to go higher and vice versa. Public opinion can be used as an additional feature in existing models that try to predict market performances based on historical data.

### Twitter:

Twitter is an online social networking and micro-blogging service that enables users to create and read short messages, called "Tweets". It is a global forum with the presence of eminent personalities from the field of entertainment, industry and politics. People tweet about their life, events and express opinion about various topics using text messages limited to 140 characters. Registered users can read and post tweets, but any unregistered users can read them. Twitter can be accessed via Web, SMS, or mobile apps. Traditionally a large volume of research in sentiment analysis and opinion mining has been directed towards larger pieces of text like movie reviews. Sentiment Analysis in micro-blogging sphere is relatively new. From the perspective of Sentiment Analysis, we discuss a few characteristics of Twitter:

Length of a Tweet The maximum length of a Twitter message is 140 characters. This means that we can practically consider a tweet to be a single sentence, void of complex grammatical constructs. This is a vast difference from traditional subjects of Sentiment Analysis, such as movie reviews. Language used Twitter is used via a variety of media including SMS and mobile phone apps. Because of this and the 140-character limit, language used in Tweets tend be more colloquial, and filled with slang and misspellings. Use of hashtags also gained popularity on Twitter and is a primary feature in any given tweet. Our analysis shows that there are approximately 1-2 hashtags per tweet, as shown in Table 3 . Data availability Another difference is the magnitude of data available. With the Twitter API, it is easy to collect millions of tweets for training. There also exist a few datasets that have automatically and manually labelled the tweets [2] [3]. Domain of topics People often post about their likes and dislikes on social media. These are not al concentrated around one topic. This makes twitter a unique place to model a generic classifier as opposed to domain specific classifiers that could be build datasets such as movie reviews.



### Machine Learning:

In this basic project I build a spark-ml app for analysis of twitter sentiment. This is just a very basic learning project that I did in my college to learn about machine learning. Currently I am working on stemming Algorithms to analyse the twitter streams more efficiently.


---


