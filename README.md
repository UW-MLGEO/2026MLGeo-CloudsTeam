## Data information
#### Accessing our data
We have downloaded the data from the tornet github which had a site from which you could download data. We have already downloaded all of it onto Sofia's hardrive. In total it is around 100GB so we are currently uploading it to an amazon server under Sofia's name. The data should finish uploading by the end of the week (02/13). We have tested that everyone in our group can access it through our python notebook.

#### Our project questions as a reminder
1. How do we use supervised machine learning to identify tornado hook echoes in radar imagery? 
Inputs: PPIs of radar reflectivity and radial velocity categorized as containing a hook or not
Outputs: binary classification of tornado hook echoes, of whether a storm event has a hook echo or not

2. Can we use unsupervised machine learning on storms with identified hook echoes to determine pre-existing conditions of tornadoes and predict whether a tornado will occur?
Inputs: PPIs of radar reflectivity and radial velocity from the times before a tornado develops a hook echo (determined from the output of part 1)
Outputs: pre-tornadic conditions, and also binary classification of whether a tornado will occur based on a storms structure.

#### How we are training our data
Our data already comes split into training and testing, and with a tornado category, so we will be able to select the images we need fairly easily. Out of those tornado-labeled images we will take a random subsample out of the 13,000 tornadic events in our data. We will also make sure our classes are balanced to prevent bias, i.e 50 samples with tornadoes with hooks, 50 samples of tornadoes with no hooks, and 50 non-tornadic cells. We will choose about 50 events from each category, and then label each frame within the event into the categories mentioned above. For our classifying model we will randomly subset the frames within our subsample to get the 50 frames we need for each category. This will be the trained dataset for the model. The output of this model will be our input for our unsupervised predictive model. 

#### Resources
None needed.
