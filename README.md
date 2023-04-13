
<img width="631" alt="Screen Shot 2023-04-13 at 2 19 54 PM" src="https://user-images.githubusercontent.com/75454891/231861644-adbd73c5-bcca-4d4e-aa28-12c611ffd747.png">
                                                
                                         





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

# Prediction steps 

We then define a function "predict_winner" that takes in two teams as inputs and predicts the winner of the game based on their seeds and win percentages. We use the "if" and "else if" statements to compare the seeds and win percentages of the two teams to determine the winner.
Next, we create a list "games" with the matchups for the first round of the tournament. 

We use the "sapply" function to apply the "predict_winner" function to each game and store the predicted winners in a vector "winners". We then print the predicted winners for each game.
After the first round, we create a new data frame "teams" with only the teams that won their first-round games. We then define the matchups for the second round in a data frame "matchups". We loop through the matchups and predict the winner of each game based on the win percentages of the two teams, using a random number to determine the winner.

Finally, we create a new data frame "teams" with the teams that advanced to the third round. We define the matchups for the third round in a list "matchups". We loop through the matchups and determine the winner of each game based on the win percentages of the two teams, using a random number to determine the winner.

Due to the small size of our dataset, the prediction model used in this Shiny app is based on a simple algorithm that considers the seed and win percentage of two selected teams to predict the winner of a matchup. The algorithm first checks which team has a lower seed, and if one team has a lower seed, it is predicted to win. If the seeds are the same, the algorithm then checks which team has a higher win percentage, and the team with the higher win percentage is predicted to win.
It's worth noting that this algorithm is a very basic model, and there are many other factors that can influence the outcome of a basketball game. Factors such as injuries, team chemistry, and player performance can all affect the outcome of a game, and are not taken into account in this model. Nonetheless, it provides a simple and intuitive way for users to compare two teams and make a prediction based on basic statistics.

# Game prediction 

# South 
<img width="1001" alt="Screen Shot 2023-04-13 at 2 08 08 PM" src="https://user-images.githubusercontent.com/75454891/231860097-2a6ecf6c-bc54-4bb4-80de-7b7677715baa.png">
 
# Midwest 
<img width="957" alt="Screen Shot 2023-04-13 at 1 09 33 PM" src="https://user-images.githubusercontent.com/75454891/231860285-9416f79e-39a1-4cac-9b8a-cd43d235a650.png">




# Shiny App

The first part of the code defines the user interface (UI) of the app using the fluidPage function from the Shiny package. The UI has two panels: a sidebar panel and a main panel. The sidebar panel contains a select input control for the user to choose a region. The main panel has two plot outputs to display the correlation matrix and the prediction plot.

The second part of the code defines the server-side logic using the server function. The server function is responsible for processing user input, creating reactive data frames, and generating the output for the UI. The reactive function is used to create a reactive data frame based on the user's input region. The renderPlot function is used to generate the correlation matrix and prediction plot based on the reactive data frame.
Finally, the shinyApp function is used to run the app by passing in the UI and server functions as arguments.

<img width="779" alt="Screen Shot 2023-03-29 at 1 28 57 PM" src="https://user-images.githubusercontent.com/75454891/228659871-868cda63-2fce-449f-8b0a-7864ea3eb580.png">

The first Shiny app in the code provided allows the user to select two teams and it predicts which one will win based on the seed number and win percentage of the teams. It also displays a scatter plot comparing the two teams' seed number and win percentage.
The second Shiny app allows the user to select a region, and it displays a correlation matrix plot of the seed number and win percentage of all teams in that region. It also displays a scatter plot of all the teams in the selected region, with the y-axis representing the seed number and the x-axis representing the win-loss record. The plot colors the teams based on their win percentage and labels each point with the team name. The plot provides a visual prediction of which team is likely to win based on their seed number and win-loss record.
