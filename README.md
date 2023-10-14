# Data-Preparation-Project---NYC-GT-Data
This R markdown file cleans and prepares two datasets on NYC Gifted & Talented (GT) exam results from 2017-2018 and 2018-2019.
# Datasets
The two original datasets are:
Copy of G&T Results 2017-18 (Responses) - Form Responses 1.xlsx
Copy of G&T Results 2018-19 Responses - Sheet1.xlsx
These contain exam results and survey responses from over 7000 students who took the GT exams in NYC across 2 years.
# Data Preparation Steps
The data preparation steps in this file include:
1.	Packages Used
The following R packages are loaded for data import, manipulation, visualization and export:
readxl - to import Excel files
dplyr - for data manipulation
ggplot2 - for data visualization
writexl - for exporting cleaned data to Excel

2.	Data Import
The read_excel() function from readxl package is used to read the Excel files into R data frames.
The column names are printed to inspect the data types and column names.
The two data frames are row bound using rbind() into a single data frame called combined_data.
3. Fix Column Data Types:
Columns like "Entering Grade Level", "Birth Month" etc are converted from character to factor datatypes using as.factor() to store them as categorical variables.
Test score columns like "OLSAT Verbal Score" are converted to numeric from character using as.numeric() after removing non-numeric chars using sub().
5. Handle Missing Values:
is.na() is used to check each column for missing values, and stats printed.
For numeric columns, missing values are imputed with the mean using ifelse() and mean().
For categorical columns, missing values are imputed with the mode using ifelse() and mode().
6. Identify and Handle Outliers:
ggplot() and geom_boxplot() are used to plot each numeric column and identify outliers visually.
Outliers are handled by winsorizing the columns between 25th and 75th percentiles using custom winsorize_single_column() function.
7.	Correct Invalid Values
Invalid district name values like "MisspelledDistrict" are corrected using ifelse().
8.	Exploratory Data Analysis
Histograms, boxplots, line graphs and scatterplots are generated using ggplot2 to understand distributions and relationships between variables.
9.	Export Cleaned Data
The cleaned dataset is written to an Excel file using write_xlsx() from writexl package.
# Output
The output is a cleaned Excel file "G&T Results cleaned_data.xlsx" that can be used for further analysis and modeling.
# Usage Notes
The R markdown file is well commented to explain each step. To use this:
•	Download the two original Excel files
•	Open the R markdown file in RStudio
•	Run the code to perform data preparation
•	Output will be saved as "G&T Results cleaned_data.xlsx"
