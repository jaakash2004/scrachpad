
## Swifter

Swifter is a library which, “applies any function to a pandas dataframe or series in the fastest available manner.”

```import pandas as pd
import swifter

df.swifter.apply(lambda x: x.sum() - x.min())
```
[https://towardsdatascience.com/one-word-of-code-to-stop-using-pandas-so-slowly-793e0a81343c](https://towardsdatascience.com/one-word-of-code-to-stop-using-pandas-so-slowly-793e0a81343c)



> df1[df1.index.get_level_values('portb').isin([389]) & df1.index.get_level_values('portb').isin([445])]
