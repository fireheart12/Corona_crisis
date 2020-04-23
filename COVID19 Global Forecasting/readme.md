# COVID-19 Global Forecasting 

![Coronavirus](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/COVID-19.jpg)

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

  Using Pandas library the datasets are read and subsequently converted into dataframes, for easier Exploratory Data Analysis(EDA) and     data pre-processing. 

* **3. Fill the missing values** :

  Using *pandas.fillna()* function, the missing values in the dataframe are replaced by the chosen values.
   * Empty values in Provinces column are assigned to NULL value.
   * Empty values in Confirmed cases column are assigned the value NULL.
   * Empty values in Fatalities case column are also assigned NULL value.

* **4. Grouping cases together** :

    Since we have been given a time-series data of various countries around the world, corresponding to the number of confirmed cases       and fatalities observed, we aim to ouput the total number of confirmed cases and fatalities observed on various dates in a               particular country/region. This is accomplished in the dataframe using *groupby()* function available in Pandas library. 

* **5. Plotting country wise results** :
    
    Now that we have extracted the confirmed cases as well as fatality count according to dates, for each country in the dataframe; step     two is initiated where *matplotlib* is used in order to plot these counts over time. To enable comparitive study, counts of some         countries are plotted against each other. Here I have plotted the counts of the following countries : 
    
     * The United States of America
     * Italy
     * Republic of India
     * France
     * China
     * Taiwan
     * The United Kingdom
    
    ![A comparitive study of confirmed cases across the globe](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/Comparitive%20study%20-%20Confirmed%20cases.png)
    
    ![A comparitive study of fatal cases across the globe](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/Comparitive%20study%20-%20Fatal%20cases.png)
    
* **6. Combining country and provinces into region** :
    
    In this section, *Country_Region* and *Province_State* is combined under one header, that is *Region*. Subsequently, the                 Country_Region and Province_State column is removed in order to combine two features into a single feature. This feature pre-           processing aids us in effectively summing the essence of two features into one, simultaneously narrowing down the dimesional             structure of the feature matrix fed to the deep neural networks.
    
* **7. Data Exploration via Choropleth maps** : 
   
    Choropleth maps are popular maps used to represent statistical data through various shading patterns or symbols on                       predetermined geographic areas (i.e. countries). They are good at utilizing data to easily represent variability of the desired         measurement, across a region. Since we are given the data of various countries, Exploratory Data Analysis(EDA) via choropleth maps       seems a suitable option.
    
    In order to accomplish this, we employ the *choropleth()* function incorporated in the *plotly.express* module. Two Choropleth maps     were plotted in order to depict the **global growth** of the coronavirus pandemic.
    Down below are the snapshots in order of :
     * Globally confirmed COVID-19 cases in January, taken at timestamp 0 in the generated choropleth map.
     * Globally cofirmed COVID-19 cases in April, taken at the final timestamp in April, in the generated choropleth map.
     * Globally fatal COVID-19 cases in January, taken at timestamp 0 in the generated choropleth map.
     * Globally fatal COVID-19 cases in April, taken at the final timestamp in April, in the generated choropleth map.
        
    ![Global Confirmed Cases in January](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/Global%20Confirmed%20Cases%20in%20January.png?raw=true "Optional Title")
        
    ![](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/Global%20Confirmed%20Cases%20in%20April.png)
    
    
    ![](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/Global%20Fatal%20Cases%20in%20January.png)
    
    
    ![](https://github.com/CodingWitcher/Corona_crisis/blob/master/COVID19%20Global%20Forecasting/EDA%20Snapshots/Global%20Fatal%20cases%20in%20April.png)
    
   ```diff
   - Github can't support the display of Choropleth map or dynamic(race) graphs. Hence these outputs can only be truly visualized with the passage of time on these same notebooks committed on Kaggle platform.  
     
   - 1. Global forecast confirmed predicted cases Python Notebook ( https://www.kaggle.com/fireheart7/globalforecast-confirmedcases )
   - 2. Global forecast cumulative fatal cases Python3 notebook ( https://www.kaggle.com/fireheart7/globalforecast-fatalcases )
   ```

* **8. Generating a Race bar chart to compare the growth of COVID-19(EDA Phase 2)** : 

    


    
    
      









