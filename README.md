# Revenue Forecasting Model for Sales Opportunities

This project involves building a **revenue forecasting model** using historical sales opportunities and email interaction data to predict company revenue over multiple future time horizons. The data is sourced from Relatas, where I completed an internship developing AI-driven sales insights.

The model forecasts monthly, quarterly, and yearly revenue, helping the business with financial planning and reporting by predicting which sales opportunities are likely to close and their expected revenue impact.

## Problem Statement

Given historical sales opportunity data and email interactions between sales teams and customers, the goal is to forecast:

- Revenue for the **current month**

- Revenue for the **current quarter**

- Revenue for the **full financial year**

Using data starting from 2016, the model forecasts revenue for the remainder of 2017 (as a back-test) and for the year 2018.

The challenge includes:

- Handling in-progress sales opportunities with expected close dates.

- Leveraging email interaction data with NLP techniques to enhance prediction accuracy.

- Comparing forecasted revenue against actual outcomes for model validation.

## Dataset

- **Opportunities Data**: Details about sales opportunities including stage (Won, Lost, In Progress), close dates, revenue amount, etc.

- **Email Interaction Data**: Extracted email text and metadata capturing communication between sales teams and clients.

## Solution Approach

### High-Level Design

#### 1. Data Preprocessing:

- Clean and merge opportunity and email data.

- Label opportunities as won/lost or in-progress based on stages and close dates.

- Extract time-based features (month, quarter, year).

#### 2. Feature Engineering:

- Extract features from email text using NLP techniques (e.g., sentiment analysis, keyword extraction).

- Use opportunity metadata (deal size, customer segment, region).

- Incorporate temporal patterns (seasonality, historical win rates).

#### 3. Modeling:

- Use classification models (Random Forest, Gradient Boosting) to predict probability of closing won.

- Use regression models to estimate expected revenue from in-progress opportunities.

- Combine predictions to forecast revenue for given periods.

#### 4. Evaluation & Back Testing:

- Train models on data before 01 Oct 2017.

- Predict revenue for Oct-Dec 2017 and compare with actuals.

- Calculate accuracy and % deviation.

- Tune model using various features including NLP-derived sentiment scores.

#### 5. Forecasting 2018:

- Use trained model to forecast Jan 2018, Q1 2018, and full year 2018 revenue.

## Technical Architecture

```mermaid
flowchart TD
    A[Opportunities Data] --> B[Data Preprocessing]
    C[Email Interactions] --> B
    B --> D[Feature Engineering]
    D --> E[NLP Feature Extraction\n(Sentiment, TF-IDF)]
    E --> F[ML Models\n(Classifier, Regressor)]
    F --> G[Revenue Forecast\n(Monthly, Quarterly, Annual)]
```

## Algorithms Used

### - NLP:

- Sentiment Analysis (VADER / TextBlob)

- TF-IDF Vectorization for email text

- Named Entity Recognition for customer mentions

### - Machine Learning:

- Random Forest Classifier / XGBoost for opportunity outcome prediction

- Linear Regression / Gradient Boosting Regressor for revenue amount prediction

## Usage

1. Load historical data (opportunities.xlsx, sales-pipeline.xlsx).

2. Preprocess and extract features.

3. Train the model on historical data up to 01 Oct 2017.

4. Run forecasts for:

- October 2017 (month)

- Q4 2017 (Oct-Dec)

- Full 2017 financial year

5. Perform back testing by comparing forecasted revenue with actual.

6. Forecast revenue for 2018 periods (Jan, Q1, full year).

7. Analyze results and adjust features or model parameters as needed.
