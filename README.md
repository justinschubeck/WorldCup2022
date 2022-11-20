<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://www.si.com/soccer/2018/07/14/world-cup-trophy-weight-height-size-history-details">
    <img src="images/trophy.jpg" alt="Logo" width="150" height="150">
  </a>

  <h3 align="center">Machine Learning FIFA World Cup 2022 Predictions</h3>
  <p align="center">
    by: [Justin Schubeck](https://www.linkedin.com/in/justinschubeck/)
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
This project consists of 

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
The user can choose to run the Jupyter notebook without making any edits. The ```final_model = ``` line can be changed to any of the models. The options are ```gb```, ```rf```, ```svm```, or ```lr```. Other models could also be added. The results will be printed to the screen. If the user is to choose any other set of data, it would have to be preprocessed in the same way. Additional features could also be added and analyzed if the user would like to. 

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