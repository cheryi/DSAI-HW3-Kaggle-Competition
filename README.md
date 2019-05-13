# DSAI-HW3-Kaggle-Competition

input folder contains training data and testing data.

Kaggle_process.ipynb is the process of downloading data and using kaggle api.

predict_future_sales_xgboost.ipynb is the main model of the competition, forked from [Feature engineering, xgboost](https://www.kaggle.com/dlarionov/feature-engineering-xgboost/output) and do some adjust.
The Documentation's link [here](https://nbviewer.jupyter.org/github/cheryi/DSAI-HW3-Kaggle-Competition/blob/master/predict_future_sales_xgboost.ipynb).

### Observation
The first time I forked the model and ran on kaggle's kernel, it all looks same as the original one. Then, I downloaded data and coded on my notebook(based on the forked model), the importance of feature changed and output(testing prediction) slightly decreased. Thus, I ran the original model(forked model) on my notebook and the strange thing happened. The importance of feature and output all changed, different from previous two, the RMSE still higher than original one. After surveying solutions to this problem, it might due to the race condition and random seed. Since the seed had been set fixed, I eliminated the discussion about seed and found that the andom sequence in one OS is not always the same in another OS. **The OS has an impact on xgboost seed generation.** After trying several times adjusting, the result still worse than the forked one, so I use the score from it finally. 



![image](https://github.com/cheryi/DSAI-HW3-Kaggle-Competition/blob/master/different_os.png)
Both 2 submission has same parameters but on different OS, top row is on Kaggle's kernel, bottom row is on macOS Mojave.
