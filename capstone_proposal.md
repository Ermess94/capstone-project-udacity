# Machine Learning Engineer Nanodegree
## Capstone Proposal
Matteo Giuliani  
October 10th, 2024

### Domain Background
Starbucks is a renowned global brand specializing in coffee and other beverages.
Starbucks offers a mobile application that enables registered users to order coffee for pickup, pay directly via the app in-store, and earn rewards points. 
Additionally, the app features promotional offers, which can range from simple advertisements about a product to actual deals like discounts or BOGO (buy one, get one free) offers. 
This project aims to customize these promotional offers for each user based on their historical responses to similar offers, identifying those most likely to engage.

### Problem Statement
The primary goal is to identify the most suitable offers for each user, based on their reactions to previously received promotions.
The challenge is that not all users receive the same offers, and this variability must be addressed using a dataset provided by Starbucks, covering customer interactions over a 30-day period. 
I will also develop a machine learning model to predict how customers will respond to these offers.

### Datasets and Inputs
The dataset consists of simulated data that mirrors user behavior on the Starbucks rewards mobile app.
Starbucks sends offers to users of the app every few days, and this data is captured across three JSON files:

- **portfolio.json**: Contains details of offers, including their IDs and metadata (e.g., type, duration).
- **profile.json**: Contains demographic data for each customer.
- **transcript.json**: Contains records of transactions, offers received, offers viewed, and offers completed.

Here is an overview of each file's schema and the variables they include:

#### portfolio.json
- **id** (string): Unique identifier for the offer.
- **offer_type** (string): Type of offer, such as BOGO, discount, or informational.
- **difficulty** (int): Minimum spending required to qualify for the offer.
- **reward** (int): Reward provided for completing the offer.
- **duration** (int): Duration of the offer's validity, measured in days.
- **channels** (list of strings): Channels through which the offer is delivered.

#### profile.json
- **age** (int): Age of the customer.
- **became_member_on** (int): Date when the customer joined the app.
- **gender** (str): Gender of the customer (with 'O' indicating non-binary/other options).
- **id** (str): Unique customer ID.
- **income** (float): Customer's income level.

#### transcript.json
- **event** (str): Description of the activity (e.g., transaction, offer received, offer viewed).
- **person** (str): Customer ID.
- **time** (int): Time elapsed in hours since the start of the test, beginning at t=0.
- **value** (dict): Depending on the record, this may include an offer ID or transaction amount.

The **portfolio.json** file identifies three primary types of offers Starbucks may distribute:
1. **BOGO (Buy-One-Get-One)**: Provides a second, identical product at no extra charge when a specific spending threshold is met.
2. **Informational**: Provides information about a product with no direct reward but encourages purchases if a spending threshold is met.
3. **Discount**: Offers a discount on a product, reducing its original price when certain conditions are met.


### Solution Statement
To determine which offers to send to customers, I will focus on identifying the offers that are most appealing to them. 
Through Exploratory Data Analysis (EDA), I will explore key aspects, including:
1. The most frequently accepted offers.
2. Customer responses to different offers.
3. Analysis of age and gender groups that show the highest interest in offers.

These analyses will be conducted at both a general population level and an individualized level. 
For predicting how a customer might respond to an offer, I plan to use models such as RandomForestClassifier and DecisionTreeClassifier, assessing which model best captures the patterns in the data.

### Benchmark Model
For a quick and effective benchmark, I will use the KNeighborsClassifier. 
This method is commonly used for binary classification problems due to its simplicity and speed. 
The model’s performance will be evaluated using the F1 score as the primary metric.

### Evaluation Metrics
The F1 score will be used as the evaluation metric for this project, providing a balance between precision and recall. 
This metric is particularly useful for determining how well the model handles both false positives and false negatives.
The F1 score ranges from 0 to 1, where a score of 1 represents perfect precision and recall, while 0 indicates the poorest performance.

### Project Design
The overall approach for this project will follow these steps:
1. Set up the working environment using Jupyter.
2. Clean and preprocess the data to prepare it for modeling.
3. Perform detailed exploratory analysis to understand the data.
4. Build and compare various models to identify the best fit for the data.
5. Apply the benchmark model and evaluate results using the chosen metric.
6. Compile findings and insights into a comprehensive blog post.
