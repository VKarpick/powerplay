# Quantifying PK Aggression

powerplay_coords.csv has some columns containing tuples. Not a good way to store data, but was the easiest way to work with it. To read the file properly into a pandas DataFrame:
```
from ast import literal_eval
import pandas as pd

def literal_converter(x):
    return pd.NA if x == "" else literal_eval(x)
    
df = pd.read_csv(
    "https://github.com/VKarpick/powerplay/blob/main/data/powerplay_coords.csv?raw=true",
    converters={
        c: literal_converter
        for c in ("possession_coord", "opponent_coords", "goalie_coord")
    }
)
```
