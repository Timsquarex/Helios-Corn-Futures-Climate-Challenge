# Helios Corn Futures Climate Challenge (Kaggle Competition)
## Team: DrinkMoreWater (Me and William, team of 2)

<p>
This repository is focusing on the process of
<ol type='1'>
    <li>Exploring the main dataset and figuring out the classification of the dataset depends on regional
    climate types, hemisphere and their corn planting seasonality</li>
    <li>Focusing heavily on the feature engineers of the pure climate variables as this is the main part of the competition.</li>
</ol>
</p>

<p>
For this repository, we could categorise the file into the state of:
<ol type='1'>
    <li>Light EDA on main dataset</li>
    <li>Feature Engineering exploration and backtesting by using my teammate's (William) API.</li>
    <li>Approach of feature selection</li>
    <li>My final submission (59.34) in private scoreboard</li>
</ol>

- Data: 
    - Dataset_by_countries directory (from index.qmd)
    - North_1_Hemisphere directory (from index.qmd)
    - North_2_Hemisphere directory (from index.qmd)
    - South_Hemisphere directory (from index.qmd)
    
    - corn_climate_risk_futures_daily_master.csv (main dataset from Kaggle)
    - corn_regional_market_share.csv (dataset from Kaggle)
    - corn_regional_climate_type.csv: Classified by Koppen climate type (by William)
    - corn_regional_hemisphere.csv: Classified by using hemisphere (by William)

- harvest_season_plots: images saved (from harvest_period_plots.py)

- requirements.txt: libraries required.

- Phrase 1: Light EDA
    - index.qmd: Splitting dataset by using Koppen Climate Type, hemispheres, and mapping planting seasonality by integers. *Data/Dataset_by_countries, North_1_Hemisphere, North_2_Hemisphere, South_Hemisphere*

    - index_2.qmd: Using subsets to plot time series plots, distributional plots (on cliamate and corn futures variables).

    - harvest_period_plots.py: The file to plot planting seasonality for each regions, and saved them into *harvest_season_plot* folder.

- Phrase 2: Heavy feature engineering
    - feature_engineering_1.ipynb: for engineering new climate types with different equations, including heatwaves, coldwaves, flood, storms, and wildfires.

    - feature_engineering_2.ipynb: for engineering regime detection (La Nina, and El Nino) features, but ended up, those calculations became weather forecasting approach.

    - baseline_features_notebook.ipynb: baseline features modified by William, and used as our team baseline, and I tried and error different approaches in this notebook.

    - with_pca_attempt.ipynb: try to fit PCA approach to see if it is possible to engineer meaningful features.

    - helios_submission_1.ipynb: try the baseline that given by the host of the competition, and added my heatwaves, coldwaves, flood, storms, and wildfires climate risks to get a better result (but it didn't improve CFCS).

    - helios_submission_2.ipynb: try the baseline from Kaggle discussion, and added new climate risks types to get a better result (it does improve +0.6 CFCS, but not much).

    - helios_submission_3.ipynb: We used our own baseline notebook, and did non-linear transformation, lag features, new climate types features, and ended up we moved to Kaggle notebook since the dataset are too large to handle.

- Phrase 3: The most important part to show the final_submission (P.S. I have large dataset file, therefore it might not work locally but it works in Kaggle) 
    - final_feature_engineering.ipynb: This includes final feature engineering approaches we used in our final submission, and also how I saved the correlation results into csv and combined them together to select the best subset features. *final_result_corr_2.csv*

    - samplings.ipynb: after done the final feature engineering, we have large dataset, so I decided to split into 20 subsets randomly and to test the consistent performance of different features (the first filter: I only chose the features with 0.6 avg_sig_corr above into the next stage of filtering).

    - samplings_result.ipynb: with the second filtering and the third filtering, I chose the only consistent top features in 20 subsets by ranking them according to sig_corr_ratio 

        - The features need to place above top 200 in sig_corr_ratio in every subsets (ended up, we just only have 2 features in this second filtering), and 

        - The features need to place above top 200 in avg_corr_ratio in every subsets (ended up, we just only have 16 features in this third filtering).

        - Summary: ended up, we filtered the features from ~13,000 features into 18 features for the final_submission.ipynb

        - **Reasons of doing this: We realised that our feature with the highest avg_sig_corr does not always perform well in test data, that's why we tried to select a certain amount of features with consistent performance to optimise the score and prevent the overfitting problem.**

    - final_submission.ipynb: 


- Backtesting API by William (teammate), includes:
    - cfcs.py
    - CFCS_API.txt

</p>
