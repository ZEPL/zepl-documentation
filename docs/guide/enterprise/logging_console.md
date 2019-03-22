# The Log Console in Zepl

Zepl provides a *Log Console* for a given notebook that the user can open to view the interpreter logs. The output stream in the *Log Console* will be specific to the given notebook and its interpreters.

## How to Use the Log Console

Zepl provides the *Log Console* for Python, Spark and JDBC interpreters. To begin using it simply run the paragraph you're working on. It's located at the bottom of the notebook and can be opened by clicking on the *Console* tab. If you shutdown the notebook the *Log Console* will be closed automatically.

<img src="../../../img/logging_console_demo.gif" class="image-box big-img" />     
 
> Note: You will only see log output in the *Log Console* if the notebook is running. 

## About Log Console Contents

The interpreter logs are based on the [Apache Zeppelin Interpreter](https://zeppelin.apache.org/docs/0.8.0/usage/interpreter/overview.html) log with the following output:

- timestamp: [ISO8601](https://en.wikipedia.org/wiki/ISO_8601)
- log level: `INFO`, `ERROR`, `WARN`
- thread: the name of the thread that generated the logging event
- message: the application supplied message associated with the logging event

The following is some sample Spark Interpreter log output in the *Log Console*:
```
...
[2018-09-04 15:46:46,483Z] INFO (pool-2-thread-4) | Job 13121f1eca... finished by scheduler interpreter
[2018-09-04 15:46:45,070Z] INFO (event-loop)      | Created broadcast 0 
[2018-09-04 15:46:45,074Z] INFO (event-loop)      | Submitting 4 missing tasks from ShuffleMapStage 0
[2018-09-04 15:46:45,076Z] INFO (event-loop)      | Adding task set 0.0 with 4 tasks
[2018-09-04 15:46:45,128Z] INFO (event-loop-3)    | Starting task 0.0 in stage 0.0 (TID 0, 124008 bytes)
[2018-09-04 15:46:45,134Z] INFO (event-loop-3)    | Starting task 1.0 in stage 0.0 (TID 1, 123915 bytes)
...
[2018-09-04 15:46:45,156Z] INFO (worker for task 0) | Running task 0.0 in stage 0.0 (TID 0)
[2018-09-04 15:46:45,156Z] INFO (worker for task 3) | Running task 3.0 in stage 0.0 (TID 3)
...
[2018-09-04 15:46:45,164Z] INFO (worker for task 2) | Fetching spark
[2018-09-04 15:46:46,131Z] INFO (worker for task 2) | Finished task 2.0 in stage 0.0 (TID 2). 1968 bytes
...
```