# Apache Spark with WASP

WASP is a workload-aware task scheduler and partitioner for in-memory MapReduce framework.

## What is WASP
WASP jointly optimizes Npartitions and Nthreads at runtime, which parameters are defined as:

- Npartitions: how many data partitions are created from a single RDD
- Nthreads: how many threads are allocated to a single executor

Spark often suffers performance degradation with suboptimal Npartitions and Nthreads parameters. Usually, these two parameters are set empirically by users, which yield suboptimal performance due to too high memory pressure or underutilization of concurrency. WASP monitors memory pressure and concurrency at runtime and dynamially tunes the Npartitions and Nthreads, which achieves much faster execution time and high resource utilization.

## How to Operate?
* Add 3 options in HiBench (or other configuration file)
  - spark.input.size: estimated data size in hadoop (or other DFS)
  - spark.total.executor.number: total number of executors in your cluster
  - spark.total.core.number: total number of cores in one executor

* Possible Spark version
  - 1.6.1, 2.0.1

* Possible benchmark
  - WordCount, Bayes, Kmeans, TeraSort, Sort, PageRank (HiBench v5.0)
