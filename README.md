# Examining Determinants of Opioid Mortality
## Introduction
According to most sources, the "Opioid Epidemic" got its start around the early 1990s and gained traction in the mid-1990s. Opioid drugs are meant to be prescribed to people dealing with severe and chronic pain. Despite its effectiveness as a painkiller, it is a highly addictive substance. The terms "Opioid Epidemic" and "Opioid Crisis" were termed because of the drastic increase in opioid-related deaths, including overdoses and suicide. Our team is interested in the determinants of opioid related-mortality rates. We used public datasets to explore this question, looking at regional, demographic, and economic factors. 

## Research Questions
-What demographics are susceptible to higher rates of opioid mortality?

-Is the opioid crisis region/state specific?

-Is there a relationship between poverty and the amount of opioid related-deaths?

-Has access to prescription opioids shaped the current wave of the opioid crisis?

## Data Acquisition

Demographic data from The Home of the US Government's Open Data website, Data.gov: [Demographic data](https://catalog.data.gov/dataset/drug-overdose-death-rates-by-drug-type-sex-age-race-and-hispanic-origin-united-states-3f72f)

Drug prescription data by state and year from "Data.Medicaid.gov": [Prescription data](https://data.medicaid.gov/datasets?fulltext=State%20Drug%20Utilization%20Data)

Economic Research Service (USDA)**: [USDA Data](https://data.ers.usda.gov/reports.aspx?ID=17826)

CDC Injury Center: [Geographic data](https://www.kaggle.com/datasets/craigchilvers/opioids-in-the-us-cdc-drug-overdose-deaths)

## Data Exploration and Clean Up
Multiple datasets related to opioid mortality, demographic, socioeconomic and geographic factors were used in this study. All datasets were acquired as .csv files. API keys were not available on the websites where we obtained our data. Once obtained, subsets of the data, pertinent to our research, were isolated (i.e. overall opioid overdose deaths with a focus on synthetic opioids). Once the datasets were filtered to the key subject matter, a variety of line plots, bar plots, and heatmaps were used to visualize different trends ranging from 1991 to 2023.

### Sample Code
The first dataset was broken down to look at the percentage of people living in poverty for individual states. By doing this, the dataframe only shows relevant information.

     *df = df[['state_National', 'total_est_pct2']] df = df.dropna(inplace=False)*
     
To show this information for every state, a heat map was created from the dataframe.

     *fig = px.choropleth(df, locations='Abbreviation', locationmode="USA-states", color='total_est_pct2', scope="usa", color_continuous_scale="YlOrRd", # or any other color scale title=" % of Sates Population in Poverty")*
     *fig.show()*
     
![Opioid Deaths by Poverty](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Output/state_poverty_map.png)


## Data Analysis

In order to get a better understanding of the impacts of synthetic opioids to the US population, the line plot below was created to be able to visually compare the overall opioid death rates to the death rates attributed solely to synthetic opioids, including Fentanyl.  As shown, the trends between the 'All Opioids' and the 'Other Synthetics' lines show similar increasing directionality beginning in 2013 on forward.

![Opioid Deaths by Drug](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Output/rate_by_synth1.png)



To examine the percentage of people in poverty per individual state, a bar graph was generated. To condense the information, this only showed the top 10 states with the highest percentage of poverty. A similar bar graph was made, showing the top ten states with the highest opioid-related deaths per 100k people (these graphs can be found in the powerpoint slides and jupyter notebook). The graph below summarizes the two, allowing for a comparison of state poverty and opioid-related deaths.

![Opioid Deaths by Poverty](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Output/poverty_vs_deaths.png)



Exploring geographic factors, bar charts showing overdose rates by state for 2013 and 2019 were generated. These showed an increasing trend for overdose rates. A correlation plot on population density and overdose rates, showed population density to be a more strongly correlated factor in 2019 than in 2013. Another correlation plot showed that poverty became less highly correlated in that same time frame (the bar charts and correlation plot for poverty can be found in the slides and jupyter notebook).

![Opioid Deaths by Population](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Output/Pop_density2019.png)



Has the prescription of opioid drugs influenced the increase in opioid deaths? Drug prescription data "Data.Medicaid.gov" was used to quantify the amount of 4 prescription opioids (fentanyl, morphine, oxycodone, and hydrocodone), which was delineated by state and year. From 1991 to 2023 there was an increase in fentanyl prescriptions and a less drastic increase in morphine prescriptions. This is shown in a line plot, aggregating data from all 50 states, and heatmaps depicting the changes in prescription rates by state (heatmaps can be located in powerpoint slides and jupyter notebook). Trends in Medicaid reimbursement rates were also explored from the same dataset but no significant trends were found that were relevant to our story. Medicaid reimbursement was ruled out as a determinant of opioid related-mortality rates. 

![Opioid Deaths by Prescriptions](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Output/Country_Level_Trends_in_Opioid_Prescriptions.png)


## Result Summary
By 2018, the impacts of opioid overdose deaths was more prominent with men than women, with the ratio of death rates of men to women was 2.23.
The three most highly impacted age groups by opioid overdose deaths were, in descending order, 25 to 34 year olds, 35 to 44 year olds, and 45 to 54 year olds with death rates per 100k of 28.1, 27.7, and 23.0, respectively. For perspective, the overall average death rate for 2018 was 14.3.

There was no obvious trend between poverty rates and opioid-related mortality. However, the top ten states with the highest opioid-related deaths aligns with the results seen in the geographic portion of our research.
Overdose rates increased from 2013 to 2019, as seen on the Overdose vs State bar graphs. Of particular decline and intensity were Appalachia and the surrounding areas, including West Virginia, Delaware, Pennsylvania, Ohio and West Virginia. 

Overall trends for prescription opioid rates fits in with the rest of the data and aligns with the trends seen in Appalachia. The amount of fentanyl prescribed by health professional increased over the period from 1991 to 2023, leveling off on the same level as oxycodone, hydrocodone and morphine around 2009 (For the years 1991 and 1995, either little to no fentanyl was being prescribed or for various reasons was not being recorded by medical professionals). This trend of fentanyl, along with a less drastic increase in the prescription of morphine, precedes the rise in opioid-related deaths starting in the early 2000s. Visualizing these trends by state (in the heatmaps) supports the geographic region as being the major determinant of opioid related-deaths. States with the highest prescription rates of fentanyl and morphine overlap with those having high overdose rates in Appalachia.

## Conclusion
The major determinants of opioid related-mortality was geographic region and demographics. While drug prescription and poverty rates were not strong indicators of drug-related deaths, both datasets support geographic region as being the most impactful factor in opioid mortality.

## Limitations & Further Studies
(1) Overall, the data shows that a male using opioids, especially synthetics such as fentanyl, between the ages of 25 to 44 years old in the US is more highly susceptible to overdosing as compared to the overall population. One key limitation to the dataset analyzed is that it does not segregate race and ethnicity as its own demographic factor, as it was only included as a subset of either age or gender.  The ability to analyze the data solely on race and ethnicity could provide a separate view that may broaden the understanding of the impacts of opioids on those particular segments of the population.  This provides an opportunity to further understand why the data was organized in this manner and potentially locate a data source that does provide this information for further analysis. (2) While the trend of drug prescription appears to be a precursor to the opioid death rate, no direct causation can be shown with our data. Further studies would look into which opioids people were dying from (illicit or prescribed). The possible link between overprescription of fentanyl and opioid-related mortality should incentivize medical professionals and pharmaceutical scientists to find a less addictive medication for people dealing with chronic and severe pain. (3) No overlap was found with the poverty rate and opioid-related deaths, however parsing the data by household income would provide a better opportunity to understand the impacts of finances on death rate. (4) The CDC dataset doesn’t capture newer data after 2019, especially the Covid 19 pandemic which saw an increase in death rates due to opioid use.

## File Locations
- Code: [Jupyter Notebook](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Determinants%20of%20Opioid%20Mortality.ipynb)
- Presentation: [Examining Determinants of Opioid Mortality](https://github.com/NefertitiM/Determinants-of-Opioid-Mortality/blob/main/Examining%20Determinants%20of%20Opioid%20Mortality.pdf)
