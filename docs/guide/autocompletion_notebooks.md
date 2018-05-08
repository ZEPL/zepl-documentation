# Autocompletion in ZEPL

## How to use autocompletion in ZEPL

* `ctrl + .` : autocompletion shortcut

ZEPL supports autocompletion for Python, Spark, and SQL. To begin using the autocompletion feature, simply the run the paragraph you're working on. You can run the paragraph after you select the interpreter you want to use.

<img src="../../img/autocompletion_demo.gif" class="image-box big-img" />

<br>
Don't forget that before you use the autocompletion feature, first run the paragraph.
If you see a warning message, check that the notebook or paragraph has run. You can do this by checking both the paragraph and the container status.
<img src="../../img/autocompletion_error_message.png" class="image-box big-img" />

<br>

## Supported Interpreter Type

Here is the list of interpreters and their specific autocompletion supported features.

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