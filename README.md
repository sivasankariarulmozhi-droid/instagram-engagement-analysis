# Instagram Engagement Analysis
*(sourced from a multi-platform social media dataset, filtered to Instagram)*

A data analysis project exploring what drives post engagement on Instagram:content type, audience size, posting time, and account verification — using exploratory analysis, hypothesis testing, and a predictive model.

## Business Question

What post and account characteristics are associated with higher engagement rates on Instagram, and can engagement rate be predicted from them?

## Dataset

[Social Media Engagement Dataset](https://www.kaggle.com/datasets/aviral342/social-media-engagement-dataset) (Kaggle): 5,000 social media posts across six platforms (Instagram, Twitter, Facebook, LinkedIn, TikTok, YouTube), filtered to Instagram posts only for this analysis. Features include content type, category, engagement metrics (likes, comments, shares, views, saves, engagement rate), follower count, influencer tier, and verification status.

## Key Findings

**1. Reels significantly outperform other content types**

Reels achieved ~11.7% average engagement rate, roughly 85% higher than Photos or Stories (~6.3%) and notably ahead of Carousels (~8.4%).

**2. Smaller accounts see stronger engagement rates**

Nano-influencers showed dramatically higher engagement rates than Micro, Mid-tier, and Macro accounts. Follower count was the strongest correlate of engagement rate in the dataset (r = -0.23), reach and engagement rate trade off against each other.

**3. Verification status has no measurable effect**

A two-sample t-test comparing verified vs. non-verified accounts found no statistically significant difference in engagement rate (t = 0.541, p = 0.589). Verification badges don't move engagement ,audience size does.

**4. Posting time shows a mostly flat pattern**

Outside of a few isolated spikes (likely single high-performing posts rather than a reliable trend), engagement rate did not vary strongly by day of week or hour of day in this dataset.

**5. Engagement rate is difficult to predict from these features alone**

A linear regression using content type, category, follower count, verification status, and posting hour explained only ~13% of the variance in engagement rate (R² = 0.132, MAE = 11.57). This suggests engagement is driven substantially by factors not captured in this dataset (caption quality, visual content, audience relationship), and that the relationship between follower count and engagement is likely non-linear, a tree-based model such as Random Forest would likely perform better.

## Recommendations

- Prioritize Reels over static photo/story content to lift engagement rate.
- Don't equate "influencer status" or verification with engagement value,evaluate creators on demonstrated engagement rate, particularly smaller accounts.
- Treat posting-time optimization as lower priority relative to content format and audience-size targeting, given the flat pattern observed here.

## Methodology

1. **Data cleaning**: filtered dataset to Instagram posts, parsed timestamps, engineered `Hour` and `DayOfWeek` features.
2. **Exploratory analysis**: engagement rate by content type, influencer tier, and posting time; correlation analysis across engagement metrics.
3. **Hypothesis testing**: two-sample t-test (Welch's) comparing engagement rate between verified and non-verified accounts.
4. **Predictive modeling**: linear regression pipeline (one-hot encoding + `LinearRegression`) predicting engagement rate from content type, category, follower count, verification, and posting hour.

## Tools Used

Python, pandas, NumPy, Matplotlib, Seaborn, SciPy, scikit-learn — in Google Colab.

## How to Run

1. Open `instagram_engagement_analysis.ipynb` in Google Colab.
2. Run cells in order — the notebook downloads the dataset automatically via `kagglehub`.

## Limitations

Engagement metrics (likes, comments, shares, views, saves) showed very low correlation with each other (0.00–0.10), which is unusual for organic social data and suggests some metrics in this dataset may be synthetically generated rather than fully reflecting real user behavior. Findings should be read as illustrative of an analytical approach rather than definitive claims about real-world Instagram behavior.
