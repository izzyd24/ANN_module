# Challenge 19
## Background
With the modules on machine learning and deep neural networks, we are tasked to---
Clean a dataset and create a binary classifier to predict: if applicants will be funded by Alphabet Soup.
## Dataset Information:
The sample csv contains 34,000 organizations that have recieved funding from Alphabet Soup. 
These are the columns: EIN, Name, Application Type, Classification, Use Case, Organization, Status, Income, Special Considerations, Ask, and Successful. 
## D1: Preprocessing 
First, we read in our CSV, and observed our column names: 
![load data](https://user-images.githubusercontent.com/102266450/185200319-f9473908-d91a-4c38-a3ce-5508b32880d5.gif)

We decided the "Is Successful" and the "application type", "affiliation", "classification", "use case", "organization", "status", "income", "special considerations", and "ask amt" columns to be the target and features for our model, respectively. 

We then dropped the "EIN" and "Name" columns, as these identification columns provide no value to our model and are confidential: 
![unique values](https://user-images.githubusercontent.com/102266450/185200371-944a97d2-1f9a-42bd-8605-587dd87b3bff.gif)

We also checked for the number of unique values, with the intention of finding any column with 10+ and made our density plot, see above!

The density plot allows us to understand how the column values are distributed, and then follows the creation of the "other" column for binning:
![density](https://user-images.githubusercontent.com/102266450/185200420-5a54d54d-3c11-4df8-827a-15d2315caa84.gif)

Our model must be in the numeric form to processs, we encode the categorical with "one-hot encoder".
This process leads us to the creation of our new dataframe, and merging with the original: 

Then, we focused on the spliting the preprocessed into features and target arrays, as well as training and testing datasets: 
![binning](https://user-images.githubusercontent.com/102266450/185200595-04c603a1-d3ff-4c0c-9255-9024f8598535.gif)

Finally, we standardized the numerical values with "StandardScaler" to scale our data: 
![scaler](https://user-images.githubusercontent.com/102266450/185200557-d61c963d-29c9-45bb-a768-19ea15369747.gif)

This is a great start, but we are now ready to train the model! 
## D2: Compile, Train, Evaluate 
In this step, we need to design a deep learning model/neural network. We will leverage a binary classification model to predict if a funded firm from the above will be successful based on the features from our dataset. 

We need to balance how many inputs to use before checking on the number of neurons and layers for the model. 

First we create the model by assigning input features and nodes for each layer with "keras":
![create layers](https://user-images.githubusercontent.com/102266450/185200643-daab7398-7e6a-4810-aeb0-acfb6cd3717f.gif)

Then, we create our first hidden layer and an output layer and check on the structure of our model.

Compile and train the model:

Evaluate the model using test data to find the loss and accuracy scores: 
![accuracy](https://user-images.githubusercontent.com/102266450/185200733-c0f62797-14a6-4d86-8218-c242955cdfe7.gif)

Lastly, we save our model's weights after every 5 epochs with a simple "nn.save".

## D3: Optimization
## Initial Model: 
A quick note on where we left off at the tail-end of our analysis in "D2"---
We achieved 72% accuracy, just shy of the 75%+ mark we are aiming for. This is following the combination of 100 epochs run + our split on input vs hidden layers at 80 and 52, respectively. 

## Adjustement One: Increase Epochs
By simply increasing to 300 epochs, we achieved a 72.5% accuracy score. It can be argued that runtime is an issue, and we should consider dropping certain columns, creating more bins, or increasing/decreasing the number of values in each bin. 

## Other Approaches: 
Another approach would be to add more neurons to the hidden layer, add another hidden layer alotogther, or use a different activation function (previously set as relu)

## Adjustement Two: Change activation function from Relu to...
Here, we replaced the "Relu" activation from our hidden layer to the "Tanh" in hopes of increasing the percentage on model accuracy. 

### Tanh Hidden Layer, 500 Epochs Results:
A slightly more aggressive approach, with less concern on runtime:
![tanh 500](https://user-images.githubusercontent.com/102266450/185200865-bed45d29-1b75-4808-aaf9-c180fa1db428.gif)

## Adjustement Three: Add a new hidden layer, Relu
Here, we are reverting back to the "relu" activation model after sub-par results with our Tanh model. Instead, we will try to add another hidden layer: 
![300 epochs](https://user-images.githubusercontent.com/102266450/185200872-969f3f91-ee4c-4fa9-a386-48bbff4f932e.gif)

### Extra Hidden Layer, 300 Epochs Results: 
We were able to reach 72.6%. 

## Last approach (before consulting with TAs/Classmates): 
In this final approach, I will only drop the "EIN", "NAME", and any column that seems out of place.
We are testing for an increase in model accuracy, but may need to look at our dataframe more closely to determine if our inputs are meaningful.

### Results: 
We reached 73.5%. We are content with these results, but plan on coming back to break the 75% threshold.


