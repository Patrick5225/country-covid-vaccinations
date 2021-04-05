<img width = 1000 height = 250 src="images/covid19_vaccine_header.jpeg">

# About
This is a data analytics consulting project that imitates data consulting work in a business environment. This project was not done alone; instead it was worked on with a team of 5 members. As a team, our goal is to deliver a business solution to a client by understanding and researching the client's problem that was given to our team and then coming up with a solution using analytical tools such as Excel, SQL, Tableau, and Python. The project experience involves solving problems, collecting external data, cleaning and analyzing data, meetings, research, deadlines, and presentations to present our findings to our client.

For this particular project, our client is a vaccine manufacturer distributor who needs help deciding which country to rollout their COVID-19 vaccinations to next, in a data-driven approach.

# Basic Overview
Coronavirus disease (COVID-19) is a contagious disease that has affected millions of people across many countries worldwide. To combat this disease, COVID-19 vaccines have been created and distributed to people living in different countries. However, the vaccines are currently in limited supply, and hence not every country has immediate access to the vaccines. The question to be solved then is:

**Question:** Which country should receive the next rollout of COVID-19 vaccinations, in a data-driven approach?

This approach involves analyzing vaccination data that contains information about the daily and total amount of vaccinations for each vaccinated country (as of March 2021), as well as collecting external datasets to backup our reasoning for choosing our recommendation.

# Data Used
**Daily and Total COVID-19 Vaccinations by Country (as of March 2021):** https://www.kaggle.com/gpreda/covid-world-vaccination-progress</br>
**Country Demographics:** https://ourworldindata.org/coronavirus</br>
**Country Coordinates (latitude and longitude):** https://developers.google.com/public-data/docs/canonical/countries_csv</br>
**Logistics Performance Index (LPI):** https://datacatalog.worldbank.org/dataset/logistics-performance-index</br>

# Methodology
The main idea of choosing the best country to rollout the COVID-19 vaccinations is to get variables that would best represent the cost-effectiveness of each country, and then summarize each variable through specific weights. By summarizing variables with specific weights, we obtain a score from 0.1 - 1.0 for every country, where countries with the highest scores determine which would be the most cost-effective countries to rollout the vaccinations.

The calculation for scoring each country is to multiply each numerical variable by their respective weights, and then take the sum of each product that will add up to a final score.

<img width="681" src="https://user-images.githubusercontent.com/32801046/113540519-28aca180-9595-11eb-8e43-160e12d15012.png">

The top 5 countries (that haven't been vaccinated yet) with the highest final scores are:

| Country | Vaccination Efficiency | Population | LPI | Final Score | Sensitivity (15%)
| --- | --- | --- | --- | --- | --- | 
| Vietnam | 0.1 | 1.0 | 0.9 | 0.62 | 0.54-0.62 | 
| Taiwan | 0.2 | 0.8 | 1.0 | 0.60 | 0.53-0.60 | 
| Iraq | 0.5 | 0.9 | 0.2 | 0.60 | 0.60-0.65 | 
| Kenya | 0.5 | 0.9 | 0.6 | 0.60 | 0.56-0.60 | 
| Togo | 0.6 | 0.7 | 0.4 | 0.60 | 0.60-0.62 | 

The final scores was calculated based on vaccination efficiency (daily vaccination rate), population, and Logistics Performance Index (LPI). The higher the value of a certain variable is, the higher the score is. Weights were given to each variable so that one variable could have more of an impact to the final score than other variables. The weights assigned to each variable was 40% to both vaccination efficiency and population, and 20% to LPI. Thus, vaccination efficiency and population will effect the final score more than LPI.

However, rather than quickly jumping to the conclusion that we should choose Vietnam because it has the highest final score, it should be noted that there is still uncertainty in the results of the machine learning model that was used to calculate the final scores. To get a better representation of final scores, we use sensitivity analysis as a "what-if" analysis to check how sensitive the final scores are if there were changes in the input variables (vaccination effiency, population, and LPI). This will help assess the consistency of the final scores under different assumptions. As a result of using sensitivity analysis, Iraq has the best acceptable final score range of 0.60-0.65, which is more consistent than Vietnam's range of 0.54-0.62.


# Results

Based on the final score and sensitivity ranges, we conclude that Iraq should be the next country to receive the rollout of COVID-19 vaccinations. Taking a closer look into the population and predicted vaccinations of Iraq, it is expected that on average, Iraq will have about 180,000 people vaccinated per day. With a population of 40.2 million people, we expect that 70% of the country's population will be vaccinated in 150 days from the first day they receive the vaccinations, and that the entire country will be vaccinated in 300 days.

| Country | Expected Vaccines per Day | Population | Expected Duration of Rollout (70%) | 
| --- | --- | --- | --- | 
| Iraq | 180,000 | 40.2M | 150-300 Days | 

<img src = "https://user-images.githubusercontent.com/32801046/113507830-97401f80-9501-11eb-9fd8-dd005b5feca5.png" height=250 width=250>
