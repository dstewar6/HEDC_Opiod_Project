# HEDC_Opiod_Project
File "dstewart_hedc_work.ipynb" details how to calculate the MME per population and plot the MME/pop per county trend across the years after merging ARCOS data with pop estimates data for NY State and Ind State. It also shows how to calculate the descriptive summaries of the drugs of interests before and after I-STOP law goes into effect.

In file "Getting directionality of change in mme/pop of counties.ipynb", we are processing the ARCOS data to get total mme per each transaction. We then add up total mme per month for each county. We merge the ARCOS data with census data to help account for population changes within each county over time. We then test each county via Chow test and adjust p-values to account for multiple tests. This script then outputs a csv file with county names and associated outcome variables, including direction of change, mean mme before and after, and percentage of change in mme.

In file "creating county map.ipynb", we generate a map of New York Counties, color coded based on whether these counties have increased, decreased, or not changed in total mme per person after I-STOP became effective (August 2013).

In file "Fitting logit w/ SMOTE.ipynb", we merge our dataframe with outcome variables (change in mme before and after August 2013) with the County Health Rankings database from University of Wisconsin Population Health Institute (linked here: https://www.countyhealthrankings.org/health-data/new-york/data-and-resources). As the number of features in comparison to observations is large, we apply recursive feature elimination to select for the most predictive variables and avoid overfitting our model. As there is an imbalance in outcomes within our dataset (41 counties decreased vs 9 increased), we also have applied synthetic minority oversampling technique when training the model. We have also generated an ROC and classification matrix to help evaluate performance of the model in this script.

In file "Arima_model (9).ipynb", we create a SARIMA model testing against the null hypothesis that there is no change in opioid transactions before and after August 2013. We compare forecasted seasonal arima values to actual values shows that there is a significant difference in these drugs due to the implementation of the law, especially oxycodone. The data was differenced once to account for stationarity. P values, T values, and RMSE values were also calculated.

Data "indiana_pop_estimates.csv" and "ny county pop estimates + fips.csv" have been uploaded for convenience as we manipulated these files from the Census Bureau to contain only the county names and pop estimates.
Data 'county health data 2013.csv' has also been uploaded for convience as we manipulated these files to assemble many separate csv files in one spreadsheet.
Data 'county_directions_percentagechanges.csv' has been used as a starting point for the 'fitting multiple logistic regression' script so we have uploaded it for convenience as well.


