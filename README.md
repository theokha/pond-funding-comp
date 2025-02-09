# Improve funding mechanism using XGBoost and BART LLM

# Deepfunding competition
for full description about the competition please refer to cryptopond platform https://cryptopond.xyz/modelfactory/detail/306250?tab=0

Huggingface : https://huggingface.co/spaces/DeepFunding/PredictiveFundingChallengeforOpenSourceDependencies

## Workflow
(in this repo you just need to run main_huggingface_XGB.ipynb, i stored all csv helper.)

### 1. Data Collection
- Download train and test data from both platform
- Create a list contains all github repo urls (all_github_urls.csv)
- For each url in all_github_urls, use get_metrics.ipynb to get repository metrics.
- Scrape frontend data on each repo link to get closed/open issues, open/closed pull-request, and used by number by running scrape_frontend_github_repo.ipynb.
- Using summarize_readme.ipynb Get readme file on each repo.

### 2. Data preprocessing
- extract repository name
- apply log transformations and ratio for numerical features like stars, watchers, etc.
- convert boolean values to integer
- encode categorical variables 
- using BART to create summarization of repo's readme file
- TF-IDF Vectorization
- feature selection

### 3. Model Training
- train XGBoost model using preprocessed data
- evaluate the model (MSE and R^2)

### 4. Making predictions
- Make final predictions on the test dataset
- create csv submission file
- transitivity check

honorable mention :

@davidgasques (metrics & ratio-ing)
https://github.com/davidgasquez/predictive-funding-challenge

@Faezehshakouri 
https://github.com/FaezehShakouri/deepfunding