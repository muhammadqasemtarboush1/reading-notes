# Class 12

## Pandas

### What is Pandas

 is an open source, BSD-licensed library providing high-performance,
 easy-to-use data structures and data analysis tools for the Python
 programming language.

### Installation

> conda:
>
> conda install pandas
>
> pip install
>
> pip install pandas
>
> import pandas Like the following:
>
> import pandas as pd
>

* ### What kind of data does pandas handle?

  * A DataFrame : is a 2-dimensional data structure that can store data of
  different types (including characters, integers, floating point values,
  categorical data and more) in columns. It is similar to a spreadsheet,
a SQL table or the data.frame in R.
  * The describe() method provides a quick overview of the numerical data in a
  * DataFrame

* ### How do I read and write tabular data?

  * read_csv(): It's a function to read data stored as a csv file into a pandas
  DataFrame. pandas supports many different file formats or data sources out
  of the box (csv, excel, sql, json, parquet, …), each of them with the prefix
  read_*.
  * head() method To see the first N rows of a DataFrame, with the required number
  of rows.
  * dtypes attribute: check on how pandas interpreted each of the
  column data types.
  * to_* :  methods are used to store data Whereas read_* functions are used to
  read data to pandas.
  * to_excel() method: stores the data as an excel file.
    * ex:

    ```python
    titanic.to_excel("titanic.xlsx", sheet_name="passengers", index=False)
    ```

    * info() : method provides technical information about a DataFrame

#### Summary

* Getting data in to pandas from many different file formats or data sources
is supported by read_* functions.

* Exporting data out of pandas is provided by different to_*methods.

* The head/tail/info methods and the dtypes attribute are convenient for a
first check.

* ### How do I select a subset of a DataFrame?

How do I select specific columns from a DataFrame?

* DataFrame.shape is an attribute : (do not use parentheses for attributes,)
of a pandas Series and DataFrame containing the number of rows and columns:
(nrows, ncolumns). A pandas Series is 1-dimensional and only the number of
rows is returned.
* To select multiple columns, use a list of column names within the selection
brackets [].
* The loc/iloc operators are required in front of the selection brackets [].
When using loc/iloc, the part before the comma is the rows you want, and the
part after the comma is the columns you want to select.
* Summary:
  * When selecting subsets of data, square brackets [] are used.
  * Inside these brackets, you can use a single column/row label, a list of
  column/row labels, a slice of labels, a conditional expression or a colon.
  * Select specific rows and/or columns using loc when using the row and column
  names
  * Select specific rows and/or columns using iloc when using the positions in
  the table
  * You can assign new values to a selection based on loc/iloc.

* ### How to create plots in pandas?

  * Summary:
    * The .plot.* methods are applicable on both Series and DataFrames
    * By default, each of the columns is plotted as a different element
      (line, boxplot,…)
    * Any plot created by pandas is a Matplotlib object.

* ### How to create new columns derived from existing columns?

  * Summary:
    * Create a new column by assigning the output to the DataFrame with
      a new column name in between the [].
    * Operations are element-wise, no need to loop over rows.
    * Use rename with a dictionary or function to rename row labels or
      column names.

* ### How to calculate summary statistics?

  * Summary:
    * Aggregation statistics can be calculated on entire columns or rows  
    * groupby provides the power of the split-apply-combine pattern
    * value_counts is a convenient shortcut to count the number of entries
    in each category of a variable

* ### How to reshape the layout of tables?

  * Summary:
    * Sorting by one or more columns is supported by sort_values
    * The pivot function is purely restructuring of the data, pivot_table supports aggregations
    * The reverse of pivot (long to wide format) is melt (wide to long format)

* ### How to combine data from multiple tables?

  * Summary:
    * Multiple tables can be concatenated both column-wise and row-wise using the concat function.
    * For database-like merging/joining of tables, use the merge function.

* ### How to handle time series data with ease?

  * Summary:
    * Valid date strings can be converted to datetime objects using to_datetime
    function or as part of read functions.
    * Datetime objects in pandas support calculations, logical operations and
    convenient date-related properties using the dt accessor.
    * A DatetimeIndex contains these date-related properties and supports
    convenient slicing.
    * Resample is a powerful method to change the frequency of a time series.

* ### How to manipulate textual data?

  * Summary:
    * String methods are available using the str accessor.
    * String methods work element-wise and can be used for conditional indexing.
    * The replace method is a convenient method to convert values according to
    a given dictionary.

---

## Notes

* If you are familiar to Python dictionaries, the selection of
a single column is very similar to selection of dictionary values
based on the key.

---

* Interested in the last N rows instead? pandas also provides a tail()
method. For example, titanic.tail(10) will return the last 10 rows of the
DataFrame.

---

* When asking for the dtypes, no brackets are used! dtypes is an attribute of
a DataFrame and Series. Attributes of DataFrame or Series do not need brackets.
Attributes represent a characteristic of a DataFrame/Series, whereas a method
(which requires brackets) do something with the DataFrame/Series as introduced
in the first tutorial.

---

* Each column in a DataFrame is a Series. As a single column is selected, the
returned object is a pandas Series.

---

* The inner square brackets define a Python list with column names,
whereas the outer brackets are used to select the data from a pandas
DataFrame as seen in the previous example.

---

## Source

## [User Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)

## [Get Started With Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html)
