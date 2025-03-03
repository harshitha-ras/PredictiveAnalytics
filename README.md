# Dental Imaging Device Prediction Model
### Overview
This project develops a predictive model for dental imaging devices, focusing on failure prediction and service ticket analysis. The model uses historical data to forecast device failures and estimate the likelihood of multiple service tickets within a 90-day period.

### Data Analysis Approach
1. Data Preparation:

    - Load and clean the dataset
    
    - Convert date strings to datetime objects
    
    - Create additional features like ticket_month and ticket_year
    
    - Extract device model information from device_alias

2. Device Failure Analysis:

    - Define failure categories based on specific issue types
    
    - Group data by device to analyze failure history
    
    - Calculate failure rates for each device

3. Time-to-Failure Prediction:

    - Implement survival analysis using Cox Proportional Hazards model
    
    - Use device characteristics and failure history as predictors
    
    - Estimate hazard ratios and predicted time to failure for each device

4. Multiple Ticket Prediction:

    - Create a binary target variable for devices with multiple tickets in a month
    
    - Aggregate device features and category information
    
    - Train a Random Forest Classifier to predict multiple ticket likelihood

### Models Used
1. Cox Proportional Hazards Model (Survival Analysis):

    This model was particularly useful for predicting time to failure and assessing risk factors:
    
      - Failure prediction: The model identified devices at high risk of failure, with some showing up to 100% predicted risk.
    
      - Time to failure estimation: For high-risk devices, the model predicted a time to failure of 0 days, indicating imminent or already occurred failures.
    
      - Risk factors: The model likely identified which device characteristics and usage patterns contribute most to failure risk, though specific details weren't provided in the results.

2. Random Forest Classifier:

    This model was effective in predicting the likelihood of multiple service tickets:
    
      - Multiple ticket prediction: The model identified devices with a 100% probability of generating multiple tickets in the next 90 days.
    
      - Device age correlation: Older devices (e.g., OMEGA PRISM 3D 11X10 and VORTEX NEXUS 3D) were more likely to generate multiple tickets.
    
      - Model-specific issues: The TRIDENT SPECTRA VISION model appeared in both high failure risk and multiple ticket probability lists, suggesting potential design or manufacturing issues.

### Why These Models?
    - Survival Analysis: Ideal for predicting time-to-failure, accounting for devices that haven't failed yet (censored data)
    
    - Random Forest: Effective for classification tasks with multiple features, resistant to overfitting

Key Features Used
    - Device age
    
    - Ticket count
    
    - Device model
    
    - Category levels (1, 2, 3, 4)
    
    - Record type
    
    - Out-of-box status

### Results
    1. Age-related patterns: While older devices were more prone to multiple service tickets, age wasn't always a determinant of immediate failure risk.
    
    2. Model-specific issues: Certain models, like TRIDENT SPECTRA VISION, showed higher vulnerability to both failures and frequent service needs.


### Insights
    1. Maintenance prioritization: The results allow for targeted preventive maintenance on high-risk devices.
    
    2. Resource allocation: Support resources can be more effectively allocated based on predicted service needs.
    
    3. Design implications: Insights into model-specific issues can inform future design improvements.
    
    These models provided actionable insights for proactive maintenance, resource planning, and potential design enhancements in dental imaging devices.

### Future Improvements
    - Incorporate more detailed device usage data
    
    - Explore deep learning models for time series prediction
    
    - Implement regular model retraining to adapt to changing patterns
