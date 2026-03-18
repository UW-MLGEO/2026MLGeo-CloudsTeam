# Tornado Hook Identification using a CNN - Final Project Report




## Clouds Team
Angel Chui - 2nd year ATMOS grad <br> 
Sofia Vakhutinsky - 2nd year ATMOS grad <br>
Lesly Silva - 4th year ESS undergrad <br> <br>
*Some formatting for this markdown file used AI/LLM (e.g. ChatGPT, Claude)*




## Introduction
- Tornadoes are dangerous and pose a large risk to human life and society, therefore exploring methods to improve forecasting is an important task. <br>
**Figure 1:** Annual tornado counts (bars) and associated fatalities (line) in the United States since 1950, highlighting the persistent societal risk posed by severe storms. Data Source: NOAA SPC. <br>
![Tornado History](figures/Tornado_stats.png)
- One way scientists identify tornadoes on radar is by looking for hook echoes, which are hook, bean, or pendant-like shapes visible on radar that occur when rain or hail is wrapping around a rotating storm. 
- This final class project for ESS 469/569 aims to explore the use of machine learning, specifically a Convolutional Neural Network (CNN), for identifying tornado hook echoes on radar imagery. 
- Project Question: How can we use machine learning to identify tornado hook echoes in radar imagery? <br>
**Figure 2:** Examples of radar imagery showing different types of hook echoes with the left image showing a classic defined hook shape while the image on the right shows a more pendant or appendage-shaped hook.<br>
![Hook Echo Example1](figures/hookex1.png)
![Hook Echo Example2](figures/hookex2.png)


## Background
- The National Weather Service (NWS) Weather Surveillance Radar-1988 Doppler system (WSR-88D) was launched in 1988 and became the core radar observational system used for forecasting and research in the United States.
- Linear statistical methods and threshold-based algorithms were developed for tornado prediction during the 1980s through 1990s, such as the Mesoscale Detection Algorithm (MDA).
- In the 2000s onwards, machine learning (ML) techniques were developed that used binary classification and CNNs to work with outputs from MDA to create modern day tornado forecasting methods.
- In 2025, a comprehensive dataset of 9 years of observational data from the WSR-88D system was created as part of the TorNet study, which used this dataset to train a CNN and compare this with other ML methods (random forests and logistic regression) and traditional forecasting methods (tornado vortex signature) using the same dataset.
    -  Veillette, M. S., Kurdzo, J. M., Stepanian, P. M., Cho, J. Y. N., Reis, T., Samsi, S., McDonald, J., & Chisler, N. (2025). A Benchmark Dataset for Tornado Detection and Prediction Using Full-Resolution Polarimetric Weather Radar Data. Artificial Intelligence for the Earth Systems, 4(1). https://doi.org/10.1175/AIES-D-24-0006.1  
    - TorNet github: https://github.com/mit-ll/tornet




## Inputs/Outputs
### Inputs
- The TorNet dataset includes over 200,000 samples of storm events, each with the storm centered on a radar ‘chip’ or subsection of a Plan Position Indicator (PPI) radar scan. In each event, there were also 4 time frames, at 2 sweeps, or angles above ground that the radar was scanning at. 
- These radar images were stored as NetCDF files with 4 dimensions: time, azimuth, range, and sweep. There were six radar variables recorded; however, we chose to use only two of these for our model to reduce dimensionality: Reflectivity (DBZ) and Radial Velocity (VEL), which are the most useful for identifying hook echoes.
- The storm events from the TorNet data set were also subset into three categories: confirmed tornado [TOR] (6.8%), a tornado warning occurred but no tornado formed [WRN] (31.8%), and non-tornadic storm cells [NUL] (61.4%).
- In addition, each frame has a binary label of tornadic or non-tornadic.
- For our model, we trained a subset of this TorNet dataset, abo
- Because we were using supervised learning and could not label the entire 
- Model inputs include labelled radar image frames from the confirmed tornadoes subset of the original TorNet dataset (6.8% of the total dataset).
- From this subset, we randomly selected cases and labelled each frame with a binary classification of either a frame with a tornado with a hook (1) or a tornado without a hook (0).
- Our final numbers for the training data input were 1523 of tornadoes without hooks (0) and 228 of tornadoes with hooks (1) or 12.6% of the input data had hooks and 87.4% did not have hooks.
**Figure 3:** Shows examples of what a tornado without hook and tornado with hook looks like. <br>
Below is a radar image showing a tornado with a hook.
![torhook example](figures/torhookexample.png) <br>
Below is a radar image showing a tornado without a hook.
![tornohook example](figures/tornohookexample.png)




### Outputs
- Labelled radar images as tornado with hook or tornado without hook.
- For model evaluation, we checked whether the outputs were true/false positives and true/false negatives.




## ML approach
- The model used for this project can be found in this repository in the notebook: torhook_model.ipynb
- Our model is based on the baseline CNN used in the TorNet study from 2025. This model uses Keras 3.0 and Tensorflow to create the model architecture and do the calculations.
- The TorNet CNN uses inputs from the TorNet dataset and the output is a heatmap that shows the probability of when and where a tornado will occur.
- We originally chose this model because we had a second goal of using the outputs from our current model to forecast tornados so we chose an existing model that had similar outputs.
- We used their model for transfer learning by freezing all convolutional layers in their model except for the last 15 layers and removing their output layers. Figure 4 below depicts how we changed the TorNet architecture for transfer learning and our new output hyperparameters.
**Figure 4:** Shows the TorNet CNN architecture (top) and our CNN architecture (bottom) and how we performed the transfer learning. <br>
![model architecture](figures/torhook_architecture.png)
- Additional details about our model hyperparameters are listed below:
    - Output layers:
        - Global Average Pooling (2D) - compresses each feature map into a single number by averaging 
        - ReLu Activation function - introduces non-linearity, which we need for curved hook features in radar
        - Batch Normalization - normalizes the global average pooling and ReLu, helping model/data stabilize
        - Dropout (50%) - randomly disables half the neurons during each training batch to prevent overfitting
        - Softmax Activation Function - converts the final two neuron outputs into probabilities that sum to 1
    - Learning/Training Hyperparameters used in the last 15 unfrozen layers
        - Optimizer: Adam, adjusted learning rate: 3e-5
        - Loss: sparse categorical cross entropy - penalizes confident wrong predictions
        - Early stopping based on validation loss - usually around 15 epochs




## Results
- 
- 
**Figure 5:** Mean ROC Curve
![Mean ROC](figures/mean_ROC.png)




**Figure 6:** Mean Confusion Matrix
![Confusion Matrix](figures/mean_confusion_matrix.png)


**Figure 7:** Prediction Probability
![PDF](figures/prediction_pdf.png)




## Discussion
- 
- 




## Future Work
- Determine a new method of labelling/identifying tornado hook echoes on radar. This would involve creating a firm definition of a radar hook echo.
- Soliciting expert opinions on what is or is not a hook echo may help with improving training data.




















