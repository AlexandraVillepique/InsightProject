# Pick a Place

This project is part of Fellowship at *INSIGHT DATA SCIENCE*. The slides presenting this project are here: http://slides.com/aleksandravillepique/deck#/

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

Instead of determining demographic info behind the popularity of a particular type of business, I concentrated on a different approach. As I said previously,  persons with a particular set of interests tend to patronize the business that matches their interests or needs. It might be possible to establish types of business that go well together, merely because they attract a similar type of customers. In such enviroment, a correct kind of neighbors will increase the number of people who enter the premises, simply by being close to the business type preferred by targeted customers.   

This analysis approach can be covered by YELP data only, and then, if time allows, analysis can be scaled up in precision using other data sources. 

The first step with this approach is to locate which businesses are physically close together. A clustering algorithm should be applied to geographical coordinates of the businesses. 
I did a test of such algorithm to see which one will perform the best for the purposes of my analysis.  **Clustering algorithm** notebook offers an explanation of why DBSCAN is more suitable for use in a geographical application. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Clustering%20Algorithms%20.ipynb

However, with this approach I had to weed out University dataset from YELP data and concentrate only on the data that covered the whole cities. The bias introduced by university centric areas would negatively impact generalization of my analysis.  **Phoenix_AZ** notebook offers an example of clustering applied on Phoenix, Arizona. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Phoenix_AZ.ipynb

## Dealing with biases


For my analysis, I decided to use reviews count as a proxy of the popularity of the business. However, the very structure of the city introduces bias. A typical town in the US tends to have heavily visited the downtown area and sparsely populated suburbs. This implies that business located in downtown will appear more attractive than business in suburb simply because there are more people visiting the area. I found a way to sort that particular problem. I formed a new variable, based on Location Quotient, and an economic indicator of the economic structure and activity of the area. This particular variable does not depend on the number of the visitors of the individual cluster of business but instead offers ranking of the local popularity of each business in the Phoenix. The details describing the variable, its definition and calculations can be found in notebook:  **New Variable - Location Quotient**.   

So, I could proceed with analysis. **Analysis**  is a notebook with detailed analysis with the result and map plots.  View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Analysis.ipynb  In this notebook, I also compared two different approaches to the map plots. The potential business owner wishes to see a simple presentation of the analysis results that directly addresses his/hers question. A map plot seems a logical solution of the results visualization.  
This notebook also covers a crude test of my analysis method. I compared my approach to the random placing of the business. So analysis based on Spearman rank correlation outperforms random siting of a business.   
The precision of this analysis approach could and should be improved by including another dataset. The most beneficial data would be data that include rent/property prices across the area. Moreover, demographic and economic information about the area can be included to increase the precision.   

**SteamlinedAnalysis** is a notebook that presents an analysis crucial for picking a location based on a popularity of the business category. In this notebook, only algorithms that produced satisfactory results are kept. View it here: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/SteamlinedAnalysis.ipynb   

Of course, just for fun, I decided to see what is going on in another city. 
**Pittsburgh_PA** is notebook that shows results of analysis for Pittsburgh, PA. View at: http://nbviewer.ipython.org/github/AlexandraVillepique/InsightProject/blob/master/Pittsburgh_analysis.ipynb


