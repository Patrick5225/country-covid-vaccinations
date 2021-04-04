<img width = 1000 height = 250 src="images/covid19_vaccine_header.jpeg">

# About
This is a data analytics consulting project that imitates data consulting work in a business environment. This project was not done alone; instead it was worked on with a team of 5 members. As a team, our goal is to deliver a business solution to a client by understanding and researching the client's problem that was given to our team and then coming up with a solution using analytical tools such as Excel, SQL, Tableau, and Python. The project experience involves solving problems, collecting external data, cleaning and analyzing data, meetings, research, deadlines, and presentations to present our findings to our client.

For this particular project, our client is a vaccine manufacturer distributor who needs help deciding which country to rollout their COVID-19 vaccinations to next, in a data-driven approach.

# Basic Overview
Coronavirus disease (COVID-19) is a contagious disease that has affected millions of people across many countries worldwide. To combat this disease, COVID-19 vaccines have been created and distributed to people living in different countries. However, the vaccines are currently in limited supply, and hence not every country has immediate access to the vaccines. The question to be solved then is:

**Question:** Which country should receive the next rollout of COVID-19 vaccinations, in a data-driven approach?

This approach involves analyzing country vaccination data that contains information about the daily and total amount of vaccinations for COVID-19 (as of March 2021), as well as collecting external datasets to backup our reasoning for choosing our recommendation.

# Data Used
**Daily and Total COVID-19 Vaccinations by Country (as of March 2021):** https://www.kaggle.com/gpreda/covid-world-vaccination-progress</br>
**Country Demographics:** https://ourworldindata.org/coronavirus</br>
**Country Coordinates (latitude and longitude):** https://developers.google.com/public-data/docs/canonical/countries_csv</br>
**Logistics Performance Index (LPI):** https://datacatalog.worldbank.org/dataset/logistics-performance-index</br>

# Results
_For the reasoning behind the main idea of choosing the best countries to rollout the vaccinations, check out the methodlogy section below._

The top 5 countries (that haven't been vaccinated yet) with the highest final scores are:

| Country | Vaccination Efficiency | Population | LPI | Final Score | Sensitivity (15%)
| --- | --- | --- | --- | --- | --- | 
| Iraq | 0.5 | 0.9 | 0.6 | 0.68 | 0.66-0.69 | 
| Togo | 0.6 | 0.7 | 0.7 | 0.66 | 0.65-0.66 | 
| Tajikistan | 0.6 | 0.7 | 0.7 | 0.66 | 0.65-0.66 | 
| Brunei | 0.9 | 0.3 | 0.8 | 0.64 | 0.62-0.68 | 
| Sao Tome and Principe | 1.0 | 0.2 | 0.8 | 0.64 | 0.62-0.69 | 

Based on the final score and sensitivity ranges, we conclude that Iraq should be the next country to receive the rollout of COVID-19 vaccinations. Taking a closer look into the population and predicted vaccinations of Iraq, it is expected that on average, Iraq will have about 180,000 people vaccinated per day. With a population of 40.2 million people, we expect that 70% of the country's population will be vaccinated in 150 days from the first day they receive the vaccinations, and that the entire country will be vaccinated in 300 days.

| Country | Expected Vaccines per Day | Population | Expected Duration of Rollout (70%) | 
| --- | --- | --- | --- | 
| Iraq | 180,000 | 40.2M | 150-300 Days | 

<img src = "https://user-images.githubusercontent.com/32801046/113507830-97401f80-9501-11eb-9fd8-dd005b5feca5.png" height=250 width=250>

