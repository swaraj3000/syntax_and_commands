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


[Reference](https://saturncloud.io/blog/how-to-efficiently-read-large-csv-files-in-python-pandas/)
