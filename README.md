# Analyzing Baltimore Election Precincts (2016)
## Background
Baltimore, Maryland divides voting into different precincts. The precinct number is written as a number in the format xx-xxx. The first two numbers indicate the election district, and the second number indicated the precinct within that district. These election precints and districts are purely for administering the election and counting votes. They are different from congressional or legislative districs. 

These districts and precincts have lots of data on them so we can use them to analyze election results. I decided to analyze the 2016 election.
  
## Business Question
What Election Precincts in Baltimore exhibit similar party voting behavior in major political races?

## Analysis
Of the five clusters I compiled the characteristics of each cluster anchor. Note that these traits are in relation to the average Baltimore. For example the precinct that is "Very Republican", Republicans only got around 33% of the vote. This is because baltimore is a very democratic city.

Cluster 1 (Blue) - Average size, Very Democratic, all others below average.
Cluster 2 (Red) - Large, Extremely Republican, Extremely Libertarian, Very little Democrats. 
Cluster 3 (Black) - Small, Very Libertarian, Average Republican and Democrat.
Cluster 4 (Green) - Large, Very Green, below average democrats.
Cluster 5 (Yellow) - Very Small, Very Democratic, all others below average. 

Just looking at the factors the Blue and Yellow clusters are very similar except for size. The others are similar in having less democrats than the average. If I were doing this again I might exclude the size parameter, because it is less related than just straight vote percentages. The final map is shown below along with a race map of Baltimore.

![alt text](https://github.com/cmclane1/comparing-baltimore-bristol-county-household-income/blob/main/Bristol-Baltimore.png)

I do not believe the anchor positions are of any importance but there are a lote of interesting things here. First look at the blue and yellow clusters (which are extremely similar in political party voting, just not size) and you can clearly see that they line up extremely closely with the neighborhoods that are majority Black. Then the Green and Red clusters are in majority white neighborhoods. The Black cluster leans white but is more erradic and has a smaller number of precincts (also is average in Republican and Democrat). A conclusion is that Black Baltimoreans are vote more democratic on aggregate. White voters vote less democratic, but are split. That central corridor of white majority neighborhoods (Where JHU is) voted heavily for the green party, a liberal 3rd party. While other white neighborhoods near the Patapsco River or Townsend, lean Republican (conservative).

My last takeaway to maybe be looked into in the future is that these patters of race and voting also reflect the shape of the congressional district with limited exception. It would be interesting to expand this project to look at the entire state of maryland and analyze the gerrymandering that has clearly taken place. 

## Step by Step Walkthrough
First I had to clean up the data. I first removed all write in candidates because I saw them as largely outliers, who often were not part of one of the major parties, and simplify my analysis, and any further analysis. I did however notice when doing this that the number of write in votes was actually quite large, and after further investigating the vast majority of these votes were for a democrat Sheila Dixon running for mayor. Baltimore is a very democratic city, so my assumption is she lost the primary and thought she still stood a shot with a write in campaign so I did include her in my analysis because she did get a significant amount of votes.

I also decided to focus only on major races, for reasons of simplification and my guess is that most people actually care and vote for these races, and it is much simplier to treat all votes as equal. It did not make sense to me to count a democratic comptroller vote equal with a vote for hillary clinton. (Also you tend to get uncontested races for less important offices). So the only races included were President/Vice-President, Mayor, U.S. Senator, and Representative in Congress. 

Other things not considerd in this analysis. There was no liberatarian running for Rep in Congress or Mayor. Also Baltimore covers multiple Congressional districts, so some precincts will be voting for different people and this could have an affect, I chose to ignore this because I only analyzed the party that was voted for. 

Excel did not have the properly formatted precinct numbers, they were broken into two columns, so I used equations to make one with that. Then in another table I used countif to sum all of the votes cast in a precint. I also had to concatenate a the precinct number with the party of the candidate so that I could also do the same countif process so find how many votes were cast for each party in each precint. Using this I found the precent of the vote each party got in each precinct. I then standardized these percents and the total number of votes. Then found the euclidean distance squared using sumxmy2 function of each precinct to the five chosen anchor precincts. Then I found the minimum of these distances to associate each precinct with an anchor. Then using solver and the sum of these minimum distances if found the optimum anchor points for a five cluster analysis.

I then used conditional coloring of cells so I could visually identify which anchor each precint was with. Lastly I took a map of the precincts and PAINSTAKINGLY put a colored circle over each precint and a colored anchor over the anchors. 
  
## Links to Sources
[Analysis](https://github.com/cmclane1/comparing-baltimore-bristol-county-household-income/blob/main/Baltimor-Bristol-Analysis.xlsx)

[Data](https://github.com/cmclane1/comparing-baltimore-bristol-county-household-income/blob/main/Baltimore-Bristol-Data.xlsx)

[Opportunity Atlas](https://www.opportunityatlas.org/)

[Baltimore Wikipedia](https://en.wikipedia.org/wiki/Baltimore)

[Bristol County Wikipedia](https://en.wikipedia.org/wiki/Bristol_County,_Rhode_Island)

[Catholic Counties of the US](https://www.thearda.com/ql2010/QL_C_2010_1_26c.asp)
