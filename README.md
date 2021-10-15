## 1. Documentation
### 1.1 Motivation

**For what purpose was the dataset created? Was there a specific task in mind? Was there a specific gap that need-ed to be filled? Please provide a description. **

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
*Entities, linkages, timeframe and algorithmic biases*

**What do the instances that comprise the dataset represent?**

The instances that comprise the dataset represent film titles, corresponding revenues and the IMDB review of the film.

**Does the dataset contain all possible instances or is it a sample of instances from a larger set?**

No, the data set is limited to the 50 films with the most revenue per year. This means that for the year 2015 until the year 2021, films will be scraped based on the amount of revenue. The number of 50 is based on the tradeoff between having enough data to do analyses on, while keeping the amount of data being scraped low enough so that the scraping will not lead to errors.

**What data does each instance consist of?**

Review: ranking from 1 to 10.
Revenue: Number of dollars.
Film title: Character



For every movie the dataset contain a related revenue, which will be an indicator on how the revenues of movies for a specific year were. Furthermore, the data will be provided in IMDB ratings if the rating is available to the corresponding movie. In total the dataset has three instances, mentioned above, all three are considered as features. The data of each instance represents a measurable piece of data, which can be seen as a variable. The revenues and ratings are linked to a specific movie title, where movie titles can be linked to the year of release. This makes the data comparable over the years. All the available data has been scraped, resulting in a dataset of 200 movies for each year with corresponding revenues and ratings. The dataset will compare movies released from 2015 until 2021, to get an insight on the impact of Covid-19 on the film industry. 

*Sampling, construct measurement and data structure *





*Length:* an amount of three instances.

*Amount:* all the data that was available is scraped. So for each year, there are 200 films with corresponding revenues and ratings. 

*Missing information:* 

*Explicitness:* 

*Level of self-containment:* The provided data relies on an external source, namely the [Box Office Mojo website](https://www.boxofficemojo.com/). Because the website gets updated regurlarly, users should notice that the data will change over time. 

## **Collection process**

**How was the data associated with each instance acquired?**
The film names and the revenues are acquired directly via [Box Office Mojo Worldwide page](https://www.boxofficemojo.com/year/world/?ref_=bo_nb_hm_tab). The ratings are provided via [IMDB](https://www.imdb.com/). Also the ratings were directly observable via webscraping. 

**What mechanisms were used to collect the data?**
For the collection we used Jupyter Notebook running on Python. 

**Who were involved in the data collection process?**
The data collection was done by four students from Tilburg University for the class [Online Data Collection & Management](https://odcm.hannesdatta.com/)


## 5.		Uses

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
Also the possibilities of unforeseen errors in the initial dataset can have their effect on future users. As these errors might be included it will lead to un-valid con-clussions. 

**Are there tasks for which the dataset should not be used? If so, please provide a description**

There are no tasks for which the dataset should not be used based on any legal or ethical concerns. 




