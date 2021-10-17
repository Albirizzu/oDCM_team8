## 1. Documentation
### 1.1 Motivation
**Motivation for data context**

The movie industry has taken a big hit due to the COVID-19 pandemic. During 2020 and 2021, movie theaters and cinemas have had to deal with various restrictions, such as a limited number of visitors, mandatory COVID-vaccination checks and closing down entirely.
The aim of this repository is to collect data regarding cinematic movies, to answer the following research question: *What is the impact of Covid-19 on boxoffice revenue?*
We will create a dataframe containing revenue data of movies before, during and after the pandemic (2015 until 2021) using Box Office Mojo. 
This will allow us to compare boxoffice revenues of the film industry during this time period and to get some new insights on the of impact Covid-19. There are several boxoffice revenue datasets available online (on e.g. Kaggle), however they are not up-to-date and focus on US revenue only. We believe our dataset will be of added value to the research community as there are no other datasets available focussing on this specific time period in a worldwide context. 
As a result of movie theaters closing down, many blockbusters decided to postpone their release. This might have led to a decrease in quality of the movies released during the pandamic. We will add IMDb ratings to the dataset to allow the research to compensate for movie quality. 
The latter also distinguishes this dataset from others, because it contains data about revenues as well as data about rankings. Furthermore is the data as up-to-date as possible when it is being scraped, because it uses the Box Office Mojo and IMDB websites for the data collection. When updates are published on the websites, the scraper is able to provide it into a dataset. This gives researchers the ability to work with accurate data. 

**Motivation for choice website/API**

The following three websites have been assessed containing relevant boxoffice data:
<ol>
<li>First website: https://www.boxofficemojo.com/</li>
<li>Second website: https://www.rottentomatoes.com/top</li>
<li>Third website: https://www.the-numbers.com/</li>
</ol>
<p> These three websites are somewhat comparable as the all show boxoffice data about movies.
Furthermore, different kinds of data can be retrieved per movie, for example revenue in a specific year, genres, runtime, distibutor etc. The websites distribute enough data to fit the 
research. </p>

<p> Comparing the websites with each other, the website of https://www.boxofficemojo.com stands out in terms of data availability about the movies. 
First, the data on https://www.boxofficemojo.com provides a simple overview of the top 200 movies based on revenue for a specific year. 
This is in contrast with the website https://www.rottentomatoes.com/top, which only gives an overview of the title of the top 100 movies based on the number of written reviews, 
which does not fit the research really well.
The third website https://www.the-numbers.com, also gives an overview of movies ranked on revenue for every released movie in a specific year.
However, the problem with https://www.the-numbers.com is that the revenues are based on the Domestic Theatrical Market performance (North American movie territory) only, which makes the data useless for this research. For this research looks for the global impact of Covid-19 on the movie industry. </p>

<p> Therefore, data will be scraped from https://www.boxofficemojo.com. </p> 

Concerning the IMDb data, there are several IMDb datasets available on https://www.imdb.com/interfaces/. The dataset containing information on ratings and votes uses unique IMDb id's to link movies to their corresponding IMDb user rating. As these IMDb id's are not available on Boxoffice Mojo we would not be able to merge the two dataframes together. We considered merging a dataset containing movie id's and movie titles with the dataset containing movie ratings. Eventually we decided against this as we feared in a dataset of this size there would be movies with the exact same title, resulting into movies being assigned the wrong rating.
To ensure the quality of our data, we decided to use a webscraper instead. An additional advantage of this is that as the COVID-19 pandemic is still ongoing, it is valuable for our data to be up to date.  

### 1.2 Composition

**What do the instances that comprise the dataset represent?**

The dataset comprises of the following instances scraped from Box Office Mojo: movie title, year of release, corresponding revenues made in- and outside the USA, and worldwide. Revenues inside the USA and revenues outside the USA will also be given in percentages of the total revenues. Additionally, movie titles and ratings are scraped from IMDb. We scrape the data from both Box Office Mojo and IMDb for movies released between 2015 and 2021. The Box Office Mojo and IMDb data are merged together based on movie titles. 

**Does the dataset contain all possible instances or is it a sample of instances from a larger set?**

Our dataset is based on the worldwide Box Office ranking from Box Office Mojo. This ranking does not contain all movies released each year but merely the top 200. 
This means that for the year 2015 until the year 2021, only movies within the top 200 best ranking worldwide boxoffice revenue will be scraped.

**What data does each instance consist of?**
<ol>
<li>"Ranking": ranking of movie in year of release based on worldwide boxoffice revenue
<li>"Movie": name of the film
<li>"Worldwide": amount of worldwide revenue given in US$
<li>"US($)": amount of revenues made in the USA given in US$
<li>"%-US": percentage of worldwide box office revenues made in the USA 
<li>"Foreign": amount of revenues made outside the USA given in US$ (scraped data is from US website)
<li>"%-Foreign": percentage of worldwide box office revenues made outside the USA
<li>"Rating": IMDb user rating on a scale of 1 to 10  
<li>"Year": release year of the movie
</ol>

**Is any information missing from individual instances?**

We were not able to scrape IMDb ratings for all movies in the Box Office Mojo ranking. Therefore some movies will display an N/A in the rating column.

**Are there any errors, sources of noise, or redundancies in the
dataset?**

As Box Office Mojo does not provide any movie ID's the data from Box Office Mojo is matched with data scraped from IMDb based on movie titles. In contrast to ID-tags, movie titles are not unique. Therefore there is a possibility that one movie can be matched with multiple movie ratings. Additionally, movie ratings are subjected to bias as they only measure the opinion of people who rate movies on IMDb.

**Is the dataset self-contained, or does it link to or otherwise rely on
external resources?**

The dataset relies on the [IMDB](https://www.imdb.com/?ref_=helpms_helphdr_cons)-website and the [BoxOfficeMojo](https://www.boxofficemojo.com/?ref_=bo_nb_tt_mojologo)-website. This means that the data that is being scraped gets daily updated on the website and could therefore change. There's, thus, no archive of the exact data at a specific point in time. 



### 1.3 **Collection process**

**How was the data associated with each instance acquired?**

The data extraction method we used was BeautifulSoup. We did so as both websites we used are static websites. The film names and the revenues are acquired directly via [Box Office Mojo Worldwide page](https://www.boxofficemojo.com/year/world/?ref_=bo_nb_hm_tab). Here the worldwide box office revenue data is provided in a table. We use Beautiful soup to parse through the table. Each row in the table can be find in a 'tr'-tag. Each item in each row can be find in a 'td'-tag. We extract the items from the td-tags by looping through each row (tr) individually. This way we ensure the data integrity won't be compromised by missing values. We loop through different years by adding a counter to the URL equal to the years of interest. Our Box Office Mojo data was obtained at 

The ratings are provided via [IMDB](https://www.imdb.com/). On IMDb, feature films are presented in a list. We use soup.find_all to find the movies on this list. We then use the 'h3-' and 'strong-tag' to extract the movie title and rating respectively. To loop through all years, we must add a counter to the URL equal to the years of interest. Furthermore, we want to scrape multiple pages for each year. To do so, we use the range function. This allows us to add the pagenumber to the URL in steps of 50.

**What mechanisms were used to collect the data?**

For the collection we used Google Colab running on Python. Our Box Office Mojo data was obtained at 2021-10-17 08:43:51,507. The IMDb data was obtained at 2021-10-17 09:06:16,515. After data collection, the dataframes are uploaded to Google drive as a CSV-file.  

**If the dataset is a sample from a larger set, what was the sampling strategy?**

The dataset is a sample from a large set. First of all, we decide to scrape only the data from the 2015 to the present to see how covid impacts on gross revenues and merging this data with rating on IMDb website. Then we decide to take only the best 50 films for gross revenues from boxofficemojo's website. Beyond that, the sample is arbitrary.

**Who were involved in the data collection process?**

The data collection was done by four students from Tilburg University for the class [Online Data Collection & Management](https://odcm.hannesdatta.com/). Since it is a university project, no compensation was foreseen.

**Over what timeframe was the data collected? Does this timeframe match the creation timeframe of the data associated with the instances? If not, please describe the time- frame in which the data associated with the instances was created.**

The data was collected in a time frame that does not correspond to the time frame in which the data associated with the instances was created. We collected data for the years 2015 to 2021 and therefore most of the data was already on the website. On the other hand, some data are still updated daily, so they may still change over time (especially for those referring to the current year and 2020).

**Were any ethical review processes conducted?**

Our data does not store any personally identifiable information. We do not foresee and legal or ethical concerns.

## 1.4.   Preprocessing

**Has there been done any preprocessing after data collection?**

We changed some of the column names as opposed to the way they are displayed on Box Office Mojo. Box Office Mojo displays US-revenue under the column name 'domestic'. We felt this was a somewhat ambiguous term and decided to change it to 'US'.

**How are the final datafiles stuctured?**

Before creating the final dataset, we ensured all variables had the correct datatype. We changed the 'Rank'-variable from an object to an integer as it is a number. When deploying the dataset as a CSV-file, we make sure to keep the column names and remove the index column.

**Was the “raw” data saved in addition to the preprocessed/cleaned/labeled
data? **

No, the labeling is done when creating the dataframe. This means that the table contains the names given by us. 

**Is the software used to preprocess/clean/label the instances available?**

The labeling has been done in the same source file as the scraping itself, which means that Python is being used.

## 1.5.		Uses

**Has the dataset been used for any tasks already? If so, please provide a description.**

The dataset we created based on scraping data from the box office mojo and Imdb websites  has not been used for any tasks so far. The idea is to look for the impact of Covid-19 on the movie industry. In which we want to compare the revenues of movies across years. This can be done by calculating the average revenue per year, so that we can compare year by year. Or the dataset might be specified into more detail, where we only compare the revenues of the top 5 movies across the years. 

**Is there a repository that links to any or all papers or systems that use the dataset? If so, please provide a link or other access point**

We used a repository on Github : https://github.com/Albirizzu/oDCM_team8.git
*What (other) tasks could the dataset be used for?*
The dataset now mainly focusses on the revenues produced per movie. This revenues will be compared over a couple of years to look for the impact of Covid-19. 

However, the task can be extended to analyze the growth curve of revenues made in the movie industry. Whether this effect is exponential or linear over the last couple of years. 

Also, an analysis on the effect of review ratings on the revenues can be done. A linear regression based on these two variables can be done to search for a correlation. 

Finally, besides the total market revenue the dataset also data on the domestic theatrical market revenue ( USA). Based on this data we could compare how well the USA did compared to the world in generating revenue for a movie. 

**Is there anything about the composition of the da-taset or the way it was collected and prepro-cessed/cleaned/labeled that might impact future uses? For example, is there anything that a future user might need to know to avoid uses that could result in unfair treat-ment of individuals or groups (e.g., stereotyping, quality of service issues) or other undesirable harms (e.g., finan-cial harms, legal risks) If so, please provide a description. Is there anything a future user could do to mitigate these undesirable harms?**

The composition of the data set is now based on the top 50 movies based on their revenue. So this has to be kept in mind for the future, to keep the composi-tion based on the top 50 based and doesn’t change it to the top 100 or top 200. 
Also the possibilities of unforeseen errors in the initial dataset can have their effect on future users. As these errors might be included it will lead to un-valid con-clussions. 

**Are there tasks for which the dataset should not be used? If so, please provide a description**

There are no tasks for which the dataset should not be used based on any legal or ethical concerns. 
