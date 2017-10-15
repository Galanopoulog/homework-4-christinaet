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

The data node is replicated, but the name node is not. If there's a network failure, data will be inaccessible. If a disk on name node fails, the metadata may be lost forever. In Hadoop 2, there is a backup name node.

2. (2 points) What happens when a data node fails?

When a data node fails, the name node marks it as dead and does not forward any new IO requests to it. Any data that was registered to a dead data node is not available to HDFS any more. Data node failure lowers a block's replication factor. The name node constantly tracks which blocks need to be replicated and initiates replication whenever necessary.

3. (1 point) What is a daemon?  Describe the role task trackers and job trackers play in the Hadoop environment.

A daemon is a background process. Hadoop consists of the following daemons:
Namenode, Secondary namenode, Jobtracker, Datanode, Tasktracker
The namenode and jobtracker daemons are master daemons. 

Jobtrackers manage tasktrackers and distribute the work between mappers and reducer. Tasktrackers administer the code (mapper and reducer tasks) on DataNodes. 

4. (1 point) Why is Cloudera's VM considered pseudo distributed computing?  How is it different from a true Hadoop cluster computing?

The full cluster is running only on one machine. True Hadoop cluster computing uses a cluster composed of many computers. 

5. (1 point) What is Hadoop streaming? What is the Hadoop Ecosystem?

Hadoop streaming is an API that allows programmers to write Mappers and Reducers in languages other than Java (i.e. python)

Hadoop Ecosystem is a series of tools and solutions that makes using the Hadoop framework easier and more user friendly. 

6. (1 point) During a reducer job, why do we need to know the current key, current value, previous key, and cumulative value, but NOT the previous value?

We need the current and previous keys to determine if we are changing keys. We then add the current value to the cumulative value group by the right key; previous value is not useful in this process.  

7. (3 points) A large international company wants to use Hadoop MapReduce to calculate the # of sales by location by day.  The logs data has one entry per location per day per sale.  Describe how MapReduce will work in this scenario, using key words like: intermediate records, shuffle and sort, mappers, reducers, sort, key/value, task tracker, job tracker.  

Users submit the MapReduce job (input data, MR program, configuration). The input data is split into fixed size chunks. Hadoop divide the job into map and reduce tasks - one map task for each split. Job trackers assign map tasks to individual nodes (usually the one that has/is close to the split data). Task trackers launch mappers that run the map function for each record in the split. Intermediate mapper output are emitted as key-value pairs and written locally. The key is location by day, the value is 1 (number of sales). For example, an intermediate record might look like this: { key : { date: 20170101, store_id : 1}, value : 1 }

The framework shuffles and sorts the intermediate records, and groups them by key. The sorted output is then transferred to the node where task trackers launch reducers. The reduce function accepts sorted mapper output, iterate through each list and sum up the value (sale count) by each key. When there are multiple reducers, each reducer gets one partition of the mapper output. The final output of the reducer(s) is the total number of sales per location per day. 

### Applied (5 points total)

Submit the mapper.py and reducer.py and the output file (.csv or .txt) for the first question in lesson 6 for Udacity.  (The one labelled "Quiz: Sales per Category")  Instructions for how to get set up is inside the Udacity lectures.  
