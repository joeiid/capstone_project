<<<<<<< HEAD
# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Song Popularity Classification

# Capstone Project: Song Popularity Classification

---


## Problem Statement:
---

Spotify spends millions of dollars every year on new artist and new songs on the mission of finding songs that will hit the charts. In 2021 Spotify spend $7 billion in royalties to artist and record labels in order to have their music on its platform. Unfortunately most of the songs that make it to spotify ends up being a waste of time invested and money spent. Spotify has hired me and my team to write a program that can identify if a song will be popular by analyzing the features of the song. For this project, we will be working with almost 600k songs to see if we can find what makes a song popular.


## Data:
---

Title: Spotify Dataset 1921-2020, 586,672 Tracks
Subtitle: Audio features of 586,672 tracks, popularity metrics of 1M+ artists
Source: Spotify Web API with 586,672 tracks
Creator: Yamac Eren Ay
Release Date (of Last Version): April 2021
Link to this dataset: https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-600k-tracks

### Data Dictionary

|Feature|Type|Description|                                 
|---|---|---|
|**popularity**|*int*|Popularity of tracks scores (0-100), scores were populated by Spotify and is scored by the number of times the song has been played.|
|**explicit**|*int*|Determines if the song is explicit or not.|
|**duration_ms**|*int*|Duration of track in milliseconds.| 
|**release_date**|*datetime*|The date the song was released on.| 
|**danceability**|*float*|Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.| 
|**energy**|*float*|Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.| 
|**key**|*int*|The key the track is in. Integers map to pitches using standard Pitch Class notation. E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on. If no key was detected, the value is -1.| 
|**loudness**|*float*|The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typically range between -60 and 0 db.| 
|**mode**|*int*|Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0.|
|**speechiness**|*float*|Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks.| 
|**acousticness**|*float*|A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.| 
|**instrumentalness**|*float*|Predicts whether a track contains no vocals. "Ooh" and "aah" sounds are treated as instrumental in this context. Rap or spoken word tracks are clearly "vocal". The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0.| 
|**liveness**|*float*|Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live.| 
|**valence**|*float*|A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).| 
|**tempo**|*float*|The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.| 
|**time_signature**|*int*|An estimated time signature. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure). The time signature ranges from 3 to 7 indicating time signatures of "3/4", to "7/4".| 
|**popularity_category**|*int*|This feature was created to make the popularity column binary. If a song had a popularity score above 0, a score of 1 was given to it. If a song had a popularity score of 0 a score of 0 was given.| 

----

## EDA
---

### HeatMaps
In these heatmaps we were able to see that popularity does not have a really strong correlation to one feature. The strongest one I noticed was 'loudness'(0.33), 'energy'(0.3), and 'explicit'(0.21). I would also be important to note that 'acousticness' had a negative correlation with a score of (-0.37), aswell with instrumentalness with a score of (-0.24).
Looking at the heat map gave a decent way to be able to see what features correlate to popularity and with each other. So far I did not see huge correlations between popularity and other features that were noticable. 'Key', 'Time Signature', and 'Mode' are also not as important to help categorize because when looking at the graphs they seem to be evenly distributed.

### Visualizing Data in Graphs
After splitting the popularity feature into binary, in some of the graphs we can clearly see how some features will noticeably have a good split, where if the song is popular it will have a higher score in the feature and if the song is not popular it will have a lower score. 'energy' and 'acousticness' are the two more obvious features that show us that relationship. For 'energy', if the song is popular, the 'energy' score will be much higher than if the song is not popular. 
I see something similar for 'acousticness', for 'acousticness' we have a negative correlation score. If the song is not popular, the 'acousticness' score will be much higher than if the song is popular. Even with the feature having a negative corelation with popularity, I still want to make sure we keep it because it is a very good way to be able to differentiate between popularity.
In a few of the other charts, the graphs seemed to mimick each other. Liveness is a good example of features that might not have much of an impact on the popularity score. The graph is almost identical to each other, popular just has a bigger graph because of the data imbalance. I still decided to keep those in because our data has very few features to work with.

### Feature Importance 
The feature importance model used a forest of trees to evaluate the importance of each feature. This gives me another view at what features are very important to keep to classify popularity. We can see that 'acousticness' is by far the most popular of the feautures, and we were also able to see that when comparing the graphs in the EDA II portion. We also see almost no imortance in 'key', 'time signature', and 'mode', which helps us confirm the analysis we did in EDA I.


## Modeling
---

In this notebook we are going over the different modeling and balancing techniques used for this project. The target for the modeling will be: • 'popularity_category'

#### The features used are:

• 'explicit'
• 'danceability'
• 'energy'
• 'key'
• 'loudness'
• 'mode'
• 'speechiness'
• 'acousticness'
• 'instrumentalness'
• 'liveness'
• 'valence'
• 'tempo'
• 'time_signature'

We saw in the EDA that some features had more impact than others when making a song popular, this will show us the impact the features will make through the modeling process. We also saw how umbalance the data was when splitting the popularity feature. These are the techniques used for balancing the data:

• Random Over Sampler: This works by randomly relecting examples form the minority class, with replacement, and adding them to the training dataset.

• Near Miss undersampling: Near Miss looks at the class distribution and randomly eliminates sample from the larger class. If two data point from the larger class are very close to each other in the distribution it is eliminated.

•Weight: Normally class weights give all the classes a equal importance regardless of how many samples each class has. Weights are set into place to give more weight(importance) to the minority class to balance the data.

#### Models chosen:
    • Logistic Regression
    • K-Nearest Kneighbors
    • Radom FOrest
    • XGBoost

#### Why did I choose these models?
When I was looking at what models to pick, I had to look at a few things. What models are best for classification? Which models are good for binary classification? Non-Linear relationships? The first thing I looked at was my EDA to see what kind of relationships my data has. Logistic Regression is one of the simpler and most used classification models so I included it to be my starting point for my classification models. Unfortunately my data was not very linear, to satify that I included the Random Forest model. Random Forest works really well for multiple feature selection, large data, and noise which made this a good choise. XGBoost is similar to Random Forest because it also uses Decision Trees, but works better for unbalanced data. KNearestNeighbors works by estimating the likelihood that a data point will become a member of one group or another based on the data points nearest to it. Since in some of the models we saw a seperation between the graphs, I thought it would be a good model to include.

### Model Summary:
For this project we will be looking more at accuracy, because we are looking at how well the model can predict popularity of a song.

Unbalanced modeling: Suprisingly the unbalanced models did not perform that bad. This could be because the data is very ubalanced and could be very overfit. The best performing model was Random Forest with a training score of 0.997988 and a test score of 0.945987.

Undersampling modeling: Undersampling performed the worst out of all the different balancing techniques used. The results were extremly over-fitt showing high train score and low test scores, and also has a very high variance score.

Oversampling modeling: Oversampling had the best results. The results had high training and test score with very low variance. The best model was Random Forest with a training score of 0.998528 and a test score of 0.944610. We will proceed with this model for model tunning. 

Weighted modeling: Weighted modeling also performed very well. Random Forest was also the best performing and had very similar scores to the oversampling. This is the second best data balancing technique.


## Hyperparameter Tuning: Random Forest

---

Hyperparameters is like the settings of an algorithm that can be adjusted to optimize performance. Hyperparameters must be set before training. In the case of a random forest, hyperparameters include the number of decision trees in the forest and the number of features considered by each tree when splitting a node. Because hyperparameter tuning is based on experimental findings rather than theory, the easiest way to identify the ideal settings is to test many different combinations and evaluate the performance of each model. However, assessing each model only on the training set can lead to overfitting, one of the most fundamental difficulties in machine learning.

We adjusted the following set of hyperparameters:

• n_estimators = number of trees in the foreset
• max_features = max number of features considered for splitting a node
• max_depth = max number of levels in each decision tree
• min_samples_split = min number of data points placed in a node before the node is split
• min_samples_leaf = min number of data points allowed in a leaf node
• bootstrap = method for sampling data points (with or without replacement)

Summary:

After doing some hyperparameter tuning with the best the model that originally gave us the best score we only got a 0.02% increase on our accuracy test score and our accuracy training score stayed about the same. The amount of time did not really benifit the model at all. Either way we did have pretty good success over all with our accuracy scores which was the goal.
=======
# capstone-project
>>>>>>> 8b145a4d987d00535a75df6572b552b2d5ac1108
