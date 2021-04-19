# Process Book

Members: Luke Artola, Samantha Li, Yun Yee Tan

## Topic
Debt 


# Visualizations

## US

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
