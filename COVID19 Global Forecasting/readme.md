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

* **covid-19-eda.ipynb** : A notebook where Exploratory Data Analysis(EDA) is performed on the training data. 
* **globalforecast-confirmedcases.ipynb** : This notebook aims to predict the cumulative predicted confirmed cases for COVID-19, in the future all across the globe.
* **globalforecast-fatalcases.ipynb** : This notebook aims to predict the cumulative predicted fatal cases for COVID-19, in the future all across the globe.
* **Predicted_cases.csv** : The ouput(*predicted cumulative cases*) is exported as a .csv file and is uploaded here.
* **Predicted_Fatal_cases.csv** : The ouput(*predicted fatal cases*) is exported as a .csv file and is uploaded here.

## Notebook Design Structure

### globalforecast-confirmedcases.ipynb : 

* **1. Importing necessary Python3 modules** :
  * **Numpy** : NumPy(Numerical Python) is a python library used for working with arrays. It also has functions for working in domain of linear algebra, fourier transform, and matrices.
  * **Pandas** : Pandas is a Python package providing fast, flexible, and expressive data structures designed to make working with 'relationa' or 'labeled' data both easy and intuitive. It aims to be the fundamental high-level building block for doing practical, real world data analysis in Python.
  * **Matplotlib** : Matplotlib is a plotting library for the Python3 programming language.
  * **Plotly** : Like Matplotlib, Plotly is also a plotting library. The sole aim of importing it here was to make use of its submodule in order to create *choropleth* map for a visual global analysis later. 
  * **Bokeh** : Similarily, Bokeh is also an interactive visualization library for modern web browsers. We import this so that the *choropleth* visualization can be rendered on the committed Jupyter notebook, running on the Google Chrome or any other web browser.
  * **sklearn** : Scikit-learn provides a range of supervised and unsupervised learning algorithms via a consistent interface in Python. The library is focused on preprocessing/modeling data. It is not focused on loading, manipulating and summarizing data. For these features, we refer to NumPy and Pandas. 
  * **Tensorflow** : Is a deep learning framework encapsulating comprehensive, flexible ecosystem of tools, libraries and community resources that lets researchers push the state-of-the-art in ML, and developers easily build and deploy ML powered applications.

* **2. Loading the COVID-19 dataset** :

Using Pandas library the datasets are read and subsequently converted into dataframes, for easier Exploratory Data Analysis(EDA) and data pre-processing. 










