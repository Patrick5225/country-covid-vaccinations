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
The main idea of choosing the best country to rollout the COVID-19 vaccinations is to get variables that would best represent the cost-effectiveness of each country, and then summarize each variable through specific weights. By summarizing variables with specific weights, we obtain a score from 0.0 - 1.0 for every country, where countries with the highest scores determine which would be the most cost-effective countries to rollout the vaccinations.

The calculation for scoring each country is to multiply each numerical variable by their respective weights, and then take the sum of each product that will add up to a final score.

<img width="681" src="https://user-images.githubusercontent.com/32801046/113540519-28aca180-9595-11eb-8e43-160e12d15012.png">

Initially, the variables that were chosen were Gross Domestic Product (GDP) per capita, Human Development Index (HDI), daily vaccination (vaccinations per day per population), population, distance (in meters) from the United States, and Logistics Performance Index (LPI). After discussion of the analyst team, we decided to choose the following variables with their corresponding weights:

<img width="443" alt="Screen Shot 2021-04-04 at 10 57 50 PM" src="https://user-images.githubusercontent.com/32801046/113542478-39f7ad00-9599-11eb-8e42-e6647a79fc6d.png">

_Note: There was a moderately positive correlation observed between daily vaccination with HDI and GDP, so this is why we did not include HDI and GDP as one of the main variables._

Hence, the final scores was calculated based on vaccination efficiency (daily vaccination), population, and LPI. The higher the value of a certain variable is, the higher the score is. Weights were given to each variable so that one variable could have more of an impact to the final score than other variables. The weights assigned to each variable was 40% to both vaccination efficiency and population, and 20% to LPI. Thus, vaccination efficiency and population will effect the final score more than LPI.

Most of the variables, such as population, were available and collected through public datasets online. However, daily vaccination is more complex and difficult to retrieve. There were only a limited amount of daily vaccinations that were available online for vaccinated countries, so data was cleaned that would give the best estimates of daily vaccinations for each vaccinated country. For non-vaccinated countries, because the countries that have not been vaccinated yet, a predictive model was built in Python to predict the expected daily vaccinations. Check out the Jupyter Notebook [Predicting daily vaccines and Scores.ipynb](https://github.com/Patrick5225/country-covid-vaccinations/blob/main/scoring/Predicting%20daily%20vaccines%20and%20Scores.ipynb) in the scoring folder to see how the predictive model was created and how final scores were calculated for each country.

# Results

The top 5 countries (that haven't been vaccinated yet) with the highest final scores are:

| Country | Vaccination Efficiency | Population | LPI | Final Score | Sensitivity (15%)
| --- | --- | --- | --- | --- | --- | 
| Vietnam | 0.1 | 1.0 | 0.9 | 0.62 | 0.54-0.62 | 
| Taiwan | 0.2 | 0.8 | 1.0 | 0.60 | 0.53-0.60 | 
| Iraq | 0.5 | 0.9 | 0.2 | 0.60 | 0.60-0.65 | 
| Kenya | 0.5 | 0.9 | 0.6 | 0.60 | 0.56-0.60 | 
| Togo | 0.6 | 0.7 | 0.4 | 0.60 | 0.60-0.62 | 

However, rather than quickly jumping to the conclusion that we should choose Vietnam because it has the highest final score, it should be noted that there is still uncertainty in the results of the machine learning model that was used to calculate the final scores. To get a better representation of final scores, we use sensitivity analysis as a "what-if" analysis to check how sensitive the final scores are if there were changes in the input variables (vaccination effiency, population, and LPI). This will help assess the consistency of the final scores under different assumptions. As a result of using sensitivity analysis, Iraq has the best acceptable final score range of 0.60-0.65, which is more consistent than Vietnam's range of 0.54-0.62.


# Conclusion

Based on the final score and sensitivity ranges, we conclude that Iraq should be the next country to receive the rollout of COVID-19 vaccinations. Taking a closer look into the population and predicted vaccinations of Iraq, it is expected that on average, Iraq will have about 180,000 people vaccinated per day. With a population of 40.2 million people, we expect that 70% of the country's population will be vaccinated in 150 days from the first day they receive the vaccinations, and that the entire country will be vaccinated in 300 days.

| Country | Expected Vaccines per Day | Population | Expected Duration of Rollout (70%) | 
| --- | --- | --- | --- | 
| Iraq | 180,000 | 40.2M | 150-300 Days | 

<img src = "https://user-images.githubusercontent.com/32801046/113507830-97401f80-9501-11eb-9fd8-dd005b5feca5.png" height=250 width=250>
