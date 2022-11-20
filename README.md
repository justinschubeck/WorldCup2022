<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://www.si.com/soccer/2018/07/14/world-cup-trophy-weight-height-size-history-details">
    <img src="images/trophy.jpg" alt="Logo" width="150" height="150">
  </a>

  <h3 align="center">Machine Learning Predicting The 2022 FIFA World Cup</h3>
  <p align="center">
    by: <a href="https://www.linkedin.com/in/justinschubeck/">Justin Schubeck</a>
  </p>
</p>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#dependencies">Dependencies</a></li>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#running">Running</a></li>
      </ul>
    </li>
    <li><a href="#authors">Authors</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project
This project consists of collecting data from past international football results from June 14th, 2018, (Russia 2018 World Cup start date) until September 27th, 2022. There were 45 more matches between September 27th, 2022, and the 2022 World Cup, but those games were not documented in the dataset. Most of these games during the time period were also treated like practice, as players did not want to risk injury. Data was also collected for past official FIFA rankings during this time period. Therefore, any non-FIFA teams for which there was match data was excluded.<br />

The data was first cleaned for inconsistencies like date format and country name. The FIFA rank for each team at the time of each game was embedded. Data regarding the ranking datset was merged with the results dataset for both home and away teams.<br />

New features were then implemented to help predict a match result. Many features were added such as: result type, points gained, rank difference, and goal difference. Interactions of features were also compared such as dividing a previous feature by the opponent rank. Other features such as average goals scored, average goals conceeded, average rank of opponent, FIFA points earned, and average game points earned were tested as well. Many features were also experimented with across 5 games, 15 games, and all data. The type of game was also considered. The data was separated into friendlies, semi-competitive competitions, and competitive competitions. This is because many international friendly games are a second or third string squad and not taken seriously compared to a World Cup.<br />

Features were then analyzed to ensure none are too similar and to see which ones would best separate the classes. To do this, the 3-result option of a football game was converted to a binary output. Either the home team won, or the home team did not win. All features were then graphically analysed with violin plots to view distribution separation and jointpots to view similarity. The final input data consisted of the following features:
* ```rank_dif``` : difference in rank between home and away team for current game
* ```goals_dif``` : difference in mean goals scored between home and away team for all data
*	```goals_dif_l5``` : difference in mean goals scored between home and away team for last 5 games	
* ```goals_dif_l15``` : difference in mean goals scored between home and away team for last 15 games	
* ```goals_suf``` : difference in mean goals conceeded between home and away team for all data
*	```goals_su_l5``` : difference in mean goals conceeded between home and away team for last 5 games	
* ```goals_suf_l15``` : difference in mean goals conceeded between home and away team for last 15 games	
* ```dif_points``` : difference in mean points gained between home and away team for all data
* ```dif_points_l5```	: difference in mean points gained between home and away team for last 5 games
* ```dif_points_rank```	: difference in mean points gained per opponent rank between home and away team for all data
* ```dif_points_rank_l5``` : difference in mean points gained per opponent rank between home and away team for last 5 games
* ```goals_per_ranking_dif``` : difference in mean goals per mean rank between home and away team for all data 
* ```dif_rank_agst```	 : difference in rank between home team and away team for all data
* ```dif_rank_agst_l5``` : difference in rank between home team and away team for last 5 games
* ```is_friendly_0```	: friendly game
* ```is_friendly_1``` : semi-competitive competition
* ```is_friendly_2``` : competitive competition (continental or intercontinental championships and its respective qualification)<br />

Different classifiers were then fine tuned using a train-test-split of 80% train and 20% test. The data was scaled for numeric columns, and the models parameters were found using grid search with three cross validation splits. In the end, each model performed very similar, so Gradient Boosting was chosen. The final model was then trained on the entire dataset. The best values for each model chosen were:
* GradientBoostingClassifier(learning_rate=0.01, max_features='sqrt', min_samples_leaf=7, min_samples_split=3, random_state=7)
  * 95% Confidence Interval: (0.6682883037807136, 0.7336704743638524)
  * AUC Score: (Train=0.79, Test=0.80)
* RandomForestClassifier(max_depth=5, max_features='sqrt', max_leaf_nodes=150, min_samples_leaf=10, n_estimators=150, random_state=7)
  * 95% Confidence Interval: (0.6677231083331896, 0.7220428550008515)
  * AUC Score: (Train=0.79, Test=0.82)
* SVC(gamma=0.01, probability=True, random_state=7)
  * 95% Confidence Interval: (0.6661863143560298, 0.7300364097870049)
  * AUC Score: (Train=0.79, Test=0.78)
* LogisticRegression(C=0.01, max_iter=2000, random_state=7, solver='saga')
  * 95% Confidence Interval: (0.6633649326334179, 0.7400301112203043)
  * AUC Score: (Train=0.79, Test=0.78)<br />

For the predictions of the 2022 FIFA World Cup, the model would predict the probability of each match. Because the datasets had home field advantage bias, the predictor will run twice for each match (once with Team 1 as home, and once as Team 2 as home). The probability of winning will be determined by the model. If the results are one-and-one, then the match will be interpreted as a draw in the group stage. This will be performed for every match in the group stage, keeping track of the points table. Since the model does not predict goal differential, any tiebreakers will be determined by the higher average probabilities between the teams. In the knockout stages, if a one-and-one prediction occurs, the average of the probabilities between the two games will be the tie-breaker. This structure will predict the entire tournament.<br />

**It was heavily decided that Brazil would win the 2022 FIFA World Cup, followed by Belgium, then Argentina.**

<!-- GETTING STARTED -->
## Getting Started

### Dependencies
This project was run with the following package versions:

* NumPy 1.21.5
* Pandas 1.3.5
* Sklearn 1.0.2
* Scipy 1.7.3
* Matplotlib 3.5.1
* Seaborn 0.11.2

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/justinschubeck/WorldCup2022.git
   ```
2. Setup (and activate) your environment

### Running
The user can choose to run the Jupyter notebook without making any edits. The ```final_model =```  line can be changed to any of the models. The options are ```gb```, ```rf```, ```svm```, or ```lr```. Other models could also be added. The results will be printed to the screen. If the user is to choose any other set of data, it would have to be preprocessed in the same way. Additional features could also be added and analyzed if the user would like to. 

**File Descriptions**
* ```fifa_ranking.csv```: This is a custom subset of the *FIFA World Ranking 1992-2022* [dataset](https://www.kaggle.com/datasets/cashncarry/fifaworldranking?resource=download). 
* ```results.csv```: This is a custom subset of the *International football results from 1872 to 2022* [dataset](https://www.kaggle.com/datasets/martj42/international-football-results-from-1872-to-2017).
* ```WorldCup2022.ipynb```: This Jupyter Notebook contains the setup, feature engineering, feature analysis, model tuning/analysis, and predictions.
* ```Predictions/```: This folder contains the WorldCup2022.pdf run for each of the following models: Gradient Boosting, Random Forest, Support Vector Machine, and Logistic Regression. The filled out bracket pdf for each model is also included.

<!-- Authors -->
## Authors
* Justin Schubeck - jschubeck7@gmail.com

Project Link: [https://github.com/justinschubeck/WorldCup2022](https://github.com/justinschubeck/WorldCup2022)


<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements

* README Template: [Catia Silva](https://faculty.eng.ufl.edu/catia-silva/)
* Basic Structure: [Sergio Pessoa](https://www.kaggle.com/code/sslp23/predicting-fifa-2022-world-cup-with-ml)

## Thank you