## Reading Large Files

### Chunking
In chunking, we read files in small chunks. It is similar to the way we eat big burger or any big item, instead of eating all at once, we eat small cores.
``` python
import pandas as pd

chunksize = 1000
for chunk in pd.read_csv('large_file.csv', chunksize=chunksize):
    # process each chunk here
```

In this example, the read_csv function will return an iterator that yields data frames of 1000 rows each. You can then process each chunk separately within the for loop.



### Dask 
Dask is a distributed computing library that provides parallel processing capabilities. Dask can handle data sets that are larger than the available memory by partitioning the data and processing it in parallel across multiple processors or machines.
```
pip install dask[complete]
```

``` python
import dask.dataframe as dd
df = dd.read_csv('large_file.csv') 
```

One advantage of using Dask is that it can handle much larger datasets than Pandas. Dask can process data sets that are larger than the available memory by using disk storage and partitioning the data across multiple processors or machines.


### Use Compression
To reduce memory usuage we can directly read from compressed file. 
Ex - 
``` python
import pandas as pd

df = pd.read_csv('large_file.csv.gz', compression='gzip')
```
In the above approach, it will decompress the file on fly. 


## Different Operations in DataFrame

### Data Manipulation Functions:

* merge() and concat(): Used for combining DataFrames either by merging on specific columns (merge()) or concatenating along an axis (concat()).
* join(): Similar to merge() but used for combining DataFrames on their indexes.
append(): Appends rows of one DataFrame to another.
Use Case: When you need to combine data from multiple DataFrames based on common columns or indexes.

### Data Aggregation Functions:

* groupby(): Used to split data into groups based on some criteria and then apply a function (e.g., sum, mean, count) to each group independently.
* agg(): Aggregates data using one or more operations over the specified axis.
* pivot_table(): Creates a spreadsheet-style pivot table as a DataFrame.
Use Case: When you need to summarize or aggregate data over groups or categories.

### Data Selection and Filtering Functions:

* Boolean Indexing ([]): Selects subsets of data based on boolean conditions.
* loc[] and iloc[]: Used for label-based and integer-based indexing, respectively.
* query(): Provides a SQL-like interface for selecting data.
Use Case: When you need to filter rows or select specific subsets of data based on conditions.

### Data Transformation Functions:

* apply(): Applies a function along an axis of the DataFrame.
* map(): Used for element-wise mapping of values.
* transform(): Applies a function to each group and returns a DataFrame with the same shape as the original.
Use Case: When you need to perform custom transformations on data or manipulate values within a DataFrame.

### Data Cleaning and Handling Missing Values:

* fillna(): Fills missing values with specified methods or values.
* dropna(): Drops rows or columns with missing values.
* interpolate(): Interpolates missing values.
Use Case: When dealing with missing or incomplete data.

### Data I/O Functions:

* read_csv(), read_excel(), read_sql(): Reads data from various file formats or databases.
* to_csv(), to_excel(), to_sql(): Writes data to various file formats or databases.
* Use Case: Importing and exporting data from/to different sources.

### Data Sorting and Ranking:

* sort_values(): Sorts the DataFrame by specified column(s).
* sort_index(): Sorts the DataFrame by index.
* rank(): Computes numerical data ranks along the specified axis.

### Data Reshaping and Transformation:

* melt(): Unpivots DataFrame from wide to long format.
* pivot(): Reshapes DataFrame from long to wide format.
* stack() and unstack(): Reshapes hierarchical indexing from DataFrame to Series or vice versa.

### Time Series and Date Functionality:

* to_datetime(): Converts the input to datetime.
* resample(): Converting the frequency of time series data.
* rolling(): Provides rolling window calculations.

### Statistical Functions:

* describe(): Generates descriptive statistics of DataFrame or Series.
* cov(): Computes covariance between DataFrame columns.
* corr(): Computes correlation between DataFrame columns.


### String Functions:

* str.contains(): Checks whether a string contains a substring.
* str.replace(): Replaces occurrences of pattern/substring with another pattern/substring.
* str.extract(): Extracts matched groups from the strings in the DataFrame.


### Visualization:

* plot(): Creates basic plots like line, bar, scatter, etc.
* hist(), boxplot(), scatter_matrix(): Creates histogram, box plot, and scatter matrix, respectively.


### Statistical Testing:

* ttest_ind(): Performs independent samples t-test.
* anova(): Performs analysis of variance (ANOVA).

### Categorical Data Functions:

* astype(): Converts the data type of a column to a specified type.
* astype('category'): Converts a column to a categorical data type.
* value_counts(): Returns counts of unique values in a column.


[Reference](https://saturncloud.io/blog/how-to-efficiently-read-large-csv-files-in-python-pandas/)
