## How to navigate our repository

Our final project report and summary is saved as Final_Project_Report.md. It should have all the information you need about our project.

We have two folders, code_notebooks and figures. The figures one is there so that all the images in our markdown file display. 

Here is a rundown of each notebook and it's purpose in our code_notebooks folder:
- accessing_tornet_data.ipynb
    - This notebook was primarily used to set everyone in our group with access to the aws server that housed our data. Since this server was private and will be discontinued going forward, data will only be available for downnload on the tornet github: https://github.com/mit-ll/tornet
- radar_labeler.ipynb
    - This is the notebook we used to train our data. It selects random subsets from the TorNet data and displays each frame one by one, allowing the user to click buttons on the widget to save the frame filepath in a csv file for later use by the model.
- torhook_model.ipynb
    - This is the notebook that actually runs our model. For specifics about our model, please refer to our Final Project markdown file.
- model_metric_plots.ipynb
    - This notebook creates the plots for validating our model and analysis on it's performance. 


### Below is the Read_Me file we were asked to make early on in the project. We left it in just in case it was needed to grade our assignment, but it does contain dated information.


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
None needed for processing the training/input dataset. Further discussion on potentially needing resources from Akshay at choosing ML/running ML stage.