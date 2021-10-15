## 1. Documentation
### 1.1 Motivation
*Motivation for data context*

The aim of this paper is to collect data regarding theatrical movies, to answer the following research question: *What is the impact of Covid-19 on the film industry?*
Therefore, a dataset containing data of movies before, during and after the pandemic will be created (2015 until 2020). 
This will be valuable to compare different kinds of variables relating to the film industry during this time period and to get some new insights on what kind of impact Covid-19 
had, e.g. were there changes in revenues?  
As other datasets only have data about one specific year, this dataset has been merged to one combined dataset containing data of multiple years. 

*Motivation for choice website/API*

The following three websites have been assessed containing relevant data, regarding the reseach question:
<ol>
<li>First website: https://www.boxofficemojo.com/</li>
<li>Second website: https://www.rottentomatoes.com/top</li>
<li>Third website: https://www.the-numbers.com/</li>
</ol>
<p> All three websites show available data about movies, which is the first step to make the websites comparable to each other.  
Furthermore, all kind of data can be retrieved per movie, for example revenue in a specific year, genres, runtime, distibutor etc. The websites distribute enough data to fit the 
research and moreover, the data can be specified in variables to make it usefull for this research. </p>

<p> Comparing the websites with each other, the website of https://www.boxofficemojo.com stands out in terms of data availability about the movies. 
First, the data on https://www.boxofficemojo.com provides a simple overview of the top 200 movies based on revenue for a specific year. 
This is in contrast with the website https://www.rottentomatoes.com/top, which only gives an overview of the title of the top 100 movies based on the number of written reviews, 
which does not fit the research really well.
The third website https://www.the-numbers.com, also gives an overview of movies ranked on revenue, actually not only the top 200 but every released movie in a specific year.
However, the problem with https://www.the-numbers.com is that the revenues are based on the Domestic Theatrical Market performance (North American movie territory) only, which 
makes the data useless for this research. 
While this research looks for the global impact of Covid-19 on the movie industry. </p>

<p> Therefore, data will be scraped from https://www.boxofficemojo.com. </p> 



### 1.2 Composition

**What do the instances that comprise the dataset represent?**

The instances that comprise the dataset represent film titles, IMDB ranking, corresponding revenues made in- and outside the USA and worldwide. Revenues inside the USA and revenues outside the USA will also be given in percentages of the total revenues. 

**Does the dataset contain all possible instances or is it a sample of instances from a larger set?**

No, the dataset is limited to the 50 films with the most revenue per year. This means that for the year 2015 until the year 2021, films will be scraped based on the amount of revenue. The number of 50 is based on the tradeoff between having enough data to do analyses on, while keeping the amount of data being scraped low enough so that the scraping will not lead to errors.

**What data does each instance consist of?**
<ol>
<li>"Ranking": review number from 1 to 10
<li>"Movie": name of the film
<li>"Worldwide": amount of worldwide revenue
<li>"Domestic": amount of revenues made in the USA
<li>"%-Domestic": percentage of revenues made in the USA 
<li>"Foreign": amount of revenues made outside the USA
<li>"%-Foreign": percentage of revenues made outside the USA
</ol>

**Is any information missing from individual instances?**

Yes, ..............

**Are there any errors, sources of noise, or redundancies in the
dataset?**

There's a possibility that there could be duplicates in the dataset. The data on the websites where the data is scraped gets updated daily, and it might occur that a film on one website gets a different (exact) name as the same film on another website. 

**Is the dataset self-contained, or does it link to or otherwise rely on
external resources?**

The dataset relies on the [IMDB](https://www.imdb.com/?ref_=helpms_helphdr_cons)-website and the [BoxOfficeMojo](https://www.boxofficemojo.com/?ref_=bo_nb_tt_mojologo)-website. This means that the data that is being scraped gets daily updated on the website and could therefore change. There's, thus, no archive of the exact data at a specific point in time. 



## **Collection process**

**How was the data associated with each instance acquired?**
The film names and the revenues are acquired directly via [Box Office Mojo Worldwide page](https://www.boxofficemojo.com/year/world/?ref_=bo_nb_hm_tab). The ratings are provided via [IMDB](https://www.imdb.com/). Also the ratings were directly observable via webscraping. 

**What mechanisms were used to collect the data?**
For the collection we used Jupyter Notebook running on Python. 

**Who were involved in the data collection process?**
The data collection was done by four students from Tilburg University for the class [Online Data Collection & Management](https://odcm.hannesdatta.com/)

## 1.5.		Uses

**Has the dataset been used for any tasks already? If so, please provide a description.**

The dataset we created based on scraping data from the box office mojo and Imdb websites  has not been used for any tasks so far. The idea is to look for the impact of Covid-19 on the movie industry. In which we want to compare the revenues of movies across years. This can be done by calculating the average revenue per year, so that we can compare year by year. Or the dataset might be specified into more de-tail, where we only compare the revenues of the top 5 movies across the years. 

**Is there a repository that links to any or all papers or systems that use the dataset? If so, please provide a link or other access point**

We used a repository on Github : https://github.com/Albirizzu/oDCM_team8.git
*What (other) tasks could the dataset be used for?*
The dataset now mainly focusses on the revenues produced per movie. This revenues will be compared over a couple of years to look for the impact of Covid-19. 

However, the task can be extended to analyze the growth curve of revenues made in the movie indus-try. Whether this effect is exponential or linear over the last couple of years. 

Also, an analysis on the effect of review ratings on the revenues can be done. A linear regression based on these two variables can be done to search for a correlation. 

Finally, besides the total market revenue the dataset also data on the domestic theatrical market revenue ( USA). Based on this data we could compare how well the USA did compared to the world in generating revenue for a movie. 

**Is there anything about the composition of the da-taset or the way it was collected and prepro-cessed/cleaned/labeled that might impact future uses? For example, is there anything that a future user might need to know to avoid uses that could result in unfair treat-ment of individuals or groups (e.g., stereotyping, quality of service issues) or other undesirable harms (e.g., finan-cial harms, legal risks) If so, please provide a description. Is there anything a future user could do to mitigate these undesirable harms?**

The composition of the data set is now based on the top 50 movies based on their revenue. So this has to be kept in mind for the future, to keep the composi-tion based on the top 50 based and doesn’t change it to the top 100 or top 200. 
Also the possibilities of unforeseen errors in the initial dataset by data that has been updated over the time can have their effect on future users. As these errors might be included whenever the data has been up-dated it will lead to un-valid conclusions. 

**Are there tasks for which the dataset should not be used? If so, please provide a description**

There are no tasks for which the dataset should not be used based on any legal or ethical concerns. 
