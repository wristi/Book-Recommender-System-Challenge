#One sentence summary
This project takes user data from three Amazon Book Data sets and utilizes collaborative filtering methods to create a reliable recommender system.

#Abstract
•	In this challenge, my goal is to accurately predict which products users will buy based on user activity, alongside ratings which have been given by the user. 
•	Using a collaborative filtering system, this approach takes product IDs, compiles a list of users who scored them, and builds a similarity between all these users. From there it is possible to compare similar products and suggest those to other users. 
•	A model employed by other Kaggle users has netted a runtime of 1 minute and 13 seconds. Following a similar route, I intend to get under a minute with my specific method

#Motivation and Background
•	This topic intrigues me because the methods of filtering can be used on different levels, so there is enough room for me to iterate as I see fit. This is the perfect challenge for me, as its structure and implementation are theoretically easy to comprehend but cannot be replicated with just the bigger picture in the same way a board game can be coded. With this said, a challenge like this will aid at a time where I am still an intermediate.
•	This is also a unique issue because it is solely based on how well I can use algorithms to enhance the performance of a system. Given that this project is a success, there are numerous ways to iterate on this idea, like using deep learning. 
•	In this problem, I specifically am looking for a way to take implicit data and factor it alongside explicit data, in order to give more accurate representation of what people want. Implicit and explicit data includes things like whether you clicked a product versus if you liked or rated it 5 stars. One glaring problem that I intend to solve, is that implicit data is never recorded negatively. If you click a product, you show an arbitrary ‘interest’ in it and the recommender system factors this into its suggestions. 

#Dataset
•	My Dataset consists of 73k instances of User Activity from CI&T DeskDrop. This data set contains 5 crucial features: Item Attributes (User info, Article URL), User context (Context for the implicit feedback like user visits), Logged user tracking, Implicit feedback, as well as the type of client from the user.
•	The Article Data is 17.99 MB, and the User Interactions are 11.95MB 


#Goals
Feasibility:
In the feasibility stage, I will take my time performing Data Analysis & visualization to find out which Recommendation Algorithm is needed. Specifically, I’ll tie similarities between articles or between users (Item-to-Item VS User-to-User.) Next, I will make my way through the different libraries and see which package works best for the Algorithm I go with. 

#Prototype:
In prototyping, most of the time will go into designing code to support Matrix Factorization techniques and creating features to take implicit/explicit data.

#Production:
The production stage revolves around performance after the code works as intended. For bonus points I would like to make an app that can run this program and suggest some articles to users. 

•	Outline a detailed 5-week workplan.

Week 1: Accumulating Recommender Systems and understanding the difference between Recommender Systems. At this time, I will also build code to hold the data downloaded from Kaggle. 

Week 2: Dabbling in matrix factorization and building a working framework in code. Ideally in this time, I’ll be starting to familiarize myself with the library features in SciPy or CaseRecommender. 

Week 3: In the third week of development, I will be writing algorithms with the libraries I have worked with in the second week. By this point I expect to already have worked code that takes in the Data and outputs results based on the explicit rating system.

Week 4: In this phase, I expect to already have the explicit rating system working and this week will be devoted to integrating the implicit data. With this I’ll have both values factor into what recommendations are made.

Week 5: This final week will be devoted to condensing this code and trying to gauge performance. This will be the week to beat the Kaggle challenge time of 191.3 seconds.  

