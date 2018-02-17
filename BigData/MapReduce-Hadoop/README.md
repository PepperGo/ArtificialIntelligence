# MapReduce/Hadoop

## Relationship between MapReduce and Hadoop
Hadoop is an open source tool of ASF( Apache Software Foundation). Open source means you can change its code according to your requirement.  
Hadoop is a Java-based programming framework that supports the processing and storage of extremely large data sets in a distributed computing environment.   
Apache Hadoop is the most popular and powerful big data tool, Hadoop provides world’s most reliable storage layer – HDFS, a batch Processing engine – MapReduce and a Resource Management Layer – YARN.


## Hadoop
Hadoop is an open-source framework that allows to store and process big data in a distributed environment across clusters of computers using simple programming models. It is designed to scale up from single servers to thousands of machines, each offering local computation and storage.  

### What is Big Data?
Big data means really a big data, it is a collection of large datasets that cannot be processed using traditional computing techniques. Big data is not merely a data, rather it has become a complete subject, which involves various tools, technqiues and frameworks.  

Thus Big Data includes huge volume, high velocity, and extensible variety of data. The data in it will be of three types.
- Structured data : Relational data.
- Semi Structured data : XML data.
- Unstructured data : Word, PDF, Text, Media Logs.

### Big Data Solutions
Traditional Approach: RDBMS    

Google’s Solution: Google solved this problem using an algorithm called MapReduce.   
This algorithm divides the task into small parts and assigns those parts to many computers connected over the network, and collects the results to form the final result dataset.   
Hadoop: Hadoop runs applications using the MapReduce algorithm, where the data is processed in parallel on different CPU nodes. In short, Hadoop framework is capable enough to develop applications capable of running on clusters of computers and they could perform complete statistical analysis for a huge amounts of data.  

### Hadoop - Introduction
Hadoop is an Apache open source framework written in java that allows distributed processing of large datasets across clusters of computers using simple programming models. A Hadoop frame-worked application works in an environment that provides distributed storage and computation across clusters of computers. Hadoop is designed to scale up from single server to thousands of machines, each offering local computation and storage.   

Hadoop Architecture: 
Hadoop framework includes following four modules:
- Hadoop Common: These are Java libraries and utilities required by other Hadoop modules. These libraries provides filesystem and OS level abstractions and contains the necessary Java files and scripts required to start Hadoop.
- Hadoop YARN: This is a framework for job scheduling and cluster resource management.
- Hadoop Distributed File System (HDFS™): A distributed file system that provides high-throughput access to application data.
- Hadoop MapReduce: This is YARN-based system for parallel processing of large data sets.

#### MapReduce
**Hadoop MapReduce** is a software framework for easily writing applications which process big amounts of data in-parallel on large clusters (thousands of nodes) of commodity hardware in a reliable, fault-tolerant manner.  
The term MapReduce actually refers to the following two different tasks that Hadoop programs perform:  
- The Map Task: This is the first task, which takes input data and converts it into a set of data, where individual elements are broken down into tuples (key/value pairs).  
- The Reduce Task: This task takes the output from a map task as input and combines those data tuples into a smaller set of tuples. The reduce task is always performed after the map task.

The MapReduce framework consists of a single master JobTracker and one slave TaskTracker per cluster-node.  
The **master** is responsible for resource management, tracking resource consumption/availability and scheduling the jobs component tasks on the slaves, monitoring them and re-executing the failed tasks.   
The **slaves TaskTracker** execute the tasks as directed by the master and provide task-status information to the master periodically.

The **JobTracker** is a single point of failure for the Hadoop MapReduce service which means if JobTracker goes down, all running jobs are halted.  

HDFS uses a master/slave architecture where master consists of a single NameNode that manages the file system metadata and one or more slave DataNodes that store the actual data.

A file in an HDFS namespace is split into several blocks and those blocks are stored in a set of DataNodes. 
The **NameNode** determines the mapping of blocks to the DataNodes. 
The **DataNodes** takes care of read and write operation with the file system. They also take care of block creation, deletion and replication based on instruction given by NameNode.

#### Hadoop Distributed File System
Hadoop can work directly with any mountable distributed file system such as Local FS, HFTP FS, S3 FS, and others, but the most common file system used by Hadoop is the **Hadoop Distributed File System (HDFS)**.  



#### How Does Hadoop Work?
- Stage 1
A user/application can submit a job to the Hadoop (a hadoop job client) for required process by specifying the following items:  
The location of the input and output files in the distributed file system.  
The java classes in the form of jar file containing the implementation of map and reduce functions.  
The job configuration by setting different parameters specific to the job.  

- Stage 2
The Hadoop job client then submits the job (jar/executable etc) and configuration to the JobTracker which then assumes the responsibility of distributing the software/configuration to the slaves, scheduling tasks and monitoring them, providing status and diagnostic information to the job-client.

- Stage 3
The TaskTrackers on different nodes execute the task as per MapReduce implementation and output of the reduce function is stored into the output files on the file system.


### Hadoop - Enviornment Setup
Please refer to [Hadoop - Enviornment Setup](https://www.tutorialspoint.com/hadoop/hadoop_enviornment_setup.htm).  
Or just google how to install and configure haddop in your machine.  

For mac:[Hadoop Installation on Mac OS X](https://isaacchanghau.github.io/2017/06/27/Hadoop-Installation-on-Mac-OS-X/)
[Another useful material for mac](https://amodernstory.com/2014/09/23/installing-hadoop-on-mac-osx-yosemite/)

#### Hadoop Operation Modes
Once you have downloaded Hadoop, you can operate your Hadoop cluster in one of the three supported modes:
- Local/Standalone Mode : After downloading Hadoop in your system, by default, it is configured in a standalone mode and can be run as a single java process.
- Pseudo Distributed Mode : It is a distributed simulation on single machine. Each Hadoop daemon such as hdfs, yarn, MapReduce etc., will run as a separate java process. This mode is useful for development.
- Fully Distributed Mode : This mode is fully distributed with minimum two or more machines as a cluster. We will come across this mode in detail in the coming chapters.

### Hadoop - HDFS Overview


## Reference:
1. [Hadoop Official Documentation](https://hadoop.apache.org/docs/r1.2.1/mapred_tutorial.html)
2. [MapReduce-tutorialspoint](https://www.tutorialspoint.com/map_reduce/map_reduce_introduction.htm)
3. [Hadoop-tutorialspoint](https://www.tutorialspoint.com/hadoop/hadoop_big_data_overview.htm)
