# Recommendations with IBM
##Introduction
This project aims at analyzing the interactions that users have with articles on the IBM Watson Studio platform, and make recommendations to them about new articles they will like. Below you can see an example of what the dashboard could look like displaying articles on the [IBM Watson Platform](https://dataplatform.cloud.ibm.com/https://dataplatform.cloud.ibm.com/community?context=wdp)

The goal is to write a recommendation engine that shows the articles that are most pertinent to a specific user.

The project consists of the following parts:

### I. Exploratory Data Analysis

Data exploration is conducted and basic analysis is made. The dataset contains a list of articles and a list of user interactions with these articles, i.e. one entry everytime a user clicked on a item. It does *not* contain any ratings.

### II. Rank Based Recommendations

Rank-based recommendations are created. Approach: find most popular articles based on the most interactions.

### III. User-User Based Collaborative Filtering

In order to focus more on the known profile of each customer and to get more personal recommendations, collaborative filtering is implemented, as well:

- For any given user, the other users are sorted based on similarity to their 'click history'. Articles of the most similar users are recommended for a given user.
- This approach is improved by ranking equally similar users by their overall count of interactions.

### V. Matrix Factorization

Finally, matrix factorization based on Singular Value Decomposition is applied to derive recommendations. Steps involved:

- Derive a reasonable train/test split on the user interaction data
- Build a user-article-matrix on both sets and define the comparable overlap (i.e. users and articles that are contained in both sets and thus are not subject to the cold-start-problem)
- The test matrix is predicted based on the train matrix with different parameters for the number of latent features. The results of each parameter are plotted and discussed.

A discussion of possible real-world evaluation is conducted.

## Requirements

The requirements are defined in `requirements.txt`, basically consisting of:

- Numpy
- Pandas
- Matplotlib
- Jupyter Noebook

## Requirements

The requirements are defined in `requirements.txt`, basically consisting of:

```
.
├── README.md
├── Recommendations_with_IBM.html
├── Recommendations_with_IBM.ipynb (Main Jupyter Notebook)
├── data (Data from the IBM Watson Platform)
│   ├── articles_community.csv
│   └── user-item-interactions.csv
├── requirements.txt
├── top_10.p (Pickles for the matrix factorization)
├── top_20.p (Pickles for the matrix factorization)
├── top_5.p (Pickles for the matrix factorization)
└── user_item_matrix.p (Pickles for the matrix factorization)
```