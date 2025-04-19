Income Estimation Model – Preprocessing Steps 🛠️

To prepare the data for a Random Forest model, I followed these steps:

1. Descriptive Stats 📊  
   Took a quick look at the data — checked distributions, spotted weird stuff, and got a feel for what I was working with.

2. Feature Engineering 🧠  
   Built some new features using mean and max values:  
   - `payment_period` grouped by binned age ➡️ `payment_period_mean_by_bin_age`, `payment_period_max_by_bin_age`  
   - `amount` by `txn_description` ➡️ `amount_mean_by_txn_description`, `amount_max_by_txn_description`  
   - `balance` by `merchant_suburb` ➡️ `balance_mean_by_merchant_suburb`, `balance_max_by_merchant_suburb`

3. High Cardinality Cleanup 🧹
   Dropped categorical columns with 10+ unique values — too noisy, not worth it.

4. Handling Missing Values 🕳️➡️📦  
   Filled missing data using the mode (most common value). Simple and effective!

5. Categorical to Numeric 🔬  
   Used `get_dummies()` to convert categorical features into numeric ones — ensuring compatibility with machine learning algorithms.

Modeling Steps 🤖


I built three versions of the model:

Default model – just using the default parameters

Feature importance–based model – built using all features, but paying attention to their importance

Optimized model – built using only the most relevant features and tuned parameters

For each version, I evaluated the model using Train and Test R² scores to compare performance 📈

👉 For the optimized model, I only included features with importance > 1%, and then fine-tuned the parameters to get the best performance.

Univariate Analysis 📊


I performed univariate R² analysis on the optimized model to see how much each feature contributes on its own.

✅ I kept only the features where:

The Test R² score was above 5%, and

The feature didn’t cause overfitting (i.e., the gap between train and test R² was reasonable)

This helped me focus on the most stable and meaningful predictors 💡

Final Model 🧩


For the final model, I used only the top-performing variables — the ones that had the biggest impact on model accuracy.

✅ This helped simplify the model while keeping performance strong and stable.

The result: a cleaner, more focused model that does the job without unnecessary complexity 🚀
