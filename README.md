## DATA622 HW #4
- Assigned on October 11, 2017
- Due on October 25, 2017 11:59 PM EST
- 15 points possible, worth 15% of your final grade

### Instructions:

Use the two resources below to complete both the critical thinking and applied parts of this assignment.

1. Listen to all the lectures in Udacity's [Intro to Hadoop and Mapreduce](https://www.udacity.com/course/intro-to-hadoop-and-mapreduce--ud617) course.  

2. Read [Hadoop A Definitive Guide Edition 4]( http://javaarm.com/file/apache/Hadoop/books/Hadoop-The.Definitive.Guide_4.edition_a_Tom.White_April-2015.pdf), Part I Chapters 1 - 3.

### Critical Thinking (10 points total)

Submit your answers by modifying this README.md file.

1. (1 points) What is Hadoop 1's single point of failure and why is this critical?  How is this alleviated in Hadoop 2?

Hadoop 2 use YARN for resource allocation and job scheduling. There is a backup NameNode

2. (2 points) What happens when a data node fails?

3. (1 point) What is a daemon?  Describe the role task trackers and job trackers play in the Hadoop environment.

4. (1 point) Why is Cloudera's VM considered pseudo distributed computing?  How is it different from a true Hadoop cluster computing?

5. (1 point) What is Hadoop streaming? What is the Hadoop Ecosystem?

Hadoop Ecosystem is a series of tools and solutions that makes using the Hadoop framework easier and more user friendly. 

6. (1 point) During a reducer job, why do we need to know the current key, current value, previous key, and cumulative value, but NOT the previous value?

7. (3 points) A large international company wants to use Hadoop MapReduce to calculate the # of sales by location by day.  The logs data has one entry per location per day per sale.  Describe how MapReduce will work in this scenario, using key words like: intermediate records, shuffle and sort, mappers, reducers, sort, key/value, task tracker, job tracker.  

### Applied (5 points total)

Submit the mapper.py and reducer.py and the output file (.csv or .txt) for the first question in lesson 6 for Udacity.  (The one labelled "Quiz: Sales per Category")  Instructions for how to get set up is inside the Udacity lectures.  
