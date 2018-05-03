# Autocompletion in ZEPL

## How to use autocompletion in ZEPL

* `ctrl + .` : autocompletion shotcut

The Code Autocompletion can use in ZEPL notebook. When you code in Python, Spark and SQL, The Autocompletion in notebook support a better environment.

<img src="../../img/autocompletion_demo.gif" class="image-box big-img" />

<br>
Don't forget that before you use autocompletion feature, the notebook should `run` at first.
If you find warning messsage, check to run notebook.
<img src="../../img/autocompletion_error_message.png" class="image-box big-img" />

<br>

## Supported Interpreter Type

Before starting to use it, please check autocompletion supported interpreter such as Apache Spark, Python, JDBC Interpreter.

<br>
#### Spark Interpreter
| symbol  | autocompletion supported | Type |
| --- | --- | --- |
| `%spark`  | supported | SparkInterpreter - Provides a Scala environment |
| `%pyspark` | supported | PySparkInterpreter - Provides a PySpark environment |
| `%ipyspark`  | supported | IPySparkInterpreter |
| `%dep`  | supported | DepInterpreter - Load dependency libraries into Spark environment |
| `%sql`  | X | SparkSqlInterpreter - Provides SparkSQL environment |
| `%r`  | X | SparkRInterpreter - Provides R environment |

<br>
#### Python Interpreter
| symbol  | autocompletion supported | Type |
| --- | --- | --- |
| `%python`  | supported | PythonInterpreter - Provides a Python environment |
| `%ipython` | supported | IPythonInterpreter - Provides a iPython environment |
| `%conda`  | X | PythonCondaInterpreter - Provides a [Conda](https://conda.io/docs/) enviroment |
| `%sql`  | X | PythonInterpreterPandasSql - Provides [pandasql](https://pypi.python.org/pypi/pandasql) environment |

<br>
#### JDBC Interpreter
| symbol  | autocompletion supported | Type |
| --- | --- | --- |
| `%sql`  | supported | JDBC interpreter with drivers for popular databases. |