# Class 11

## Jupyter

### What is Jupyterlab

JupyterLab is a next-generation web-based user interface for Project Jupyter.
JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner

### Installation

> conda install -c conda-forge jupyterlab
>
> mamba install -c conda-forge jupyterlab
>
> pip install jupyterlab
>
> pipenv install jupyterlab <br/>
pipenv shell

### Some Features

* Code Consoles provide transient scratchpads for running code interactively, with full support for rich output. A code console can be linked to a notebook kernel as a computation log from the notebook, for example.

* Kernel-backed documents enable code in any text file (Markdown, Python, R, LaTeX, etc.) to be run interactively in any Jupyter kernel.

* Notebook cell outputs can be mirrored into their own tab, side by side with the notebook, enabling simple dashboards with interactive controls backed by a kernel.

* Multiple views of documents with different editors or viewers enable live editing of documents reflected in other viewers. For example, it is easy to have live preview of Markdown, Delimiter-separated Values, or Vega/Vega-Lite documents.

## [For More You can visit the Source click Here](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)

---

## NumPy

### What is NumPy?

It is  Python package which stands for Numerical Python, is a library consisting of multidimensional array objects and a
collection of routines for processing those arrays. Using NumPy, mathematical and logical operations
on arrays can be performed.

### Installation & Environment

* > pip install numpy
* > The best way to enable NumPy is to use an installable binary package specific to your operating system. These binaries contain full SciPy stack (inclusive of NumPy, SciPy, matplotlib, IPython, SymPy and nose packages along with core Python).

* > You can import it by doing the following:

```python
import numpy
# If it is not installed, the following error message will be displayed.
Traceback (most recent call last):
File "<pyshell#0>", line 1, in <module>
import numpy
ImportError: No module named 'numpy'

# Alternatively, NumPy package is imported using the following syntax −
import numpy as np
```

 To Know More You Can visit:
[Environment implemented](https://www.tutorialspoint.com/numpy/numpy_environment.htm)

### NumPy in Data Analysis with Python

#### Numpy 2-Dimensional Arrays

With NumPy, we work with multidimensional arrays. We’ll dive into all of
the possible types of multidimensional arrays later on, but for now, we’ll
focus on 2-dimensional arrays. A 2-dimensional array is also known as a
matrix, and is something you should be familiar with. In fact, it’s just a
different way of thinking about a list of lists. A matrix has rows and
columns

#### Creating A NumPy Array

We can create a NumPy array using the numpy.array function.
If we pass in a list of lists, it will automatically create a NumPy array
with the same number of rows and columns. Because we want all of the
elements in the array to be float elements for easy computation, we’ll
leave off the header row, which contains strings. One of the limitations
of NumPy is that all the elements in an array have to be of the same type,
so if we include the header row, all the elements in the array will be read
in as strings

> Example:

```python
'''
In the below code, we:
Import the numpy package.
Pass the list of lists wines into the array function, which converts it into a NumPy array.
    Exclude the header row with list slicing.
    Specify the keyword argument dtype to make sure each element is converted to a float. We’ll dive more into what the dtype is later on.
'''
import csv
with open("winequality-red.csv", 'r') as f:
    wines = list(csv.reader(f, delimiter=";"))
import numpy as np
wines = np.array(wines[1:], dtype=np.float)
  ```

#### Alternative NumPy Array Creation Methods

There are a variety of methods that you can use to create NumPy arrays.
To start with, you can create an array where every element is zero.
It’s useful to create an array with all zero elements in cases when
you need an array of fixed size, but don’t have any values for it yet.
You can also create an array where each element is a random number
using numpy.random.rand.

#### Using NumPy To Read In Files

It’s possible to use NumPy to directly read csv or other files into arrays.
We can do this using the numpy.genfromtxt function.

```python
'''
In the below code, we:
Use the genfromtxt function to read in the winequality-red.csv file.
Specify the keyword argument delimiter=";" so that the fields are parsed properly.
Specify the keyword argument skip_header=1 so that the header row is skipped.
'''
wines = np.genfromtxt("winequality-red.csv", delimiter=";", skip_header=1)

```

#### Indexing NumPy Arrays

We now know how to create arrays, but unless we can retrieve results
from them, there isn’t a lot we can do with NumPy. We can use array
indexing to select individual elements, groups of elements, or entire
rows and columns. One important thing to keep in mind is that just like
Python lists, NumPy is zero-indexed, meaning that the index of the first
row is 0, and the index of the first column is 0.

#### Slicing NumPy Arrays

If we instead want to select the first three items from the fourth column,
we can do it using a colon (:). A colon indicates that we want to select
all the elements from the starting index up to but not including the ending
index.

#### Assigning Values To NumPy Arrays

```python
# We can also use indexing to assign values to certain elements in arrays. We can do this by assigning directly to the indexed value:
wines[1,5] = 10
# We can do the same for slices. To overwrite an entire column, we can do this:
wines[:,10] = 50
# The above code overwrites all the values in the eleventh column with 50.
```

And There Is Much Much More
You can see free CheetSheet [sheets](https://s3.amazonaws.com/dq-blog-files/numpy-cheat-sheet.pdf)
And the Sources for this Summary:

* [numpy-tutorial-python](https://www.dataquest.io/blog/numpy-tutorial-python/)
* [NumPy Tutorial](https://www.tutorialspoint.com/numpy/index.htm)

## Notes

* In a NumPy array, the number of dimensions is called the rank,
and each dimension is called an axis. So the rows are the first axis,
and the columns are the second axis.

## Things I want to know more about

* jupyter Real Used Case
* Give NumPy good time to understand it and practical examples.
