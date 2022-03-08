# Machine Learning Foundation

## Premier League Season stats

#### Premier League

The Premier League, often referred to as the English Premier League or the EPL (legal name: The Football Association Premier League Limited), is the top level of the English football league system. Contested by 20 clubs, it operates on a system of promotion and relegation with the English Football League (EFL). Seasons run from August to May with each team playing 38 matches (playing all 19 other teams both home and away). Most games are played on Saturday and Sunday afternoons.

The competition was founded as the FA Premier League on 20 February 1992 following the decision of clubs in the Football League First Division to break away from the Football League, founded in 1888, and take advantage of a lucrative television rights sale to Sky.From 2019 to 2020, the league's accumulated television rights deals were worth around £3.1 billion a year, with Sky and BT Group securing the domestic rights to broadcast 128 and 32 games respectively. The Premier League is a corporation where chief executive Richard Masters is responsible for its management, whilst the member clubs act as shareholders.Clubs were apportioned central payment revenues of £2.4 billion in 2016–17, with a further £343 million in solidarity payments to English Football League (EFL) clubs.

### Objective

This model is focused on try predict match total goals.

### Dataset description

A dataset which contains a list of games, results and some numbers about the games of premier league, the england soccer league.

- [Dataset link](https://data.world/sportsvizsunday/august-eurofootball/workspace/file?filename=Soccer+History.xlsx)

### Features list

- Season: <b> string (years of the season where the games take place)</b> </b>
- Game:<b> int (number of each game at each team)</b>
- Unique ID:<b> string (unique id of each game)</b>
- Date:<b> string (date in dd/m/yyyy format)</b>
- Team:<b> string (principal team name)</b>
- Opponent:<b> string (visitor team name)</b>
- Team G:<b> int (principal team goals)</b>
- Opp G:<b> int (visitor team goals)</b>
- Win Loss:<b> string (status of principal team result, win, loss, draw)</b>
- Points:<b> int (goals of game)</b>
- Referee:<b> string (referee name of game)</b>
- Team S:<b> int (principal team shoots)</b>
- Opp S:<b> int (visitor team shoots)</b>
- Team Fouls:<b> int (principal team fouls)</b>
- Opp Fouls:<b> int (visitor team fouls)</b>
- Team Corner:<b> int (principal team corners)</b>
- Opp Corner:<b> int (visitor team corners)</b>
- Team Yellows:<b> int (principal team yellow cards)</b>
- Opp Yellow:<b> int (visitor team yellow cards)</b>
- Team Red:<b> int (principal team red cards)</b>
- Opp Red:<b> int (visitor team red cards)</b>

### Initial Plan

Explore and measure the quality and quantity of data, applying data cleansing and feature engineering techniques to gain insights and formulate hypotheses about the number of goals in a game. using data analysis techniques the object of this exploratory research is to understand variations and trends that can provide us with better clarity on how the results can be influenced according to the statistics of each game, after data analyses step we gonna try predict match total goals on plays.

### Data Cleaning and Feature engineering explanation

For data cleaning and engineering, several techniques were applied so that the dataset was satisfactory so that it could be used by any machine learning model that might require it, in this way the following techniques were performed for data cleaning and engineering

- Remove the UniqueId field, a unique field cannot be supply valid information to a data analyse.
- About missing values we chose to exclude the line that contains a missing value and matain 14440 observations
- Separate data field in tree fields, day, mouth and year.
- Convert the values loss, win and draw to 0,1 and 2 respectively.
- rename the win Loss column to result.
- Remove tha character '-' of season id (1993-94 to 199394).
- Create the columns total fouls, total corners, total yellow cards and total red cards.
- Identify and treat outliers, we chose to keep outliers due to the nature of the analysis being about a sport, it is relatively common in sports to get results strangely out of the curve
- rename column names to name most appropriate
- convert string variable to dummies with one hot encode technique
- save the filtred dataset in a new csv file

### Key Findings and Insights

After extensive analysis we were able to reach the following conclusions based on the experiments shown below.

- We found an apparent relationship between number of goals and number of fouls, apparently games with high number of goals tend to have low number of fouls.

- the average goals increase by 0.1 from 2000 to 2018, a negligible increase, can be interpreted as a normal variation.

- the average number of absences decreased from 27 in 2000 to 19 in 2018, a continuous drop between years of approximately 30%.

- despite the number of fouls having dropped, the number of red cards remained stable.

- We found another apparent relationship between number of goals and number of corners, apparently games with high number of goals tend to have a median number of corners.

- corners and fouls stop the game, so the time taken by corners and fouls is likely to decrease the number of chances for goals due to the ball being out of play.

- when the game has 3 red cards or more, the average of goals increases by approximately 1 goal.

- Teams with fewer fouls achieved a higher frequency of wins.

### Summary of training

Trainning tachnics applyeds:

- Linear regression simple
- Linear regression with standard scaller
- Lasso regression with Hyperparameters alphas
- Ridge regresion with Hyperparameters alphas
- polynomial features to regularization model

### Result of experiments

The best result is the Lasso regression with alphas 0.01, the accuracy of this regression is
0.21169758924190396, but this result is very low, due to this it was concluded that it is impossible to predict the number of goals, at least with these dataset

### hypothesis

After the initial analysis we were able to raise three possible hypotheses for our exploration

- hypothesis 1: A team that receives a red card is more likely to receive a goal.
- hypothesis 2: The team that commits more fouls, are more likely to win.
- hypothesis 3: The fact that a team scores a goal increases its own chance of conceding a goal.

### Test result of hypothesis 3

FALSE, the teams that have the highest frequency of victories are the team with less number of fouls, in the research the teams with most elevate number of fouls reached a maximum of 40% of victories while the teams with lesser fouls reached up to 60% of victories.

### Suggestions for next steps in analyzing this data

- Analyse if the results of games can be influenced by the referee
- Analyse if the number of goals can be influenced by the previous game
- Analyse if the number of games in a season can influence the number of goals, cards and fols

### Quality of dataset and requets for more data

The general quality of this data set is satisfactory for a superficial analysis of game results, we can raise some hypotheses and some factors that influence the result of the English league, however, for a more in-depth analysis, a larger set of features would be necessary, it would be plausible require data from

- Period of the game in which the goals were scored
- Game period in which the cards came out
- If the game has added to its time
- What positions of the expelled players
- Which players scored the goals
- Goals disallowed
- Goals disallowed by VAR
- expulsions reviewed by VAR
