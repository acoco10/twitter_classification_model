# News on Twitter

**Authors:** [Michael Wirtz](https://github.com/mwirtz946), [Aidan Coco](https://github.com/acoco10)

## Overview

This project analyzes the needs of The New York Times. The company is pursuing tweets as a possible avenue for new stories about a certain set of keywords. 

## Business Problem

The New York Times is looking to find possible stories on Twitter using a specific set of keywords. They quickly run into the problem of dual-meanings and an overload of query results. They have tasked a team to help them identify when a tweet is an event or not an event. Instead of having staff manually go through all tweets to find events, they want to possess a classifier that can automatically perform this duty.  

## Data

In order to help the New York Times, we utilized a [Kaggle dataset](https://www.kaggle.com/vstepanenko/disaster-tweets) possessing keyword query results and their corresponding labels (event or non-event). The data includes 11,000 tweets, with 219 keywords. The dataset also includes general location information, of which there were many missing values. 

The text data between the two classes is incredibly similar, so we had to look for small differences in our EDA process. 

The original classification of the dataset is disaster (positive class) and no disaster (negative class). 
When searching through the dataset's tweets and labels, we found that the data was less specific to disasters and could be more accurately be defined as event vs non-event. Therefore, we used this data to produce a model for the needs of the New York Times. 

Here's how we defined each: 

<table>
<tr>
<th> Target Classes</th>
</tr>
<tr>
<td>

<ul>
<li> <b>Event (1)</b>: tweets which factually describe a real and noteworthy occurance.</li>
<li> <b>Non-Event (0)</b>: tweets which do not factually describe a real and noteworthy occurance.</li>
</ul>

</td>
</tr>
</table>


## Methods

Before we could do anything else, we needed to decide what evaluation metric would be most appropriate for the business problem. We decided that F1 Score would be perfect, as it is a measure of the model's ability to differentiate between the two classes. 

Then, prior to modeling, we lemmitized the words in each tweets to increase the comparability of the tweets. From there we used TFIDF Vectorizer to get the relative uniqueness for each word in each tweet. 

We used KNN as a baseline classification model, which produced an F1 Score of 0.5044 and an Accuracy Score of 0.8773. 

From there, we used a Random Forest Classifier and a Naive Bayes Classifier to improve upon our baseline KNN model. 

Finally, since there were so many keywords in the dataset, we used our final model to predict on a dataset that we manually labeled. This dataset contained only the top 10 keywords for the positive class and the top 10 keywords for the negative class. 

## Results

Our Random Forest Classifer had a slight performance advantage over our basline model with an F1 score of 0.5851 and an Accuracy Score of 0.8896. Still, there was much room for improvement. 

Our Naive Bayes Classifier performed even better. After some hyperparameter tuning, we were able to achieve an F1 Score of 0.61 and an Accuracy Score of 0.88. 

When we used the Naive Bayes model on our manually-labeled dataset, we were pleasantly surprised with the results. The model performed extremely well with an F1 Score of 0.85 and an Accuracy Score of 0.949. 

## Conclusion

Our best model was the multinomial naive bayes classifier which got a cross validated F1 score around .61 and an accuracy score consistently over .88. This means that our model was 8% more accurate than guessing the dominant class and had a reasonable ability to distinguish between the two classes. From this we can say it would be a useful model to further narrow your search when trying to determine between events and non events, but not the end of the process. 

Our manually-labeled dataset, however, leads us to believe that the model performs relatively well on data that it had a higher level of exposure to. 

### Next Steps

#### 1. More Data

- 11,000 is not a small data set but NLP learning always does better with more entries to learn from. This dataset could easily be 100,000 tweets

#### 2. Use Pretraied Vectors 

- We wanted to implement some pretrained vectors with GLoVe from Standford but unfortunately there model is seemingly facing some legal trouble right now. Their vectors were trained by billions of tweets.
- We expiremented with Word to Vec but the vectors learned from our data set did not improve any of our models. This code was messy and not in the final notebook. 

#### 3. Nueral Net

- A nueral net did not seem worth additional effort with our data set, but if we scraped more tweets and got a sufficiently large data set it could provide more classification power. 

## For More Information

See the full analysis in the [Jupyter Notebook](./final_notebook.ipynb) or review this [presentation](./slides_successful_movie.pdf).

For additional info, contact Aidan Coco or Michael Wirtz at
[aidancoco@gmail.com](mailto:aidancoco@gmail.com) and [michaelwirtz88@gmail.com](mailto:michaelwirtz88@gmail.com), respectively.

## Repository Structure
