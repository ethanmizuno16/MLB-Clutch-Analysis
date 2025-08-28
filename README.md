# MLB-Clutch-Analysis

Does Clutch Actually Exist in Baseball?

Authors: Raj Duraisamy, Ethan Kawahara, Ethan Mizuno

Summary
Our project aims to analyze the concept of “Clutch Performance” within Major League Baseball, focusing exclusively on batting. We define clutch as an athlete’s change in win probability under pressure in game-critical moments. By dissecting these high-pressure situations, our project aims to unveil whether clutch performance is a myth or a reality, backed by statistical evidence. 

Key Areas of Investigation:

Existence and Consistency of Clutch Performance
Our primary goal is to determine if certain MLB players consistently outperform their usual metrics in clutch situations across multiple seasons. We aim to identify if these clutch performances can be statistically supported or if they are merely a random distribution of success. 
Measurement of Clutch Performance
The study will measure clutch performance in two distinct ways
Differential Approach: The difference between a player’s performance in clutch situations and their average performance
Win Probability Summation: The cumulative change in win probability for every at-bat in a clutch setting
Criteria for High Pressure Situations
Inning Threshold
We will narrow our focus to only performances in the 8th inning or later. By creating this parameter, we assume that the final innings of a game have a higher impact on the outcome, making the player's performance during this time more important.
Score Differential
The study will also only consider the moment where the score difference is two or less as key clutch situations. This criteria will help pinpoint the exact moments where a player’s performance has a heightened chance to alter the result of the game.
Strategic Value of Clutch Hitters
Beyond identifying the existence and consistency of clutch hitters, the project seeks to quantify their strategic value to an MLB team. The project aims to explore how crucial clutch hitters are to a team’s success and overarching strategy, potentially influencing managerial decisions, player selection, and game day tactics. 
The project will also explore the influence of team salaries on the total clutch rating, investigating whether financial investment in clutch players correlates to wins. 
Research Questions:
Can statistical evidence support the existence of consistent clutch performance among players across seasons?

Answer: Yes, the statistical evidence compiled through our project  supports the possibility of consistent clutch performance among players across multiple seasons. By analyzing data spanning several years, we observed enduring patterns of performance in clutch situations that some players repeatedly demonstrated.

Do certain MLB players consistently perform better in high-pressure situations, or is clutch performance randomly distributed?

Answer: Our research conclusively demonstrates that clutch performance is not a random distribution but rather a distinguishable trait exhibited by specific players over multiple seasons.

How critical are clutch hitters to the overall success and strategy of an MLB team?

Answer: After breaking down what players are consistently clutch in the MLB, we then merged our findings to see if clutch rating for a team truly affects their success and found that there is no correlation between the two variables.
	
Motivation
We wanted to explore the clutch phenomenon in baseball, focusing on how players and teams perform under pressure and how this correlates with winning teams. Traditionally, clutch isn't a metric that's directly tracked in sports analytics, yet fans and media love to use it to describe players and teams. Failing to perform “in the clutch” gets you the immediate label of being a “choker”. Baseball, in particular, is a sport where these moments arise often, where players are demanded to be composed and deliver outstanding performance to secure the victory. We want to know if this common metric to describe players and teams is a quality that actually brings value for winning in the MLB. By comparing clutch and non-clutch performance, we aim to quantify and visualize the impact of high-pressure situations on player and team success. Finding a lack of correlation between success during the regular season and teams that perform during later innings of a close game can provide evidence for clutch being an overrated label.
Datasets

For our project, we utilized the extensive features of the PyBaseball package, an open-source Python library renowned for its extensive access to baseball statistics and analytics. From this package, we gathered play-by-play data from 2019 to 2023, which includes detailed records from Baseball Savant, a detailed statcast website that is utilized for advanced MLB statistics.  By breaking down each game into individual pitches and their outcomes, we were able to analyze players' performances under high-pressure situations and ultimately try to identify patterns that could indicate whether clutch performance is a tangible trait or merely a myth.
By incorporating the PyBaseball package into our project, our comprehensive initial dataset consisted of over 3 million entries, which we've refined to 76,106 crucial clutch events involving 1,136 unique players. These events were selected through a filtering process where we looked for particular events that occurred during a game that held weight in terms of a player’s clutch ability. More specifically, our data is organized by year, allowing us to observe patterns and trends over time and assess the consistency of clutch performances across different seasons.  This season by season breakdown is crucial for our analysis as it enables us to dissect and understand the evolution and potential longevity of clutch ability in players. Due to the incorporation of data from MLB Statcast, Baseball-Reference, and Fangraphs, we've developed a robust dataset that we found very effective in our analysis of who is considered a clutch player and whether they can replicate it over multiple seasons.

Method 
First, we import relevant packages and retrieve baseball pitching data for the years 2019 to 2023. We then joined all the datasets for each year and since we want to differentiate by each year, we add a year column for each dataset. 
For our initial data setup, we first added columns for the names of each batter. Then, we filter events so we only keep relevant batting events like if a player got a single or a home run. Since it is important for us to create a binary column to see if players received a hit. We also create a column to keep track of change in win expectancy as a result of a particular play, but with adjustments based on whether the batting team is playing at home or away. Finally, we filter the data into two different sets based on if the situation in the game can allow for “clutch” plays based on our calculation. So, we look for plays with a score differential less than or greater than two in the eighth inning or later. Now, the data is properly filtered and formatted for our use.
Now, we need to further transform the data in order for effective analysis. We add columns such as a binary column that signifies whether a player is on first, second, or third base, with values of 1 (occupied) or 0 (unoccupied). This is crucial for understanding the pressure of the situation as the number of runners on base can significantly impact the clutch nature of a play. After adding these extra metrics for our calculation, we finally calculate a “clutch rating” for each player in each season. We do this by assigning scores to each player based on a function to reflect their contribution to changes in win expectancy in high-pressure, late-game moments. It is then important to normalize this on a 0-10 scale for clarity. We finally use these scores to aggregate an overall clutch score for each player and team over the years. This allows us to see which players and teams consistently perform in these crucial moments and whether or not these scores correlate with wins during the season. 
For our final step, we visualized our data so we can better understand our insights. We produce plots for the distribution of clutch ratings for players and teams and the relationship between team clutch ratings and wins.

Results
Research Question 1: Is Clutch Performance a Myth or Reality?
	To answer if being “clutch” is a myth or reality, we first dove into analyzing the outcomes of an at-bat and seeing how they could affect the win probability of a team in a given game. By tracking the outcomes of every clutch event from the last 5 years old MLB data, we found several things that surprised us. 


One of the more intriguing findings from our analysis was the impact of triples on win expectancy, revealing a pattern that contradicts the general expectations about hits in clutch moments. Specifically, separates every triple that was hit in a clutch scenario by the number of outs before the at-bat and noticed that triples with 0 and 2 outs have had a similar impact on a team's chances of winning the game at 0.219938% and 0.1971% respectively. 

However, the game impact changes dramatically with only 1 out. With one out, triples were found to have a greater average change in win expectancy compared to 0 and 2 outs at 0.26221%. This finding suggests that triples with 1 out are particularly valuable and could be considered more clutch due to their greater impact on the win probability of a team. 

Contrary to triples, singles and doubles do not follow this pattern of affecting win expectancy. Rather, the winning probabilities appear more consistent, increasing slowly depending on the number of outs.

Moreover, walks, often overlooked in discussions about clutch hitting, displayed an interesting pattern. Walks with 0 outs were found to significantly boost win expectancy over walks with 1 or 2 outs. This outcome highlights the strategic value of a walk in setting up potential scoring opportunities, particularly when no outs have been recorded.

By analyzing specific outcomes like triples and walks in clutch situations, we gain insights into how certain events can indeed sway the win probability for a team, supporting the argument that clutch performance can be both a reality and quantifiable. However, the varying impact of different types of hits and the specific conditions under which they occur (e.g., the number of outs) also suggests that the concept of being clutch is more complex, dependent on context and not just the ability to perform under pressure

By quantifying clutchness using the change in win probability of a team, we found that the most clutch player of the past 5 years was 2023 Bryce Harper of the Philadelphia Phillies followed by 2019 Christan Yelich of the Milwaukee Brewers, and 2023 Corbin Carroll of the Arizona Diamondbacks. Using standard deviations as a measure of variability, we discovered that these players' clutch ratings were approximately 5-6 standard deviations above the mean clutch rating. To put this into perspective, in a normal distribution, 68% of values fall within one standard deviation of the mean, 95% within two, and 99.7% within three. A rating 5-6 standard deviations from the mean is phenomenally high, indicating that their performances in clutch situations were not just better than average, but extraordinarily.

	
Research Question 2: Do certain MLB players consistently perform better in high-pressure situations, or is clutch performance randomly distributed?

In order to find consistency of clutch of MLB players, we need to utilize variance. We need to compute the spread of clutch performance metrics for each player over the past five years provided by the data. 

First, we need to group the data by player and take the variance of the clutch rating for each player. This will allow us to get an effective visualization.



A histogram is great for showing the overall distribution of variances among players, highlighting any outliers or common patterns. The plot reveals to be very right-skewed, illustrating that players have very low variance for their clutch ratings. It seems that players are relatively consistent in their clutch metrics. Even though the variance may be low we cannot conclude that all of these players could be considered reliable in high-pressure situations. Players worse in the clutch consistently perform worse and players better in the clutch consistently perform better.


Research Question 3: How critical are clutch hitters to the overall success and strategy of an MLB team?

To answer the question, we wanted to observe if there was any relation between the sum of the clutch ratings for an entire team and the wins of the team in a given season. 
From the data, we grouped together the teams and found the total clutch rating for each team over the past five years. We then scaled the data from a 0-10 range allowing the comparison essay comparison between each team. 



From this, we were able to see that the Atlanta Braves, the New York Yankees, and the Tampa Bay Rays are the three teams with the highest total team clutch rating from the past 5 years while the Oakland A’s, the Chicago Cubs, and the Detroit Tigers have collectively the lowest total team clutch. 
	From this visual, we then used the standing data from Pybaseball to observe if the clutch hitting was correlated to wins. At first glance, it seems like there is a clear pattern in the data, however, by delving deeper into the data, the entire bottom left of the data is from 2020 which was a shortened season because of the COVID-19 pandemic. These outliers in the data skews the data incorrectly, so it must be removed from the plot. 


Once removing 2020, it is clear that there is no correlation between the total clutch rating of a team and the wins for the team in a given season. Using the Plotly package, we were able to create an interactive graph, allowing a user to investigate the wins of a team, the team name, the year, and the total clutch rating for that team. 

	Once finding this graph, we were then curious to see if the spending of the team was correlated at all with the wins of a team and the total clutch rating for a given year. Again, we created an interactive Plotly graph, giving the users more information about the data. However, plotting the payroll on its own would skew the data because inflation affects the leagues’ spending in a given year. Instead ,we standardized the spending of each team for the given year, allowing for us to compare the spending of each team across several years. However, even once plotting the scaled payroll for each team, there was still no clear trend, leading us to the conclusion that the clutch hitting of the team on its own, is not correlated to success of a team. 


Impact and Limitations

Our thorough analysis of a baseball player’s clutch performance has significant implications for team management, coaching, and player strategy. With this information, teams are able to strategize more effectively and purposely position players with higher clutch ratings in pivotal game situations to improve their win probability. Additionally, our findings highlight unique situations like how triples with one out can disproportionately increase win expectancy, while walks with zero outs are more valuable than a walk with one or two outs. By having these statistics compiled and visualized, coaches are able to make better real time decisions based on the situation. 
	
	Through our analysis, we found that there might be unintended consequences such as people who may be excluded or harmed by our analysis. Since our project aims to pick out players on a team who are consistently clutch, those without a strong presence in clutch situations might find their value underestimated or their roles diminished. This could lead to negative impacts on their progression as a player, contract size and their longevity with a team. By solely targeting clutch performance, our analysis may inadvertently undermine other characteristics of a player that are usually sought after by many front offices. Leadership, defensive skill and personality within the club may all be looked over since our analysis focuses on the offensive side of baseball, particularly in situations where the game is on the line.
	In terms of the data setting, our analysis was limited to regular season games from recent years and excluded playoff statistics and games with playoff implications, where players might exhibit different clutch behavior. Therefore, users of our analysis should stray away from applying our conclusions to postseason scenarios. Furthermore, the definition of clutch used in our analysis could also impact the findings, as it may not align with every possible interpretation of clutch performance in baseball. Additionally, our analysis is shaped by the data available from MLB Statcast, Baseball-Reference, and Fangraphs, which, while extensive, cannot account for every in-game variable such as psychological resilience, team dynamics, and opposing team strategies. In the future, we would hope to integrate our results into a wider array of data and observations for a more encompassing overview of a player's clutch abilities. MLB team strategists such as data analysis, general managers and coaches should use our analysis as one of multiple tools for evaluating player performance and not rely on it as a primary tool for game strategy.
 
Challenge Goals
Multiple Datasets (different years, merging of multiple statistics)

Our analysis of clutch hitting used several different datasets from several different sources. 
First we used Statcast data from 2019-2023 gathered using the Pybaseball library. We gathered each year independently and then appended them with a year column, allowing us to analyze trends in the data over this 5 year span. 

Another dataset that we used to was the playerid_reverse_lookup function in Pybaseball which allowed us to map the player ID to their real name using a database of player names and IDs. We merged this data into the main Statcast data to give us a better understanding of the data and also cross check our results with player names rather than ID numbers. 

The standings data was also an integral part of our analysis as it contained the wins, losses, and other season-long performance metrics that were important to analyzing the impact of clutch hitting on the success of a team. We were able to gather the standings data using the Pybaseball package and compare it to the Statcast data which we grouped together by team and year. 

We also used MLB payroll data from The Baseball Cube which was downloaded in XLS format. The payroll data allowed us to analyze the relationship between clutch hitting the total payroll of a team in a given year. 

New libraries (plotly, PyBaseball)

While this was not one of our initial proposed challenge goals, we found that utilizing new libraries was the most ideal method to collect the data necessary to access clutch performance. Our project utilizes the PyBaseball package to extract detailed play-by-play data. This package scrapes Baseball Reference, Baseball Savant, and FanGraphs. As our project relies on advanced metrics, it is imperative that we get data that goes deeper than just the surface of baseball statistics. This package gives us statcast data, pitching stats, batting stats, and much more. The package also gave us access to the league standings of each year, allowing us to analyze the success of a given team.

Utilizing plotly also allowed us to create visually appealing and engaging graphs that allowed for user interaction to understand the data further. We used a plotly package to allow us to hover over a specific point in our created scatter plots and learn more about the data of that point. Specifically, we used the package to analyze the impact of a team’s clutch rating on success, allowing each point to say the name of the team, the year, the amount of wins, and the total clutch rating of the team. We also applied the plotly to graph teams’ clutch rating, wins, and scaled payroll to analyze any trends. Each point was labeled with the payroll, scaled for their respective year. 
Work Plan & Evaluation

Task
 Project Workflow
Estimated Amount of Time




Data Imports and Installation
Install necessary libraries and import modules for data manipulation and visualization.
Understand what the libraries and modules are providing and how can we use them for the project
2 hours
Data Preparation
Add year information to data, merge datasets, perform player ID lookups, and set up binary columns for on-base events.
1 hour
Data Transformation
Transform win expectancy based on inning and batting team. Calculate hits and adjust win expectancy change.
1 hour
Data Analysis
Create separate datasets for different game scenarios and perform groupings for analysis.
Do the analysis on groups of filtered data that are clutch and also non-clutch
2 hours
Visualization
Generate plots to visualize data, such as win expectancy changes, clutch ratings, and bar charts for teams.
1 hour
Team Analysis
Group by teams to calculate clutch ratings and visualize team performance.
1.5 hours
Player Analysis
Rank players based on clutch ratings, both in total and scaled.
Graph the players’ rankings and put the names and scores in context using graphs and statistics. 
2 hours
Wins Correlation
Merge with standings to analyze correlation between clutch rating and wins, including scatter plots.
1.5 hours
Payroll Correlation
Merge with payroll data and analyze correlation between payroll, clutch rating, and wins.
1.5 hours
Final Visualization
Create final scatter plots to visualize correlations with payroll included.
1 hour
Documentation
Document the process and results.
3 hours
Review & Debugging
Review code for errors and potential improvements.
1 hour
Presentation Preparation
Prepare materials and results for presentation.
1 hour


Evaluation:

Overall, our work plan estimates were not very accurate for the entirety of the project. As we all had varying schedules, it made it very hard to all meet at the same time to make productive progress on the project, ultimately leading us to divide and spearhead different parts of the project. We spent a significant amount more time cleaning and processing the data for our initial plan to predict home runs. Once we began manipulating the machine learning aspects of our project and decided that predicting home runs would not be as interesting as analyzing clutch performance, we had to completely redesign our work plan. This added a substantial amount of time to the data processing and cleaning as we had to refilter our data to focus on clutch moments rather than key elements such as launch angle and pitches. After we had a clear vision of our redesigned project, we stayed pretty on track with the time breakdown for each part of the project with some minor hiccups along the way. To give finite time estimates for completion of different tasks is not truly realistic when working on a large scale project like this, especially when you are creating all the code elements yourself. As a group we would bounce ideas off of each other and this would lead to a lot of trial and error in our code, evidently increasing our time spent on a certain part of the project at times. 
Testing. 
We made sure to test our functions and plots using smaller subsets of the overall data. Working with smaller subsets of data was very helpful as it allowed for quicker iterations and in turn, faster debugging. Our functions were created for setting up the data for analysis and computing new metrics. We tested these functions by manually filtering and computing metrics and seeing if the length of that data frame matches with the lengths of the data processed by the function. In order to get a larger coverage of edge cases, we made sure to test for empty data sets. 
Testing the plot was challenging since we weren’t sure how the graphs were going to look beforehand. In order to get over this obstacle, we focused on validating the data and the data processing methods (as described before) that were used to generate the plot. Essentially, we wanted to ensure the points that were used in the graph were as intended. Additionally, we used smaller subsets (with a large enough sample size) to create plots. The plots looked incredibly similar to what we visualized for the whole data set, as seen below.
