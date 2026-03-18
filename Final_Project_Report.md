# Tornado Hook Identification using a CNN - Final Project Report


## Clouds Team
Angel Chui - 2nd year ATMOS grad <br> 
Sofia Vakhutinsky - 2nd year ATMOS grad <br>
Lesly Silva - 4th year ESS undergrad <br> <br>
*Some formatting for this markdown file and the results presented in this report used AI/LLM (e.g. ChatGPT, Claude)*


## Introduction
- Tornadoes are dangerous and pose a large risk to human life and society, therefore exploring methods to improve forecasting is an important task. <br>
**Figure 1:** Annual tornado counts (bars) and associated fatalities (line) in the United States since 1950, highlighting the persistent societal risk posed by severe storms. Data Source: NOAA SPC. <br>
![Tornado History](figures/tornadofatalitycounts.png)
- This final class project for ESS 469/569 aims to explore the use of machine learning, specifically a Convolutional Neural Network (CNN) for identifying tornado hook echoes on radar imagery. 
- Project Question: How can we use machine learning to identify tornado hook echoes in radar imagery?


## Background
- The National Weather Service (NWS) Weather Surveillance Radar-1988 Doppler system (WSR-88D) was launched in 1988 and became the core radar observational system used for forecasting and research in the United States.
- Linear statistical methods and threshold-based algorithms were developed for tornado prediction during the 1980s through 1990s, such as the Mesoscale Detection Algorithm (MDA).
- In the 2000s onwards, machine learning (ML) techniques were developed that used binary classification and CNNs to work with outputs from MDA to create modern day tornado forecasting methods.
- In 2025, a comprehensive dataset of 9 years of observational data from the WSR-88D system was created as part of the TorNet study which used this dataset to train a CNN and compare this with other ML methods (random forests and logistic regression) and traditional forecasting methods (tornado vortex signature) using the same dataset.
    -  Veillette, M. S., Kurdzo, J. M., Stepanian, P. M., Cho, J. Y. N., Reis, T., Samsi, S., McDonald, J., & Chisler, N. (2025). A Benchmark Dataset for Tornado Detection and Prediction Using Full-Resolution Polarimetric Weather Radar Data. Artificial Intelligence for the Earth Systems, 4(1). https://doi.org/10.1175/AIES-D-24-0006.1  
    - TorNet github: https://github.com/mit-ll/tornet


## Inputs/Outputs
### Inputs
- Model inputs include labelled radar image frames from the confirmed tornadoes subset of the original TorNet dataset (6.8% of the total dataset).
- From this subset, we randomly selected cases and labelled each frame with a binary classification of either a frame with a tornado with a hook (1) or a tornado without a hook (0).
- Our final numbers were 1523 of (0) tornadoes without hooks and 228 of (1) tornadoes with hooks
### Outputs
- 
- 


## ML approach
- 
- 


## Results
- 
- 
**Figure N:** Mean ROC Curve
![Mean ROC](figures/mean_ROC.png)


**Figure N:** Mean Confusion Matrix
![Confusion Matrix](figures/mean_confusion_matrix.png)

**Figure N:** Prediction Probability
![PDF](figures/prediction_pdf.png)


## Discussion
- 
- 


## Future Work
- Determine a new method of labelling/identifying tornado hook echoes on radar. This would involve creating a firm definition of a radar hook echo.
- Soliciting expert opinions on what is or is not a hook echo may help with improving training data.








