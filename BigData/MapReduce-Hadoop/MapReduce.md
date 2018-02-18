# MapReduce
MapReduce is a programming paradigm that runs in the background of Hadoop to provide scalability and easy data-processing solutions.  


## How MapReduce Works?
The MapReduce algorithm contains two important tasks, namely Map and Reduce.  
1. The Map task takes a set of data and converts it into another set of data, where individual elements are broken down into tuples (key-value pairs).  

2. The Reduce task takes the output from the Map as an input and combines those data tuples (key-value pairs) into a smaller set of tuples.  

All phases:  
[](https://www.tutorialspoint.com/map_reduce/images/phases.jpg)    
Input Phase, Map, Intermediate Keys, Combiner, Shuffle and Sort, Reducer, Output Phase


## MapReduce - Algorithm
The MapReduce algorithm contains two important tasks, namely Map and Reduce.
- The map task is done by means of Mapper Class
- The reduce task is done by means of Reducer Class.

Mapper class takes the input, tokenizes it, maps and sorts it. The output of Mapper class is used as input by Reducer class, which in turn searches matching pairs and reduces them.  
[](https://www.tutorialspoint.com/map_reduce/images/mapper_reducer_class.jpg)     



## MapReduce - API
### JobContext Interface
The JobContext interface is the super interface for all the classes, which defines different jobs in MapReduce.

### Job Class
The Job class is the most important class in the MapReduce API. It allows the user to configure the job, submit it, control its execution, and query the state. The set methods only work until the job is submitted, afterwards they will throw an IllegalStateException.
```
// Create a new Job
Job job = new Job(new Configuration());
job.setJarByClass(MyJob.class);

// Specify various job-specific parameters
job.setJobName("myjob");
job.setInputPath(new Path("in"));
job.setOutputPath(new Path("out"));

job.setMapperClass(MyJob.MyMapper.class);
job.setReducerClass(MyJob.MyReducer.class);

// Submit the job, then poll for progress until the job is complete
job.waitForCompletion(true);

```


### Mapper Class
The Mapper class defines the Map job. Maps input key-value pairs to a set of intermediate key-value pairs.   
**map** is the most prominent method of the Mapper class. 

### Reducer Class
The Reducer class defines the Reduce job in MapReduce. It reduces a set of intermediate values that share a key to a smaller set of values. Reducer implementations can access the Configuration for a job via the JobContext.getConfiguration() method. A Reducer has three primary phases − Shuffle, Sort, and Reduce.  
- Shuffle   
The Reducer copies the sorted output from each Mapper using HTTP across the network.

- Sort   
The framework merge-sorts the Reducer inputs by keys (since different Mappers may have output the same key). The shuffle and sort phases occur simultaneously, i.e., while outputs are being fetched, they are merged.

- Reduce     
In this phase the reduce (Object, Iterable, Context) method is called for each <key, (collection of values)> in the sorted inputs.
**reduce** is the most prominent method of the Reducer class.  



## MapReduce - Hadoop Implementation
The operation of MapReduce in Hadoop framework using Java

### MapReduce Algorithm
Generally MapReduce paradigm is based on sending map-reduce programs to computers where the actual data resides.  
- During a MapReduce job, Hadoop sends Map and Reduce tasks to appropriate servers in the cluster.

- The framework manages all the details of data-passing like issuing tasks, verifying task completion, and copying data around the cluster between the nodes.

- Most of the computing takes place on the nodes with data on local disks that reduces the network traffic.

- After completing a given task, the cluster collects and reduces the data to form an appropriate result, and sends it back to the Hadoop server.

### Inputs and Outputs (Java Perspective)
The MapReduce framework operates on key-value pairs, that is, the framework views the input to the job as a set of key-value pairs and produces a set of key-value pair as the output of the job, conceivably of different types.  

### Example 
[WordCount](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html)

## MapReduce - Partitioner
A partitioner works like a condition in processing an input dataset. The partition phase takes place after the Map phase and before the Reduce phase.  

The number of partitioners is equal to the number of reducers. That means a partitioner will divide the data according to the number of reducers. Therefore, the data passed from a single partitioner is processed by a single Reducer.  

A partitioner partitions the key-value pairs of intermediate Map-outputs. It partitions the data using a user-defined condition, which works like a hash function.   

### Example
[MapReduce Partitioner Implementation](https://www.tutorialspoint.com/map_reduce/map_reduce_partitioner.htm) . 

## MapReduce - Combiners
A Combiner, also known as a semi-reducer, is an optional class that operates by accepting the inputs from the Map class and thereafter passing the output key-value pairs to the Reducer class.  

The main function of a Combiner is to summarize the map output records with the same key. The output (key-value collection) of the combiner will be sent over the network to the actual Reducer task as input.  

### Example
[MapReduce Combiner Implementation](https://www.tutorialspoint.com/map_reduce/map_reduce_combiners.htm)


## MapReduce - Hadoop Administration
http://localhost:50070/
http://localhost:8088/
http://localhost:8042/
 





## Reference
1. [MapReduce Tutorial - Apache Hadoop 3.0.0](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html)
2. [MapReduce Tutorial - tutorialspoint](https://www.tutorialspoint.com/map_reduce/index.htm)
