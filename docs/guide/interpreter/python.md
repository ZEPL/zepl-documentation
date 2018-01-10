<h1> Python Interpreter </h1>

[Python](https://www.python.org/) is general-purpose programming language which is getting increasingly popular among data analysts and data scientists due to the strength of its core libraries, data wrangling.

ZEPL provides python interpreter with popular python libraries pre-installed:

 * [numpy](http://www.numpy.org/): Scientific computing library designed to efficiently manipulate large multi-dimensional arrays
 * [scipy](https://www.scipy.org/): Library that provides large number of operations for scientific and engineering computing
 * [pandas](http://pandas.pydata.org/): Easy-to-use data structuring tool for data analysis
 * [pandasql](https://pypi.python.org/pypi/pandasql): Data manipulating tool using SQL syntax built on top of pandas Dataframe.
 * [matplotlib](http://matplotlib.org/): 2D plotting library
 * [Pillow](https://python-pillow.org/): Python Image Library supporting image manipulation of many different image file format
 * [boto3](http://boto3.readthedocs.io/en/latest/): AWS SDK for python
 * [scikit-learn](http://scikit-learn.org/): Machine Learning tool for data mining ad data analysis
 * [tensorflow](https://www.tensorflow.org/): Machine intelligent library helps developer to design, build, and train deep learning models easily

## Manage Python Environment

If you need different environment other than the default environment or external packages, you can use conda interpreter bundled with python interpreter. [Conda](https://conda.io/docs/) is open source package and environment management system helps easy package installation and environment switch.

Usages

Get conda information
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
%%python.conda create --name [ENV_NAME] python=3.6
```
Activate the environment
```
%python.conda activate [ENV_NAME]
```
Deactivate the environment
```
%python.conda deactivate
```
List installed package
```
%python.conda list
```
Install packages
```
%python.conda install [PACKAGE1 PACKAGE2 ...]
```
Uninstall packages
```
%python.conda uninstall [PACKAGE1 PACKAGE2 ...]
```
Help
```
%python.conda help
```
