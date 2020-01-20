# soccer-player-archetype-clustering
Clustering soccer players using by using FIFA 2019 player attributes data.

Emre Dogan  
January 19, 2020

## Motivation
- Replacing an important player in a soccer team is a critical task.
- Clubs fail to replace these players after they retire/leave.

News for the break-up of Alex de Souza     |  News for the break-up of Cristiano Ronaldo
:-------------------------:|:-------------------------:
![](figure/alex_leave.png)  |  ![](figure/ronaldo_leave.png)


- Finding similar players having a similar gameplaying archetype might help clubs to replace these players more easily.


## Dataset
- [FIFA 19 complete player dataset.](https://www.kaggle.com/karangadiya/fifa19)

- 88 different informative attributes for each player.
- Within this study, position attributes (i.e. LS, ST, ST, RS) are not used. (might be a good future work.)


## Approach
First, by using the attributes of each player, some new features are generated in the following way:



| Generated Features| Attributes Used|
| ------------- |:-------------:|
| Pace     | Acceleration, Sprint Speed|
| Shooting | Finishing, LongShots, Penalties, Positioning, ShotPower, Volleys|
| Passing | Crossing, Curve, FKAccuracy, LongPassing, ShortPassing, Vision|
| Dribbling | Agility, Balance, BallControl, Composure, Dribbling, Reactions|
| Defending | HeadingAccuracy, Interceptions, Marking, StandingTackle, SlidingTackle|
| Physical | Aggression, Jumping, Stamina, Strength|


Each generated feature is concluded by averaging the corresponding attribute stats. Also, height and weight clumns are cleaned (removing ' and unit abbreviations).

Then, by considering all these features, k-means clustering algorithm is used in order to maximize the intra-class similarity and minimize the interclass similarity between players.


**How to decide the optimal number of clusters (k value) ?**  
Deciding on k value(number of clusters) is a critical step in clustering task. There are many different appraoches to decide k value, the most popular one: elbow method. 

*Elbow method* is a heuristic to determine the optimal number of clusters, by selecting the value of k at the “elbow” ie the point after which the distortion/inertia start decreasing in a linear fashion. In order to see optimal k value, a range of values [2, 15] is used as k value to observe the distortion as a result of clustering task.


<p align="center">
  <img width="460" height="300" src="figure/elbow_result.png">
</p>