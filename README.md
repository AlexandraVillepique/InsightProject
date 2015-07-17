# Pick a Place

This project is part of Fellowship at **INSIGHT DATA SCIENCE**.

Fellows suppose to pick a project during a first or second week of the program. For me, finding a practical, scalable project included only looking around.  
I live in a resort area, a place where certain types of business thrive, and others, crop up for a season and then close.  
Many people move here. It is a beautiful place to live, but there are no jobs. So they think opening a business will solve the problem. Often, it does not.   
I wondered, why is so? Why so many people open a business that has no chance of succeeding in a certain area? Is there a way to use a data to help them pick a location suitable for their type of business. 

Today, YELP offers free dataset that can be used for this purpose.  This data set is ultimately biased because only YELP users populate the database with their opinions, but it is good starting point. So, I took public data set YELP offered and started. 

##Exploratory analysis

First I had to look are the YELP data useful for my project. An exploratory analysis is the best approach. I wished to see is there a difference in visitation and rating of a business across regions covered by YELP data.   
Of course, I had to make sure that I do not measure difference caused by the geography or climate of the area. After all, one cannot expect ski shop equipment to thrive in places where there is no possibility to ski.   
So, I looked through the YELP business categories and picked the number of them that should not be affected by climate or geography.   

 I've seen a change. A business that are common for the whole US had different popularity across the areas covered by YELP dataset. I was on right track.   
The notebook  **PreliminaryExploratoryAnalysis** -  offers a brief overview of my first exploration of the dataset, while **ExploratoryAnalysis** - offers more dwelling into a problem.  

Although my exploratory analysis proved that YELP dataset is a good start, I was not happy with its ingrained bias. The dataset offered for the contest contained so-called University dataset and few more complete cities. The University dataset is ultimately biased because it covers only areas around the universities, and as such introduces a bias towards the particular type of the population into my analysis. However, initially I decided to keep it and try to form predictors from US Census data. In this way, I was hoping to expand my results to the areas not covered by  YELP data set.   

My idea was based on research findings that talked about the connection between a person's zip code and risk of obesity ( http://www.iqsolutions.com/ideas-and-insights/blog/how-your-zip-code-can-affect-your-weight). From this research, for me, it did not take much to make a jump to a possible connection between some demographic characteristics and the popularity of business categories.  After all, it is almost common sense that same type of customers will patronize a same group of business types.   
Just remember your high school classmates; some of them were most likely to be found in a bookstore and others in a fashion shop. Both types of persons have set of interests that will draw them to patronize, overall,  the different types of business. So businesses that targeted a particular type of customers would benefit from finding out where those customers are.    
I decided to check that idea.   

**SeakPeak** - notebook provides an example of that approach. Here I tried to connect the relationship between bookstores and ratio of bachelor degrees in population. I expected to get a positive correlation, especially because YELP dataset is strongly biased towards university areas.   
Imagine my surprise when, instead,  I got a negative correlation.   
The next step has to be attempt to answer: "Why? Why the negative correlation?" 
So I dwelled deeper into the dataset and noticed that surprisingly Las Vegas, NV has a surprisingly large number of bookstores. Careful examination of those bookstores revealed miscategorization. In Las Vegas, bookies tend to categorize their business as a bookstore.   

YELP itself admits that business categories in their dataset are not perfect. They offer with their dataset a free Python code that is supposed to help a bit with miscategorization. However, that program does not remove a human misinterpretation of the business category definition. Nevertheless, that problem can be solved by simple NLP (Natural Language Processing) analysis of the business types.   

## Change of direction

Unfortunately, US Census data, encompassing all variables I deem useful, does not have enough resolution to pinpoint a location suitable for business. I needed resolution that provides accuracies withing a block while Census data that cover income and education information tend to resolve only to the town level. 
Thus, I decided to continue my research using only Yelp data. This means that the whole approach to the problem had to be slightly changed.   

Here you can find iPhyton notebooks, detailing my data exploration of the project, analysis, and plans. 

The slides for the project you can find at http://slides.com/aleksandravillepique/deck#/

Below are individual notebooks with the short explanation what is in them.

**PreliminaryExploratoryAnalysis** -  a brief overview of my first exploration of the dataset to see is it appropriate for answering my question. 

**ExploratoryAnalysis** - more dwelling into a problem. 

**SeakPeak** - looking is there a connection between demographic info and popularity of different business categories.

Unfortunately, now I had to change direction in the analysis. Census data, encompassing all variables I deem useful, does not have enough resolution to answer truly which exact location would be suitable for which type of the business. Thus, I decided to continue my research using only Yelp data. This means that the whole approach to the problem is slightly changed. 

**Clustering algorithm** - My explanation of why DBSCAN is more suitable for use in a geographical application. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Clustering%20Algorithms%20.ipynb

**Phoenix_AZ** - Clustering applied on Phoenix. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Phoenix_AZ.ipynb

**New Variable - Location Quotient** - I had to develop a new variable to deal with varying volume of visitors to different areas of the city. 

**Analysis** -detailed analysis with the result and  map plots. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Analysis.ipynb

**SteamlinedAnalysis** - just a part of an analysis that is crucial for picking a location based on Location Quotient. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/SteamlinedAnalysis.ipynb

**Pittsburgh_analysis** - what is happening in this city? View at: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Pittsburgh_analysis.ipynb