slidenumbers: true
footer: brianstempin.com 🐍

# Intro to Spark with Python

or

## How to Crunch Some Really Big Data

---

# What is Spark, and Why Do I Care?

From their home page:

*Apache Spark™* is a unified analytics engine for large-scale data processing.

---

# What Does That Really Mean?

Let's imagine you have some data set, perhaps a really large set of files, that you'd like to perform operations on.
Let's discuss how to scale that.

---

# Naive Implementation:  Single Thread/Process

The most naive implementation is to write a single threaded program to crunch through our data.

Pros:
  
* Simple to write and understand.

---
# Naive Implementation:  Single Thread/Process

Cons:

* We only use a single core of a processor, wasting capacity.

---

# Better Attempt: Threads or Multiprocessing

Let's say that we happen to know that some of parts of our program can be run in parallel.  We could execute those parts
in separate threads or separate processes in parallel.

---
# Better Attempt: Threads or Multiprocessing

Pros:
 
* Our program is now more performant.
* Our program is able to utilize all available resources the machine has to offer.

---
# Better Attempt: Threads or Multiprocessing

Cons:
 
* Our program is much more difficult to understand; we have to treat the parallel parts differently.
* Multithreading is more difficult to debug.
* Our upper limit for performance is a single machine.

---

# Even Better Attempt:  Multiple Workers Across Multiple Machines

Now we can throw more machines at the problem!  If we can throw multiple machines at the problem, we can process the
whole world!

---
# Even Better Attempt:  Multiple Workers Across Multiple Machines

Pros:

* The ultimate in scalability; we can always add more capacity.
* Able to handle very large workloads.
* Can be made to be fault-tolerant.

---
# Even Better Attempt:  Multiple Workers Across Multiple Machines

Cons:

* We need to figure out communication.
* We need some way of handling failures.
* Networks are way slower than local memory access.

---

# How Does Spark Fit In?

* It provides a way to express computations that appears single threaded.
* It provides a planner that can optimize and parallelize operations.
* It provides a way to distribute work to workers.
* It provides primitives for distributed storage to support computation.

---

# History Lesson:  MapReduce

* Problems can are "embarrassingly parallel" are problems that have 0 contention; they operate with completely 
independently.
* Map/reduce is an example of one such algorithm.
* Google published a paper about the benefits of a distributed map/reduce engine.  This paper inspired the creation of Hadoop.

---

# History Lesson:  MapReduce

* Expressing all problems, such as SQL queries, in MR is really difficult and verbose.
* Hadoop assumed that all data was streaming to and from a hard drive, sometimes causing IO bottlenecks.

---

# Spark Primitives

* All data is stored in Resilient Distributed Datasets (RDDs), which could reside in memory, on disk, or both.
* RDDs are immutable.
* RDDs provide map/reduce functions.
* Operations are lazy and run when output is requested, allowing Spark to optimize.

---

# It Gets Cooler

* Spark provides DataSets, which are very similar to Pandas' DataFrames.
* Allows for aggregate operations, joins, etc.
* Also lazy, allowing Spark to optimize.
* DataSet operations are more like SQL queries than Python code.  Spark gets to decide the best way to achieve the desired result.

---

# It Gets Even Cooler

* You can provide your own functions to distribute in Python, Scala, or Java.
* Commercial products, such as AWS's Elastic MapReduce (EMR) allow you to quickly start a Spark cluster at scale.
* You can run Spark locally and it'll distribute work across all cores of your local machine.

---

# Bits That I'm Intentionally Ignoring

* There's tons of discussion to be had about the different ways to run Spark in a distributed manor.

---

# Examples

* The code repo for this presentation contains Jupyter Notebooks and a docker-compose file.
* If you have Docker and docker-compose installed, it's as simple as: `docker-compose up`

---

# Questions?