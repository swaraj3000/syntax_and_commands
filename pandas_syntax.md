## Reading Large Files

### Chunking
In chunking, we read files in small chunks. It is similar to the way we eat big burger or any big item, instead of eating all at once, we eat small cores.
```
import pandas as pd

chunksize = 1000
for chunk in pd.read_csv('large_file.csv', chunksize=chunksize):
    # process each chunk here
```
