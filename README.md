# MadMarch-Prophet

The 1st Part of the code is importing necessary packages and libraries, setting the working directory, reading in a CSV file containing game data, renaming two columns, and then creating four data frames for each region of the NCAA basketball tournament (South, Midwest, West, and East) by selecting only the rows that contain teams from each region.
Specifically, the code first imports several packages including tidyr, plyr, dplyr, tidyverse, readxl, lubridate, ggplot2, hrbrthemes, viridis, glmnet, pROC, and corrplot.
Then, it sets the working directory to "~/Documents/Data 332" and reads in a CSV file called "2023 Game Data copy.csv" into a data frame called df.
The code renames the third column to "TEAM" and the thirty-ninth column to "WIN" using colnames(df)[3] = "TEAM" and colnames(df)[39] = "WIN".
Next, the code creates four separate data frames for each region of the NCAA basketball tournament (South, Midwest, West, and East) using the select and filter functions from dplyr. The select function is used to choose only the columns SEED, TEAM, and WIN from df. The filter function is used to select only the rows that contain teams from each region. For example, the south_region data frame contains only the rows that contain teams from the South region, which are "Alabama", "Arizona", "Baylor", "Virginia", "San Diego St.", "Creighton", "Missouri", "Maryland", "West Virginia", "Utah St.", "North Carolina St.", "College of Charleston", "Furman", "UC Santa Barbara", "Princeton", and "Texas A&M Corpus Chris". The distinct function is used to remove any duplicate rows that may exist within each data frame.

# Exploratory Data analysis 

 <img width="748" alt="Screen Shot 2023-03-26 at 8 57 27 PM" src="https://user-images.githubusercontent.com/75454891/227843109-8084e6e1-fde7-4f9d-bf1c-4e47a8b0d694.png">
 
These are four separate ggplot commands used to create bar charts showing the win percentage by team for each of the four NCAA tournament regions: East, South, Midwest, and West.
Each ggplot command takes in a data frame (presumably containing the win percentage data for the respective region), sets the x and y aesthetic mappings using aes, and then adds a geom_col layer to create the bar chart. The fill parameter is used to set the color of the bars, and width is used to adjust the width of the bars.
Additionally, each plot has a customized x and y axis label, a plot title, and a theme with adjusted x-axis text angle. Finally, each plot has a scale_fill_manual command used to set the color of the bars manually.

<img width="635" alt="Screen Shot 2023-03-26 at 8 57 16 PM" src="https://user-images.githubusercontent.com/75454891/227854532-578059e8-6ebf-4551-aa90-e272b054298a.png">

The cor() function calculates the correlation coefficient between the Seed and WinPct variables in the df data frame, and assigns the resulting matrix to the correlation_matrix variable. The print() function is then used to display the matrix in the console.
The correlation coefficient is a statistical measure of the strength and direction of the linear relationship between two variables, Seed and Win . It ranges from -1 to 1, with -1 indicating a perfect negative correlation, 0 indicating no correlation, and 1 indicating a perfect positive correlation.

# 
