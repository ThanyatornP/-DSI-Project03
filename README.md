# Project 3 - Web APIs & Classification on subreddit

The objective of this project is to choose two subreddits from Reddit and use natural language processing and classification models to classify posts into the correct subreddit .

I choosed scuba diving subreddit and hiking subreddit as my two topics of interest because both of them are under same main community 'travel', but are also differentiated enough that it should be possible to train a machine learning model.

### The problem statement
In recent years, tavellers become ever-more worldly, the desire for adventure increases. Scuba diving and Hiking are adventure sport that allow us to explore the world above and under water. Therefore for travel agency who needs to seek for adventure traveler among the people on the internet. Therefore by knowing a dominant words that people use to discuss and search about scuba diving and hiking can helps these travel agencies spot their customers.

### Executive summary
Compared to the baseline accuracy score of 50% of classifying posts whether they are from the scuba diving subreddit, the best classification model is the logistic regression model with count vectorizer, which returned an accuracy score of 89.85%. The model performed better than multinomial naive bayes model and K nearest neighbors model.

The words that increase the likelihood of a particular post to be from the **scuba diving** and **hiking** are:  

![scuba_dom_words](https://user-images.githubusercontent.com/76549565/111750138-6d61e880-88c5-11eb-8cdf-2874abb995b7.png)
![hike_dom_words](https://user-images.githubusercontent.com/76549565/111750709-21637380-88c6-11eb-84d9-24a8ad3cc70a.png)



### Data 
Data use for NLP classification:

| Features              |type         |Description                                                          |
| ---                   |---          |---                                                                  |
| subreddit             |integer      |0 means Hiking, 1 means Scuba diving                                 |
| title                 |object       |title of the post                                                    |
| selftext              |object       |text of the post                                                     |


### Resutls and Conclusion
In this project we used Logistic Regression, Naive Bayes and K nearest neighbors to find best score, by using grid search to find the best parameters.

As Logistic Regression Model with Count Vectorizer got highest score in testing data set at this point Logistic Regression Model with Count Vectorizer shows that CV Score on Training data set and Test Score was closed together, which mean Logistic Regression Model with Count Vectorizer is the best model compares with others.

| Model | Vectorizer | CV Score on Traing data set | Test Score |
| --- | --- | --- | --- |
|Logistic Regression|Count| 89.35% | 89.85% |
|Logistic Regression|Tfidf| 89.62% | 89.02% |
|Multinomial NB|Count| 89.27% | 89.02% |
|Multinomial NB|Tfidf| 88.45% | 88.61% |
|Binomial NB|Count| 71.71% | 71.42% |
|Binomial NB|Tfidf| 71.71% | 71.42% |
|KNeighbors NB|Count| 72.40% | 75.77% |
|KNeighbors NB|Tfidf| 87.41% | 89.23% |

The accuracy of the final model shows that posts in scuba diving and hiking subreddit are fairly different, but still have a good amount of similarities

The differences are mainly due to creatures under the sea in scuba diving activity and how to describe location both activities

### Recommendations

For further model prediction improvement
<ul>
    <li>Optimize stop words</li>
    <li>Increase number of posts for training data to have more words </li>
    <li>Include more text such as  comments in each posts</li>
    <li>Use an image prediction as a features to classify </li>
</ul>

