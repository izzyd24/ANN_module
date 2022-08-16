# Challenge 19
## Background
With the modules on machine learning and deep neural networks, we are tasked to---
Clean a dataset and create a binary classifier to predict: if applicants will be funded by Alphabet Soup.
## Dataset Information:
The sample csv contains 34,000 organizations that have recieved funding from Alphabet Soup. 
These are the columns: EIN, Name, Application Type, Classification, Use Case, Organization, Status, Income, Special Considerations, Ask, and Successful. 
## D1: Preprocessing 
First, we read in our CSV, and observed our column names: 

We decided the "Is Successful" and the "application type", "affiliation", "classification", "use case", "organization", "status", "income", "special considerations", and "ask amt" columns to be the target and features for our model, respectively. 

We then dropped the "EIN" and "Name" columns, as these identification columns provide no value to our model and are confidential: 

We also checked for the number of unique values, with the intention of finding any column with 10+ and made our density plot: 

The density plot allows us to understand how the column values are distributed, and then follows the creation of the "other" column for binning:

Our model must be in the numeric form to processs, we encode the categorical with "one-hot encoder": 

This process leads us to the creation of our new dataframe, and merging with the original: 

Then, we focused on the spliting the preprocessed into features and target arrays, as well as training and testing datasets: 

Finally, we standardized the numerical values with "StandardScaler" to scale our data: 

This is a great start, but we are now ready to train the model! 
## D2: Compile, Train, Evaluate 
In this step, we need to design a deep learning model/neural network. We will leverage a binary classification model to predict if a funded firm from the above will be successful based on the features from our dataset. 

We need to balance how many inputs to use before checking on the number of neurons and layers for the model. 

First we create the model by assigning input features and nodes for each layer with "keras":

Then, we create our first hidden layer:

We create an output layer and check on the structure of our model:

Compile and train the model:

Evaluate the model using test data to find the loss and accuracy scores: 

Lastly, we save our model's weights after every 5 epochs with a simple "nn.save"

## D3: Optimization


