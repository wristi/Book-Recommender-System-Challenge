
# Book Crossing Recommender System Using Collaborative Filtering 

# One Sentence Summary:
In this project, I use 3 types of Collaborative Filtering models to recommend 10 books to a given user.

# Overview
In order to see which CF method works best, I ranked User-To-User, Item-To-Item, and Content-Based Filtering in accordance to how well they performed with this dataset. 

# Summary of Workdone
In my data analysis, I was able to merge all three of the files together by establishing commonality betwen User-IDs and Book ISBNs. These happened matched the ones found in the ratings file. From there, I investigated trends in the data like the most frequently reviewed books, books with the high ratings, and found correlation between them. Furthermore , I matched High Ratings with things like age,and countries, all of which proved fruitful for understanding how recommendations are made.

Putting a recommender system together was certainly the more challenging part, however, it took only one function to create a UserID-ISBN similarity matrix. From then on, I created Object Oriented frameworks for User,Item, and Content based KNN Models using SKLearn. 
The result were lists of 10 recommendations for a given User. 


# Data
This Dataset is actually three CSVs, for  Users, Ratings, and Books respectively. 
Within their respective files are  278,858 users whom provide a total of 1,149,780 explicit and implicit ratings.
There are also 271,379 books , which are tracked by a ISBN number.

From the link I provided, here is more information about the columns of each file:

The Book-Crossing dataset comprises 3 tables.
BX-Users
Contains the users. Note that user IDs (`User-ID`) have been anonymized and map to integers. Demographic data is provided (`Location`, `Age`) if available. Otherwise, these fields contain NULL-values.

BX-Books
Books are identified by their respective ISBN. Invalid ISBNs have already been removed from the dataset. Moreover, some content-based information is given (`Book-Title`, `Book-Author`, `Year-Of-Publication`, `Publisher`), obtained from Amazon Web Services. Note that in case of several authors, only the first is provided. URLs linking to cover images are also given, appearing in three different flavours (`Image-URL-S`, `Image-URL-M`, `Image-URL-L`), i.e., small, medium, large. These URLs point to the Amazon web site.

BX-Book-Ratings
Contains the book rating information. Ratings (`Book-Rating`) are either explicit, expressed on a scale from 1-10 (higher values denoting higher appreciation), or implicit, expressed by 0.


<img width="557" alt="image" src="https://user-images.githubusercontent.com/111654423/236696806-5e8e019e-6509-4d88-bf16-a3660954c82c.png">
Here is a graph of the Age Distribution, the most frequent age group ranged from 25-35. 

<img width="904" alt="image" src="https://user-images.githubusercontent.com/111654423/236696972-1bfc54dc-fcd0-4837-b769-fd60dc5ac47c.png">
This Bar Graph shows us that books which are frequently reviewed are not always rated highly. In the top 10, Wild Animus(rated 4.85) has substantially lower ratings than The Lovely Bones or any of the other novels.

<img width="858" alt="image" src="https://user-images.githubusercontent.com/111654423/236697130-898ab84c-bd95-4afa-b0dc-be15f4146bea.png">
This is a Top 10 of Books most frequently reviewed with the highest ratings, which are comprised of three different authors. It would be wrong to recommend the top 1% of books to everyone, some diversity was needed. 
 
# Problem Formulation
Define:
Input / Output: After inputting a User-ISBN matrix, the output will be ten books that are recommended to them. 
Models: KNN Models: 
In my code there is documentation which covers how they work in depth, but here are the functions that comprise each.

User Based Collaborative Filtering:
def normalize(self, dataframe):
def compute_similarity(self, x, y):
def create_similarity_matrix(self):
def get_neighbors(self, user_id, similarity_matrix):
def score_item(self, user_id, neighbor_rating, neighbor_similarity, ratings):
def recommend(self, user_id):

Item Based Collaborative Filtering:
def prepare_data(self):
def compute_deviations(self):
def slope_one_recommend(self, user_ratings):
def recommend(self, recommendations):

Content Based Collaborative Filtering:
def clean(self, text, combine=False):
def prepare_data(self, books, rating_threshold = 2):
def create_embedding_matrix(self):
def create_kernel(self):
def create_indices(self):
def recommend(self, query):


Collaborative Filtering uses cosine similarity to calculate distance between two points of a given matrix, drawing a line between them.
The math is represented by this expression: 

Cos(x, y) = x . y / ||x|| * ||y|| 

From the line drawn, the angle is used to gauge similarity, meaning the lower the angle, the more definite an overlap becomes.
![UntitledDiagram2-2](https://user-images.githubusercontent.com/111654423/236700440-21cc56bd-8031-4e4d-8bb2-2c3283b243df.png)



(for more on this: https://www.geeksforgeeks.org/cosine-similarity/)



Training:

There was no training necessary, as KNN models simply detect the closest data points, and require no fitting. 
This means the model has to iterate over the dataset in a loop, which can be slower or faster depending on the method used.
In the event of applying some kind of Machine Learning solution, which does require training, I recommend using some of the trends found in my Data Analysis as a reference. Try to make sure your model is not recommending only the highest rated books, and utilize feature engineering to define genres, I believe this would dramatically improve your results.

# Conclusions

The rankings of the models are as follows:

Item Based
Content Based
User Based

* Item Based CF is most reliable because of its computational edge, in which the more users there are, the more scaleable the system becomes.
* Content Based CF is runnerup, due to some discrepancies of the dataset itself. Content Based Filtering is meant to find similarities where it isn't always obvious, and things like Keywords in the data are necessary for finding similarity. Having something like a Genre to sort books as a column would make this easier, as the search criteria was proven flimsy. 
* User Based CF may be the worst due to its high computation time, the process to find similarities in each user does not scale well, and was significantly slower than the other two. 

If I had to try something else, it would be Supervised Machine Learning. You could separate the users based on what you already know about them IE: which books they have reviewed, and try to reproduce similar results. 
This repository may prove helpful for using such a method, because the trends in my Data Analysis proves helpful for giving a range of recommendations based on features of the data like Location, Age, Review Frequency, ETC.
.
# How to reproduce results
1. Clone this repository to your device of choice
2. Either using Jupyter Notebook or Google Colab, load up the notebook.
3. I have commented commands which should allow you to download the code directly, but you can simply go to the link and download the three files: http://www2.informatik.uni-freiburg.de/~cziegler/BX/
4. After that, you're good to go! 

# Files Used
Data-Analyssis.ipynb: A Comprehensive Analysis of Trends in the data
Recommender-System.ipynb: Code for User,Item,and Content based CF algorithms and Functions to create necessary Matrices.

# Software Setup
In this Project I used the packages listed:
Pandas
Matplotlib
NumPy
SKLearn

I imported surprise, re, and time/warnings library, but I did not end up using them.

The commands I used to download them were:

!sudo apt install pip3

!pip3 install pandas
!pip3 install scikit-learn
!pip3 install numpy
!pip3 install matplotlib

# Citations

https://towardsdatascience.com/my-journey-to-building-book-recommendation-system-5ec959c41847
https://surprise.readthedocs.io/en/stable/knn_inspired.html
https://towardsdatascience.com/user-user-collaborative-filtering-for-jokes-recommendation-b6b1e4ec8642
https://towardsdatascience.com/my-journey-to-building-book-recommendation-system-5ec959c41847
https://github.com/tttgm/fellowshipai/tree/master
https://github.com/mohsenMahmoodzadeh/Book-Crossing-Recommender-System
