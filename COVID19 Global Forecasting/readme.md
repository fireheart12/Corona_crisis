# COVID-19 Global Forecasting 

Coronavirus disease (COVID-19) is an infectious disease caused by a newly discovered coronavirus. The virus that causes COVID-19 is mainly transmitted through droplets generated when an infected person coughs, sneezes, or exhales. These droplets are too heavy to hang in the air, and quickly fall on floors or surfaces. 
One can be infected by breathing in the virus if one is within close proximity of someone who has COVID-19, or by touching a contaminated surface and then your eyes, nose or mouth.

More information about this deadly virus(along with prevention tips and mandatory precautions) can be found on the World Health Organization(WHO)'s webpage. Other information resources are as follows:
* https://www.who.int/emergencies/diseases/novel-coronavirus-2019 
* https://www.google.com/intl/en_in/covid19/
* https://www.mygov.in/covid-19


In this project, I aim to predict not only the **cumulative number of confirmed COVID19 cases** but also the approximate **resulting fatalities** in various locations across the world. 

For analyzing this, the entire problem was evaluated using * Time - Series modeling* approach, by looking at the past data as reported from the month of January by John Hopkins University. The data set is uploaded in this project's sub directory itself. The same data set can also be found on the Kaggle platform itself : 
* https://www.kaggle.com/c/covid19-global-forecasting-week-4/data

All the *.ipynb* notebooks were created using Kaggle's Jupyter notebooks, and were executed using *NVidia K80 GPUs.*

## COVID-19 DATASET

As mentioned above, the dataset is made publically available(*credits : John Hopkins University*). Copy of the files are uploaded in this projecty's directory as well. The data set composes of the following files : 
* train.csv - the training data containing the cumulative predicted as well as fatal cases observed in the previous months, all across the globe.
* test.csv - the dates to predict. 

*For more information on how the data was collected, please visit :*

**https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series**  

## Notebooks 



