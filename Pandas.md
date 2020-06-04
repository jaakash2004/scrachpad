
# Pandas Basics

### Pandas Groupby

Get all the keys in the group:
```df2.groups.keys()```

Get All groups and process as dataframe:
```
for grp_key, grp_df in group:
    # Process Key
    # Process Group
```

#### Random Examples (Groupby)

*       
        # Aggregation Example
        adf_grp = adf.groupby(["host", "tb_fingerprint"]).agg(Customer=('customer', 'first'),
                                                          ActivityCount=('Activity', 'sum'),
                                                          NumExecution=('Activity', 'count'),
                                                          tb_name=('tb_name', 'first'))
* 
        
        
### Pandas Read data

```
df = pd.read_sql_query(f"select ipend, ipa, porta, ipb, portb, packetsa2b, bytesa2b, packetsb2a, bytesb2a, 
                        smbname, smbfilesharepath, smbfileactions, smbbytesread, smbbyteswritten from 
                        {partition} where (portb=389 or portb=445) and ipend BETWEEN '{st_time}' AND '{et_time}'", db_conn)
```

### Pandas Concat, Merge, Join
Merge
```
df9 = df7.merge(df8, how='inner', left_on=['ipend', 'ipa', 'ipb'], right_on=['ipend', 'ipa', 'ipb'])
```

### Misc Examples

Truncate (floor) date by hour/minute/sec etc
```
df2['date_column'].dt.floor("3s") # for 3 second
df2['date_column'].dt.floor("h") # for hour
```

Pandas Column has list values.
Example:
```
df = pd.DataFrame({'A': [[1, 2, 3], 'foo', [], [3, 4]], 'B': 1})
df
           A  B
0  [1, 2, 3]  1
1        foo  1
2         []  1
3     [3, 4]  1

# Normal filtering doesn't seem to work
# Use apply method like below

df.A.apply(lambda x: x == [1, 2, 3])

```

## The Best Format to Save Pandas Data

> https://towardsdatascience.com/the-best-format-to-save-pandas-data-414dca023e0d

##How to process a DataFrame with billions of rows in seconds
* Vaex Library

    * [https://towardsdatascience.com/how-to-process-a-dataframe-with-billions-of-rows-in-seconds-c8212580f447](https://towardsdatascience.com/how-to-process-a-dataframe-with-billions-of-rows-in-seconds-c8212580f447)


## Top 3 Pandas functions
[https://towardsdatascience.com/top-3-pandas-functions-you-dont-know-about-probably-5ae9e1c964c8](https://towardsdatascience.com/top-3-pandas-functions-you-dont-know-about-probably-5ae9e1c964c8)

### idxmin() and idxmax()
Used to find the index location of the smallest and largest item.

### ne()
return True if the current value isn’t the one you’ve specified (let’s say 0), and False otherwise.

### nsmallest() and nlargest()



## Efficient Pandas: Using Chunksize for Large Data Sets

[https://medium.com/towards-artificial-intelligence/efficient-pandas-using-chunksize-for-large-data-sets-c66bf3037f93](https://medium.com/towards-artificial-intelligence/efficient-pandas-using-chunksize-for-large-data-sets-c66bf3037f93)


## Swifter

Swifter is a library which, “applies any function to a pandas dataframe or series in the fastest available manner.”

```import pandas as pd
import swifter

df.swifter.apply(lambda x: x.sum() - x.min())
```
[https://towardsdatascience.com/one-word-of-code-to-stop-using-pandas-so-slowly-793e0a81343c](https://towardsdatascience.com/one-word-of-code-to-stop-using-pandas-so-slowly-793e0a81343c)



> df1[df1.index.get_level_values('portb').isin([389]) & df1.index.get_level_values('portb').isin([445])]
