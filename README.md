# CPE393-model-monitoring (References)

https://github.com/evidentlyai/ml_observability_course

https://www.analyticsvidhya.com/blog/2024/03/complete-guide-to-effortless-ml-monitoring-with-evidently-ai/

https://fullstackdeeplearning.com/course/2022/lecture-6-continual-learning/


Assignment
• Use airline delay causes dataset “DelayedFlights.csv” (dataset URL -
https://www.kaggle.com/datasets/giovamata/airlinedelaycauses)
• Create simulation data for reference and current dataset
• Develop a model quality report using evidentlyAI
• Discuss findings from the model quality report
• Submit GitHub URL(OR) Project folder with findings discussion.

## Results

Our check with Evidently shows the model behaves very differently once we move from Jan-Jun (reference) to Jul-Dec (current).

Data drift: only the Month column drifted (which is normal—we split the year in two). All other 29 columns look the same, so the feature space itself is stable.

Model quality: numbers get worse. MAE jumps from 0.9 min to 2.4 min and RMSE from 3.9 min to 10.6 min. The dummy baseline now matches the model, meaning our forest brings no real gain in summer/autumn. R² is still high (0.995 → 0.971) but the big max error (613 min) shows it struggles with outliers.

Take-away: the model trained on the first half-year doesn’t transfer well to the second half. We should retrain regularly or add season-related features (weather, holidays, airport load) before using it in production.

## Conclusion

The model trained on the first half-year doesn’t transfer well to the second half. We should retrain regularly or add season-related features (weather, holidays, airport load) before using it in production.

