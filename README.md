Seasonal Agriculture Performance Analysis
VOIS AICTE Major Project --- Batch 2026--2027
Prepared by: Amrit Kumar
1. About the Project
This project analyses farm-level agricultural data to understand
how farming performance varies across India's three major cropping
seasons:
Kharif
Rabi
Zaid
The main purpose of the project is simple: the dataset has a lot
of farm records, but it does not have immediate insight into what is
happening. I have applied data analysis and machine learning to turn
those numbers into insights around weather, soil, farming inputs, yield
and water, revenue and cost, and profit.
The analysis is exploratory. It is meant to identify relevant patterns and
relationships from the provided data, not to suggest that one factor
directly causes another.
---
2. What I Am Trying to Research
The project addresses the following questions:
How different are rainfall, temperature, humidity and soil
conditions across Kharif, Rabi and Zaid?
Do fertilizer, pesticide and irrigation patterns change with the
season?
Does agricultural yield differ between seasons?
How do cost, revenue and profit change across seasons?
How common are loss-making farms in each season?
Is poor seasonal performance consistent across different states?
Which crops are financially stronger or weaker?
Which factors are most closely associated with farm profitability?
How efficient are different irrigation methods in terms of profit
generated per unit of water?
Does season have a statistically meaningful relationship with yield
and profit?
---
3. Project Objectives
The main objectives are:
Compare environmental conditions across the three cropping seasons.
Understand seasonal differences in farm resource usage.
Analyse yield and production performance.
Compare total cost, revenue and profit.
Identify seasons and crops with higher financial risk.
Study state-wise seasonal performance.
Measure water-use efficiency.
Use statistical tests to validate relevant patterns.
Use a Random Forest model to identify the strongest predictive
drivers of profit.
Present the findings in a manner supportive of better agricultural
planning.
---
4. Dataset
The analysis uses the provided file:
``` text
seasonal_agriculture_performance_dataset.csv
```
The dataset contains:
4,000 farm records
28 variables
3 cropping seasons
Multiple states, crop types and irrigation methods
Important groups of variables include:
Environmental variables
Rainfall
Average temperature
Humidity
Sunlight hours
Soil pH
Soil moisture
Farm and input variables
Farm area
Nitrogen
Phosphorus
Potassium
Fertilizer
Pesticide
Seed quality
Irrigation method
Water used
Agricultural performance variables
Crop
Yield
Disease/pest risk
Economic variables
Total cost
Revenue
Profit
The CSV dataset is referenced by the notebook but not embedded inside
the notebook itself. Place the CSV in the project directory before
running the analysis.
---
5. Tools and Technologies
The project was developed in Python.
---
Tool / Library           Purpose
---
Python               Main analysis environment
Pandas               Data loading, cleaning, grouping
and analysis
NumPy                Numerical calculations
Matplotlib             Data visualisation
Seaborn               Charts, heatmaps and statistical
visuals
SciPy                ANOVA and Kruskal--Wallis tests
Scikit-learn            Random Forest regression and
feature importance
Jupyter Notebook / Google Colab   Running and presenting the analysis
Analysis workflow
``` text
CSV Dataset
↓
Load Data
↓
Data Quality Check
↓
Cleaning & Missing Values
↓
Exploratory Data Analysis
↓
Seasonal Comparison
↓
Yield & Economic Analysis
↓
Water Efficiency Analysis
↓
State & Crop Analysis
↓
Statistical Testing
↓
Random Forest Feature Importance
↓
Findings & Recommendations
```
---
6. Data Cleaning
Before analysing the data, I checked the dataset for missing values and
duplicate records.
The main missing values were found in:
`Rainfall_mm` --- 48 values
`Soil_Moisture_pct` --- 40 values
`Yield_Tonnes_Ha` --- 32 values
There were no duplicate rows.
Instead of filling every missing value with one overall average, I used
group-specific medians:
Rainfall → median within the same Season
Soil moisture → median within the same Season
Yield → median within the same Crop
This maintains the natural differences between seasons and crops not
being flattened by one global average.
Outliers
I also carefully checked extreme yield values. High yields are not
always errors. Some crops, particularly Sugarcane, naturally have much
larger yields than crops such as Pulses. For that reason, extreme values
were not blindly removed from the complete dataset.
---
7. Exploratory Analysis
The notebook compares the three seasons from various perspectives.
Seasonal distribution
The dataset contains:
Kharif: 1,779 records
Rabi: 1,627 records
Zaid: 594 records
Environmental conditions
The analysis reveals a clear seasonal pattern:
Kharif has the highest rainfall and soil moisture.
Rabi is cooler and has more sunlight.
Zaid is the hottest and driest season.
This provides a good backdrop for understanding how yield, water
use and profitability can vary across seasons.
Irrigation
Flood irrigation is the most widespread irrigation method in the dataset.
The overall irrigation mix only changes slightly between seasons, which
makes irrigation efficiency an interesting point to investigate.
---
8. Yield and Economic Analysis
Average yield by season:
Season   Average Yield
---
Kharif     5.63 t/ha
Rabi      5.10 t/ha
Zaid      4.64 t/ha
Average profit by season:
Season   Average Profit
---
Kharif      ₹178.9k
Rabi        ₹87.7k
Zaid       -₹24.8k
One of the strongest observations is the increase in loss-making farms:
Kharif: 42.2%
Rabi: 51.1%
Zaid: 64.5%
So, in this dataset, financial performance is becoming weaker from Kharif to
Zaid.
However, season alone is not always explanatory. Crop choice has a
big impact on yield and profit, so I also analysed crop-level
performance.
---
9. Water Efficiency
I compared irrigation methods using yield, water consumption and average
profit.
Irrigation Method   Avg. Profit  Avg. Water Used  Profit / Water
---
Drip           ₹219,626    5,918.75 m³    ₹37.11/m³
Rainfed          ₹79,050    3,549.55 m³    ₹22.27/m³
Sprinkler         ₹91,121    6,208.26 m³    ₹14.68/m³
Flood           ₹73,354    8,026.47 m³     ₹9.14/m³
The biggest difference is on profit per unit of water. Drip irrigation
has the highest value in this dataset, while flood irrigation uses the
most water and has the lowest profit-per-water result.
This is an association in the dataset, so it should not be interpreted
as proof that irrigation method alone causes higher profit.
---
10. State-Level Analysis
I compared average profit across states and seasons to check whether the
seasonal pattern was only a national-level effect.
The analysis covers eight states:
Andhra Pradesh
Gujarat
Karnataka
Madhya Pradesh
Maharashtra
Punjab
Tamil Nadu
Telangana
A notable pattern is that Zaid is the lowest-profit season in every
state represented in the dataset.
Kharif leads in most of the states, while Punjab is an important case where
Rabi performs better. Maharashtra also shows strong Rabi performance
compared to its other seasonal results.
This indicates that seasonal recommendations should consider regional
conditions rather than relying on only one overall average.
---
11. Statistical Testing
I used statistical tests to check whether the seasonal differences seen
in the charts were supported by statistical evidence.
Yield
Two tests were used:
One-way ANOVA
``` text
F = 1.44
p = 0.2369
```
The ANOVA result is not statistically significant at the usual 0.05
level.
Kruskal--Wallis
``` text
H = 68.84
p < 0.001
```
The Kruskal--Wallis test is statistically significant.
Why are the results different?
The yield distribution is strongly skewed because crops such as
Sugarcane have much larger yields than several other crops.
ANOVA compares group means and can be sensitive to this type of
distribution. Kruskal--Wallis compares ranks and provides a helpful
secondary check when the data is not well behaved for a mean-based
comparison.
I therefore do not consider one chart or one statistical test as the
complete answer.
The profit analysis also shows a statistically significant seasonal
difference using ANOVA.
---
12. Crop Profitability
The crop-level analysis reveals large differences between crops.
Crop     Average Profit  Loss-Making Farms
---
Sugarcane      ₹817,188       11.48%
Chilli       ₹750,878       17.96%
Cotton       ₹124,547       34.65%
Groundnut      ₹44,858       40.80%
Pulses        -₹4,238       49.19%
Maize        -₹83,978       63.70%
Rice        -₹102,214       66.38%
Wheat       -₹123,398       74.10%
Sugarcane and Chilli are the strongest performers in the available data,
while Wheat and Rice show the highest average losses.
This is one reason I avoid making the conclusion only about seasons. The
crop being grown is a big part of the financial picture.
---
13. Random Forest Profitability Analysis
To explore which variables are most useful for predicting profit, I
constructed a Random Forest Regressor.
The model uses environmental, farm, crop, season, irrigation and input
variables.
I avoided applying direct accounting variables such as
`Total_Cost_INR` and `Revenue_INR` as predictors. Including them would
cause the model to learn the accounting relationship behind profit rather
than helping identify useful operational drivers.
Top feature groups
Driver     Relative Importance
---
Crop            39.45%
Soil pH           22.60%
Farm Area          11.51%
Water Used          5.91%
Rainfall           5.23%
The model suggests that crop choice, soil pH and farm area are the
strongest predictive factors among the variables included.
Important limitation: Random Forest feature importance shows predictive
association. It does not prove that changing a variable will
directly cause profit to increase.
---
14. Main Findings
The analysis provides several practical observations:
Kharif has the strongest average economic performance in this
dataset.
Zaid has the weakest average profit and the highest share of
loss-making farms.
Environmental conditions change substantially across seasons,
particularly rainfall, temperature and soil moisture.
Flood irrigation is common, but it has the lowest
profit-per-water result among the compared methods.
Drip irrigation has the highest profit per cubic metre of water
in the dataset.
Crop choice is a major factor in profitability.
Sugarcane and Chilli perform strongly, while Wheat and Rice have
much higher average losses.
Zaid is the lowest-profit season in all eight states represented
in the analysis.
Statistical testing has different results for seasonal yield depending
on the test used, highlighting the effect of skewed
crop-level yield distributions.
The Random Forest analysis also points strongly towards crop choice,
soil pH and farm area.
---
15. What the Research Suggests
Based on the dataset, I would focus future agricultural planning on:
Comparing crops within each season rather than relying only
on season-level averages.
Giving priority to water efficiency, particularly where
irrigation demand is high.
Studying soil pH and soil health alongside crop selection.
Treat Zaid as a higher-risk period in the analysed dataset.
Reviewing state-level differences before making a broad
recommendation.
Using economic measures such as profit and loss rate along with
yield.
These are data-driven observations from the project, not universal
recommendations for every farm.
---
16. Future Scope
The current notebook can be expanded into a more practical
decision-support system.
1. Season-aware crop recommendation
Create a recommendation system using:
Season
Soil condition
Water availability
Crop history
Expected economics
2. Interactive dashboard
Create a dashboard with filters for:
State
Crop
Season
Irrigation method
This makes the analysis easier for a non-technical user to explore.
3. Forecasting and scenario analysis
Add weather and market-price scenarios to estimate possible outcomes
before planting.
4. Field validation
Compare the model's findings with real farm outcomes before using the
system for operational decisions.
---
17. Project Structure
A suggested repository structure is:
``` text
Seasonal-Agriculture-Performance-Analysis/
│
├── Seasonal_Agriculture_Performance_Analysis_(2).ipynb
├── seasonal_agriculture_performance_dataset.csv
├── README.md
│
├── visuals/
│  ├── season_counts.png
│  ├── environment.png
│  ├── irrigation_share.png
│  ├── season_performance.png
│  ├── state_heatmap.png
│  ├── drivers.png
│  ├── crop_profit.png
│  └── water_efficiency.png
│
└── presentation/
└── Seasonal_Agriculture_Performance_Analysis_VOIS_Major_Project.pptx
```
The exact file names can be changed based on the final GitHub
repository.
---
18. How to Run the Project
Step 1 --- Clone the repository
``` bash
git clone https://github.com/AswiniKumar55/-Seasonal-Agriculture-Performance-Analysis-.git
cd -Seasonal-Agriculture-Performance-Analysis-
```
Step 2 --- Install the required libraries
``` bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn jupyter
```
Step 3 --- Keep the dataset in the project folder
The notebook expects:
``` text
seasonal_agriculture_performance_dataset.csv
```
If the file has a different name or location, update the `DATA_PATH`
variable in the notebook.
Step 4 --- Open the notebook
``` bash
jupyter notebook
```
Then open:
``` text
Seasonal_Agriculture_Performance_Analysis_(2).ipynb
```
Run the cells from top to bottom.
---
19. Project Outputs
The notebook provides analysis and visualisations covering:
Data quality
Seasonal distribution
Environmental conditions
Irrigation usage
Yield comparison
Economic performance
Correlation analysis
State-level profit comparison
Statistical testing
Crop profitability
Water efficiency
Random Forest feature importance
The PowerPoint presentation summarises the same analysis in a
presentation-friendly format.
---
20. Limitations
This project has some important limitations:
The analysis is based only on the provided dataset.
The dataset does not by itself prove causal relationships.
Seasonal averages can hide differences between individual crops and
states.
Random Forest feature importance is predictive, not causal.
Real-world crop recommendations would need field-level validation.
Market prices, weather forecasts and other external factors could
change the final economic outcome.
---
21. Conclusion
This project began with a simple question: does agricultural
performance change meaningfully from one cropping season to another and
what factors are associated with that change?
The analysis reveals that seasonal conditions are closely associated with
differences in yield and economics in the available data. Kharif
perform best on average, while Zaid shows the highest financial risk.
At the same time, crop choice, soil pH, farm size and water use also
play important roles.
The main takeaway is that agricultural planning should not be based only on
season. A better option is to consider season + crop + soil +
water + economics together.
The next step would be to transform this analysis into an interactive
decision-support dashboard and validate the findings with real farm
data.
---
22. Repository
GitHub:
https://github.com/AswiniKumar55/-Seasonal-Agriculture-Performance-Analysis-
---
23. Author
Amrit Kumar
VOIS AICTE Major Project --- Batch 2026--2027
---
License
This project is created for academic/project analysis purposes. Add an
appropriate open-source license if the repository is intended for public
reuse.
