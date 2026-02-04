# 🎬 Movie Recommendation System
## 1. Project Overview

Movie streaming platforms must keep users engaged by recommending content they are likely to enjoy. With thousands of movies available, users often feel overwhelmed, and poor recommendations can lead to reduced watch time, dissatisfaction, and customer churn.

This project builds a personalized movie recommendation system using the MovieLens Small dataset, combining collaborative filtering and content-based filtering to generate Top-5 movie recommendations for users while addressing data sparsity and cold-start challenges.

## Business Problem

- Users are overwhelmed by large movie catalogs

- Poor recommendations reduce engagement and retention

- Platforms need personalized, accurate recommendations

## Project Objectives

- Predict ratings for unseen movies

- Generate personalized Top-5 movie recommendations

- Evaluate performance using:

   1. RMSE (rating prediction)

   2. Precision@5 and Recall@5 (Top-N recommendations)

- Address cold-start problems using a hybrid recommendation strategy

- Deliver actionable insights for product and analytics stakeholders

## Dataset

Source: MovieLens Small Dataset – GroupLens

- Users: 610

- Movies: 9,742

- Ratings: 100,836

- Rating Scale: 0.5 – 5.0 (explicit feedback)

- Metadata: Movie titles and genres

🔹 The dataset is highly sparse (~98.3%), which motivates the use of matrix factorization and hybrid methods.

## Methodology

1. Exploratory Data Analysis (EDA)

- Analyzed rating distributions and temporal trends

- Identified popularity bias and sparsity patterns

- Explored most-rated and least-rated movies

- Processed genre information for content-based filtering

2. Modeling Approaches
   
🔹 Baseline Model

- Predicts ratings using global and user-level averages

- RMSE: ~0.87

🔹 Item–Item Collaborative Filtering (kNN)

- Cosine similarity between movies

- RMSE: ~0.98

- Limited performance due to sparsity

🔹 Matrix Factorization (SVD)

- Captures latent user preferences and movie characteristics

- Hyperparameter tuning via GridSearchCV

- Best RMSE: 0.867

- Outperformed baseline and kNN models

## Hybrid Recommendation Strategy

To mitigate cold-start issues:

- Primary: SVD-based collaborative filtering

- Fallback: Content-based filtering using movie genres

- Ensures recommendations are available even for:

  1. New users

  2. Newly added movies

This mirrors real-world recommender system architectures.

## Evaluation Metrics

Metric	       Score
RMSE (SVD)	    0.867
Precision@5	    0.698
Recall@5	       0.080

Interpretation:

- ~70% of Top-5 recommendations are relevant

- System prioritizes high-quality recommendations

- Lower recall reflects realistic Top-N trade-offs in sparse datasets

## Key Insights

- Most ratings fall between 3 and 4

- Users tend to rate movies they already expect to enjoy

- SVD generalizes well in sparse environments

- Hybrid strategy improves robustness and coverage

## Tech Stack

Python

pandas, numpy – data processing

matplotlib, seaborn – visualization

scikit-learn – similarity computations

Surprise – collaborative filtering models

📁 Project Structure
├── Dataset/
│   ├── movies.csv
│   └── ratings.csv
├── notebooks/
│   └── movie_recommendation_system.ipynb
├── README.md

## Results

SVD with tuning delivers the strongest predictive performance

Hybrid approach ensures recommendations in cold-start scenarios

Top-5 recommendations are interpretable, personalized, and relevant

Visualizations provide actionable insights for business stakeholders

## Limitations

Cold-start issues are reduced but not fully eliminated

Limited content features (genres only)

Niche genres may be under-represented

## Future Work

Incorporate richer metadata (actors, directors, keywords)

Use weighted hybrid models for better balance

Deploy real-time recommendation pipelines

Extend to implicit feedback (watch history, clicks)

## Conclusion

This project demonstrates how matrix factorization combined with content-based filtering can deliver accurate, scalable, and business-ready movie recommendations. The hybrid strategy improves reliability in real-world scenarios and provides meaningful insights for improving user engagement and retention.
