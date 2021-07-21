# Data Analysis with Spark RDD API

## Controversial trending videos and Category-trending correlation

Data set used is adapted from https://www.kaggle.com/datasnaek/youtube-new
### Input Data Set Description 

<p align = "justify"> The dataset contains several months records of daily top trending YouTube video in the following ten countries: Canada,France, Germany, India,Japan, Mexico, Russia, South Korea, United Kingdom and United States of America. There are up to 200 trending videos listed per day. In the original data set, each country’s data is stored in a separate CSV file, with each row representing a trending video record. If a video is listed as trending in multiple days, each trending appearance has its own record. The category names are stored in a few separate JSON files. </p>

The following preprocessing have been done:
* Merging the 10 individual CSV files into a single CSV file;
* Adding a column category to store the actual category name based on the mapping
* Adding a column country to store the trending country, each country is represented by two capital letter code.
* Removing rows with invalid video id values
* Removing most columns that are not relevant to the workloads

<p align = "justify"> The results is a CSV file Dataset.csv with 7 columns and no header row. The columns are as follows. The trending date column has the date format: yy.dd.mm, video_id,trending_date,category,views,likes,dislikes,country </p>

<p align = "justify"> The file <a href="https://github.com/lalithavadlamani/Spark-Data-Analytics-/blob/main/Controversial%20trending%20videos%20and%20Category-trending%20correlation.ipynb"> Controversial trending videos and category trending correlation.ipynb </a> has 2 workloads implemented in it:

* Controversial Trending Videos Identification 
* Category and Trending Correlation
</p>

### Controversial Trending Videos Identification 
<p align = "justify"> Listing a video as trending would help it attract more views. However, not all trending videos are liked by viewers. For some video, listing it as trending would increase its dislikes number more than the increase of its likes number. The first part of code aims to identify such videos. 
The output is the top 10 videos with fastest growth of dislikes number between its first and last trending appearances in the same country. </p>

<p>Computation graph: </p> 

![](https://github.com/lalithavadlamani/Spark-Data-Analytics-/blob/main/workload-1.jpg)

### Category and Trending Correlation 
<p align = "justify"> Some videos are trending in multiple countries. The second part of the code aims to identify any correlation netween video category and trending popularity among countries. For instance, we may expect to see a common set of trending music videos in many countries and a distinctive set of trending political videos in each country. The output is the average country number for videos in each category sorted by average country number. </p>

<p>Computation graph: </p> 

![](https://github.com/lalithavadlamani/Spark-Data-Analytics-/blob/main/workload-2.png)

