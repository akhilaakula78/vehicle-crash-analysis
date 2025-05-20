# Crash Severity and Clearance Time Prediction – Texas (2024–2025)

## Project Overview

This project focuses on improving traffic safety and response efficiency by predicting two critical outcomes related to road crashes:

- The likely **severity of a crash** at the time of or immediately after its occurrence
- The estimated **time required to clear** the crash from the roadway

Using over **2.4 million crash records** from the **Texas Department of Transportation (TxDOT)**, the objective is to build models that help inform and support emergency responders, traffic operators, and public safety agencies during high-pressure situations.

By predicting severity and clearance duration, this work aims to reduce delays, improve resource allocation, and enhance situational awareness during crash events.

---

## Research Objectives

### Research Question 1: Crash Severity Classification

Can we predict the severity level of a crash based on available data such as:

- Vehicle damage area and vehicle type  
- Driver behavior and test results  
- Time of day, day of week, and location characteristics  
- Weather, road conditions, and crash geometry  

The severity is categorized into three levels:

- `0` - Minor or No Injury  
- `1` - Moderate Injury  
- `2` - Severe or Fatal Injury

### Research Question 2: Clearance Duration Prediction

Can we estimate the amount of time it takes to clear a crash scene based on information such as:

- Time and location of the crash  
- Roadway and environmental conditions  
- Vehicle involvement and proximity to trauma care facilities  
- Crash type and contributing factors

---

## Methodology

The data was cleaned, processed, and scaled using `MinMaxScaler`. Boolean features were encoded, and categorical variables were one-hot encoded. Models were evaluated using a holdout validation set and tested using randomized hyperparameter tuning. For classification tasks, class imbalance was addressed using **SMOTE (Synthetic Minority Over-sampling Technique)**.

### Models Used

- **Classification (Crash Severity):**
  - Logistic Regression
  - Decision Tree
  - Random Forest
  - XGBoost

- **Regression (Clearance Duration):**
  - Linear Regression
  - Decision Tree Regressor
  - Random Forest Regressor
  - XGBoost Regressor

---

## Results Summary

| Task                          | Best Model              | Performance     | Top Influential Features                                    |
|------------------------------|-------------------------|------------------|--------------------------------------------------------------|
| Crash Severity Classification | XGBoost Classifier      | Accuracy: 84.2%  | Driver alcohol result, vehicle damage severity, crash timing |
| Clearance Time Prediction     | Random Forest Regressor | R² ≈ 0.28        | Crash hour, trauma center distance, intersection status      |

---

## Key Feature Insights

### Crash Severity Classification – What Drives It?

The model identified several features that strongly influence the likelihood of a crash resulting in minor, moderate, or severe injury. The top five most important features are:

1. **Driver Alcohol Result**  
   Indicates whether the driver tested positive for alcohol. Alcohol impairment consistently increases the risk of high-severity crashes.

2. **Vehicle Damage Rating 1 - Severity**  
   Reflects how much physical damage the vehicle sustained. Higher damage severity often correlates with more serious injury outcomes.

3. **Vehicle Age**  
   Older vehicles may lack modern safety features like airbags or automatic braking, making occupants more vulnerable in collisions.

4. **Crash Hour**  
   The time of day when the crash occurred. Late-night and early-morning crashes often involve higher speeds and impaired driving.

5. **Driver Impairment**  
   Captures whether the driver was physically or mentally impaired (e.g., fatigue, drug use, distraction), which increases crash severity risk.

---

### Clearance Duration Prediction – What Delays Response?

The regression model highlighted the following five most important factors when estimating how long it takes to clear a crash scene:

1. **Crash Hour**  
   Certain times—such as rush hour or nighttime—are associated with longer clearance times due to traffic volume or resource availability.

2. **Nearest Trauma Center Distance**  
   Crashes occurring far from trauma centers may require more coordination and extended medical attention, increasing clearance time.

3. **At Intersection Flag**  
   Crashes at intersections tend to involve multiple vehicles or infrastructure (signals, turn lanes), making cleanup and investigation slower.

4. **Driver Alcohol Result**  
   Alcohol-related crashes may require law enforcement investigation and documentation, delaying the clearing of the scene.

5. **Speed Limit**  
   High-speed zones often result in more complex crashes involving severe damage, longer response, and cleanup efforts.

---

## Real-World Application: Severity Tagging System

This project lays the foundation for a **real-time crash severity tagging system**, which can be used to assist dispatchers, emergency medical services, and smart transportation systems.

### What is Severity Tagging?

When a crash report is submitted via 911 call, highway sensors, or telematics, the system can:

- **Assign a severity level (0–2)** immediately
- **Predict estimated clearance time**
- **Prioritize EMS and police response**
- **Notify hospitals or reroute traffic in real-time**

### Potential Use Cases

- **Traffic Operations**: Real-time crash predictions integrated into highway control systems  
- **EMS Optimization**: Deploy emergency resources faster based on predicted injury severity  
- **Urban Planning**: Use severity predictions to identify high-risk zones  
- **Connected Vehicles**: Embedded predictions in in-vehicle or fleet systems  

---

## Project Structure
