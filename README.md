## 1. Documentation
### 1.1 Motivation
*Motivation for data context*

The aim of this paper is to collect data regarding movies, to answer the following reserach question: *What is the impact of Covid-19 on the movie industry?*
Therefore, a dataset containing data before, during and after the pandemic will be created (2015 until 2020). 
This will be valuable to compare the movie industry during this time period and to get some new insights on what kind of impact Covid-19 had. 
As other datasets only have data about one specific year, this dataset has been merged to one dataset containing data of multiple years. 

*Motivation for choice website/API*


# **Composition**

The instances that comprise the dataset represent the titles of the films and the corresponding revenues that the film made in the cinemas. Furthermore will the data provide in IMDB ratings if the rating is available to the corresponding film. 

*Length:* an amount of three instances.

*Amount:* all the data that was available is scraped. So for each year, there are 200 films with corresponding revenues and ratings. 

*Missing information:* 

*Explicitness:* 

*Level of self-containment:* The provided data relies on an external source, namely the [Box Office Mojo website](https://www.boxofficemojo.com/). Because the website gets updated regurlarly, users should notice that the data will change over time. 

# **Collection process**

**How was the data associated with each instance acquired?**
The film names and the revenues are acquired directly via [Box Office Mojo Worldwide page](https://www.boxofficemojo.com/year/world/?ref_=bo_nb_hm_tab). The ratings are provided via [IMDB](https://www.imdb.com/). Also the ratings were directly observable via webscraping. 

**What mechanisms were used to collect the data?**
For the collection we used Jupyter Notebook running on Python. 

**Who were involved in the data collection process?**
The data collection was done by four students from Tilburg University for the class [Online Data Collection & Management](https://odcm.hannesdatta.com/)
