# Python Interpreter

[Python](https://www.python.org/) is a general purpose programming language which is becoming increasingly popular among data analysts and data scientists due to the strength of its core libraries, simple data structures and growing wealth of packages and modules catering to data science, ML and AI.

Zepl provides a Python interpreter with the following popular  libraries pre-installed:

 * [numpy](http://www.numpy.org/): a scientific computing library designed to efficiently manipulate large multi-dimensional arrays
 * [scipy](https://www.scipy.org/): a library that provides a large number of operations for scientific and engineering computing
 * [pandas](http://pandas.pydata.org/): an easy-to-use data structuring tool for data analysis
 * [pandasql](https://pypi.python.org/pypi/pandasql): a data manipulation tool using SQL syntax built on top of pandas Dataframes
 * [matplotlib](http://matplotlib.org/): a 2D plotting library
 * [Pillow](https://python-pillow.org/): Python Image Library supporting image manipulation of many different image file formats
 * [boto3](http://boto3.readthedocs.io/en/latest/): AWS SDK for Python
 * [scikit-learn](http://scikit-learn.org/): a Machine Learning toolkit for data mining and analysis
 * [tensorflow](https://www.tensorflow.org/): a machine intelligent library that helps developer to design, build, and train deep learning models easily

## Pip

Install additional libraries using `pip`. 

Usage

```
%python
!pip install [packages]
```

Example:

```
%python
!pip install -q keras
import keras
```

The `pip` command installs packages in the current environment. If another environment is activated, it will install packages in the particular environment activated. Check the next section to create and switch multiple python environments.

## Managing Python Environments

If you'd like to install additional environments you can use the `conda` interpreter bundled with the Python interpreter. [Conda](https://conda.io/docs/) is open an source package and environment management system which enables easy package installation and environment switching.

### Usages

Get `conda` information
```
%python.conda info
```
List your environments
```
%python.conda env list
```
Create an environment
```
%python.conda create --name [ENV_NAME]

# or if you want to specify python version (e.g 3.6)
%python.conda create --name [ENV_NAME] python=3.6
```
Activate an environment
```
%python.conda activate [ENV_NAME]
```
Deactivate an environment
```
%python.conda deactivate
```

List installed packages
```
%python.conda list
```
Install packages (see previous section to install packages via `pip`)
```
%python.conda install [PACKAGE1 PACKAGE2 ...]

# or if you want to specify an environment name
%python.conda install -n [ENV_NAME] [PACKAGE1 PACKAGE2 ...]
```
Uninstall packages
```
%python.conda uninstall [PACKAGE1 PACKAGE2 ...]
```
Help
```
%python.conda help
```


## IPython Support

You can use [IPython commands](http://ipython.readthedocs.io/en/stable/interactive/tutorial.html) with the default Python interpreter in Zepl as shown below:

```python
%python

# !ls Run a shell command.
# Install additional packages
!pip install keras

# object? Details about the object
help?

# Time execution of a Python statement or expression
%timeit range(1000)
```
