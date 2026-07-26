# PRCP-1005: Forest Cover Type Prediction

## 📖 Project Overview
The primary goal of this project is to predict seven different forest cover types across four distinct wilderness areas in the Roosevelt National Forest of Northern Colorado with the best possible accuracy[cite: 6]. These specific study areas represent forests with minimal human-caused disturbances, ensuring that the existing cover types are the result of natural ecological processes rather than forest management practices[cite: 6].

## 🎯 Problem Statement & Tasks
This project is structured around the following core tasks, all of which are executed within a single Jupyter Notebook for final submission[cite: 6]:
*   **Task 1:** Prepare a complete data analysis report on the given dataset[cite: 6].
*   **Task 2:** Create a predictive model capable of multi-class classification to identify the forest cover types[cite: 6].
*   **Task 3:** Formulate a Model Comparison Report to evaluate the performance of multiple models and suggest the best one for production[cite: 6].
*   **Task 4:** Create a report detailing the challenges faced while handling the data and the specific techniques used to overcome them, complete with reasoning[cite: 6].

## 📂 Dataset Information
*   **Dataset Link:** [PRCP-1005-ForestCoverPred.zip](https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1005-ForestCoverPred.zip)[cite: 6].
*   **Data Integrity:** The dataset contains 15,120 rows and 56 columns[cite: 5]. It is clean, containing zero missing values and zero duplicate records[cite: 5].
*   **Target Variable:** `Cover_Type` (integers 1 to 7)[cite: 6]. The training data is perfectly balanced, with exactly 2,160 instances for each of the 7 cover types[cite: 5].
*   **Data Structure:** The data represents 30 x 30 meter cells and is provided in raw, unscaled form[cite: 6]. 

### Key Features
Independent variables were derived from the US Geological Survey and USFS data[cite: 6]:
*   **Geographical Metrics:** Elevation (meters), Aspect (degrees azimuth), and Slope (degrees)[cite: 6].
*   **Distance Metrics:** Horizontal/Vertical distance to nearest surface water (Hydrology), horizontal distance to Roadways, and horizontal distance to wildfire ignition points (Fire Points)[cite: 6].
*   **Sunlight Metrics:** Hillshade indices (0 to 255) at 9am, Noon, and 3pm during the summer solstice[cite: 6].
*   **Categorical Variables (One-Hot Encoded):** 
    *   `Wilderness_Area`: 4 binary columns representing areas like Rawah, Neota, Comanche Peak, and Cache la Poudre[cite: 6].
    *   `Soil_Type`: 40 binary columns representing specific soil family designations[cite: 6].

## 🛠️ Machine Learning Workflow

### 1. Exploratory Data Analysis (EDA)
*   Visualized the distribution of the target variable to confirm class balance[cite: 5].
*   Analyzed relationships between geographical features (like `Elevation` and `Slope`) and the different forest cover types, revealing that these metrics are important predictive features[cite: 5].
*   Examined how sunlight exposure (Hillshade) and water proximity influence vegetation patterns across classes[cite: 5].

### 2. Feature Engineering
To improve model learning and capture combined geographical effects, the following derived features were engineered[cite: 5]:
*   **`Hydrology_Distance`:** The combined horizontal and vertical distance to water sources calculated using the Pythagorean theorem[cite: 5].
*   **`Road_Fire_Distance_Diff`:** The absolute difference between the distance to roadways and fire points[cite: 5].
*   **`Mean_Hillshade`:** The average sunlight/shade exposure across the three measured times of day[cite: 5].
*   **`Hillshade_Range`:** The variation (max minus min) in hillshade throughout the day[cite: 5].

### 3. Predictive Modeling & Algorithm Selection
*   Multiple multi-class classification algorithms were implemented to compare different learning approaches, including linear models, tree-based models, ensemble methods, and boosting techniques[cite: 5].
*   **Best Performers:** Tree-based ensemble and boosting algorithms yielded the best performance[cite: 5]. These algorithms were selected because they effectively capture the complex, non-linear relationships between the environmental features and the target forest cover classes[cite: 5].
