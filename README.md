### Problem Statement

    Pull at least 1,000 posts each from 2 subreddits forums (startups & startup_ideas) and build a classification model that identifies which subreddit each post came from with an accuracy score of at least 90%. 
    
    The classification models that will be examine are: Logistic Regression, Decision Tree, Random Forest and Extra Trees. These will all be examine and we will select the best model to productionize.  



### Data:

    I will be using post from the following reddit url:
        . https://www.reddit.com/r/Startup_Ideas/
        . https://www.reddit.com/r/startups/

    I collected 2 sets of data:
        . 1st dataset I got using the 'praw' method and these consisted of:
            . Startup - 900 rows
            . Startup_ideas - 991 rows
        . 2nd dataset I used the pushshift API method which consisted of:
            . Startup - 900 rows
            . Startup_ideas - 991 rows
    
    | FieldName 1 | DataType | Description |
    | --- | --- | --- |
    | title | text | The title of the post |
    | subreddit | integer | 1 represents startup and 0 for startup_ideas |
    | polarity | float | Sentiment Polarity of the title |
    | word_count | integer | The number of words in the title |
    | title_length | integer | The total number of characters in the title |

### Methodology:

  - Data Cleaning 
    - Use Regex to take out hyperlinks etc from the title
    - Removed punctuations & special characters
    - Making corrections to faulty data
    - Remove stop words for some of the models


### EDA:
    - Both datasets were very similar, having most words in commen
    - There were 45 titles which only consist of 1 word, but on visualizing the    data there was a clear distiction between which word respresents which dataset, I therefore chose to leave these rows in my dataset
    - The mode for the title was 10 words
    - The sentiment were mainly neutral


### Data Preprocessing
   - Data augmentation (such as encoding categorical variables)
   - 
   - Scaling
   - Vectorizing: CountVectorizer, TfidfVectorizer
   
   
### Modeling:
  - Features used: title
  - Model used: Logistic Regression, Decision Tree, Random Forest, Extra Trees, MultinomialNB
  - Gridsearching/hyperparameter tuning: n_estimators, max_depth, max_features, ngram_range, stop_words, min_df
  
### Results:
| Model | Train Score |	Test Score |
| --- | --- | ---|
| Logistic Regression (2nd dataset) |	0.99541 | 0.99333 |
| Logistic Regression - with Scaling |	1 |	0.7124 |
| Decision Tree |	1 |	0.72559 |
| Random Forest | 0.79496 |	0.78901 |
| Extra Trees Classifier |	0.78306 |	0.77511 |
  - Visualizations here are good
  
### Conclusions:
    - No matter how great your model is it can not cater for all possible data sets as I am seeing 99% accuracy on my final dataset while I saw an 80% on the previous set of data.
    - Although I got my desired results, I am unsure how my model will perform with another set of data
    - My Production model will be a toss up between my Logistic Regression and Random Forest Model. Initially the Logistic Model was performing better but after changing the params they are both performing equally as well

  
### Next Steps:
    - I would like to closely review both sets of my data to analysis what caused huge difference in the scores
    - I would Merged the dataset to see what results I would get to came up with a Model that will work well on both datasets
