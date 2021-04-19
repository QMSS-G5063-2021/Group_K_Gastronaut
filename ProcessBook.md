# Process Book

Members: Luke Artola, Samantha Li, Yun Yee Tan

## Topic
Debt 


# Visualizations

## Horizantal Bargraph: International Debt to GDP Changes due to Covid
We wanted to start off with the reason we decided to look into this topic was that sovereign debt in general has been increasing at a steady clip around the world but with Covid it has jumped at a much faster rate. We decided to pick 7 developed economies and visualize just how much of an impact Covid has had on their fiscal situation. For this I was lucky and I was was able to pull clean data already for the graph. We decided to do a horizontal bar chart in descending order as to allow direct comparison amongst the 7 countries.    

Data Source: Institue of International Finance
https://www.iif.com/Research/Capital-Flows-and-Debt/Global-Debt-Monitor

## Choropleth: State Debt Level 2020
Wanting to explore how the current fiscal situation was at home we visualized the 2020 state debt levels to see on a macro level how the states fared especially with Covid. I pulled the state debt statistics and clean it up a bit as the debt calculations were coded as characters. After I converted it, I filtered out DC as it is not a state. I used the shape file from the Urban institute and joined it to my debt data. I then used tmap to produce the resulting choropleth with a lot of attention paid to manually adjusting the breaks for the scale given the skewness of the debt levels. 

Data Source: Forbes
https://www.forbes.com/sites/andrewdepietro/2020/11/23/states-with-the-most-and-least-debt-in-2020/?sh=759af88378a3


## HDI

## International Debt
In this section, we will explore the dynamics of international debt by analyzing debt flows between debtor nations and creditor nations/organizations.

Data source: The World Bank
https://databank.worldbank.org/source/international-debt-statistics:-dssi#


#### Line graph: Total debt per region (2000-2019)
The 3 line graphs were all created with `plotly`. I wanted to examine how debt levels changed over time from 2000-2019. After cleaning the data and mutating a variable that coded for the debtor/creditor's world region (by matching their names using `dplyr::case_when`), I then aggregated the total debt levels per region and plotted them over time. 


#### Line graph: Mean debt per region (2000-2019)
Same process as above, calculating mean debt per region. This was to account for the different group sizes across regions (e.g. there are twice as many debtor countries in Africa compared to Asia). 


#### Line graph: Total lending per creditor (2000-2019)
Same process as above, this time aggregating total lending per creditor. I narrowed it down to the top 15 creditors in 2019 (so as not to clutter the graph). 


#### Interactive Pie charts: Break down of top creditors (2000 vs 2019)
I wanted to see how the composition of top creditors compared between 2000 vs 2019. I first aggregated the total lending per creditor and then selected the top 20 (separately for 2000 and 2019). Using `highcharter`, I plotted the interactive pie charts according to the proportion of lending per creditor. 


#### Network: Debtors and creditors (2019)
Here, I wanted to visualize the network of debtors and creditors to see if there were any patterns, e.g. if debtor and creditor countries tend to borrow/lend in the same world region. Using data from 2019, I created the `nodes` dataframe by aggregating total debt/lending levels per entity and then mutating the region variable. The size of each node was equivalent to their total debt levels. For `links`, the size of each link was the amount of debt between that debtor and creditor link. After some more data cleaning (e.g. zero-indexing), I then used `networkD3::forceNetwork` to visualize the network, grouped by region. I also added a `clickAction` which displays information about the node - name, debtor/creditor status, region and debt levels.

## Apendix

#### Interactive Leaflet Choropleth: Interactive map of State Debt Levels
To create another option for visualization we created a interactive state choropleth. I used the original state debt statistics and attached it to a shape file. A pop up was attached with the name of the state, level of the states debt, and the 2020 credit rating of the state. For the credit rating data I web scraped the information off of the internet and attached it to the main data set. I set up the leaflet coded while using geocode to find the proper "setView" setting and zoom. 

Credit Rating Source: S&P
https://www.spglobal.com/ratings/en/research/articles/190319-u-s-state-ratings-and-outlooks-current-list-1738758
