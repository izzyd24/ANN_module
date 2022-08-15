# Challenge 19
## Background
With the modules on machine learning and deep neural networks, we are tasked to---
Clean a dataset and create a binary classifier to predict: if applicants will be funded by Alphabet Soup.
## Dataset Information:
The sample csv contains 34,000 organizations that have recieved funding from Alphabet Soup. 
These are the columns: EIN, Name, Application Type, Classification, Use Case, Organization, Status, Income, Special Considerations, Ask, and Successful. 
## D1: Preprocessing 
First, we read in our CSV, and observed our column names: 

We decided the "X" and the "Y" columns to be the target and features for our model, respectively. 
We then dropped the "EIN" and "Name" columns, as these identification columns provide no value to our model and are confidential: 

We also checked for the number of unique values, with the intention of finding any column with 10+ and made our density plot: 

The density plot allows us to understand how the column values are distributed, and then follows the creation of the "other" column for binning:

Our model must be in the numeric form to processs, we encode the categorical with "one-hot encoder": 

This process leads us to the creation of our new dataframe, and merging with the original: 

Then, we focused on the spliting the preprocessed into features and target arrays, as well as training and testing datasets: 

Finally, we standardized the numerical values with "StandardScaler" to scale our data: 

This is a great start, but we are now ready to train the model! 
## D2: Compile, Train, Evaluate 

## D3: Optimization


