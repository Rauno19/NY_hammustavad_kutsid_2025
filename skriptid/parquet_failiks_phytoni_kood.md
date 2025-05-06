````bash
import pandas as pd
import argparse 
````
Read in data from Excel (requires openpyxl). Adjust the filename as needed:
````bash
df = pd.read_csv('../andmestikud/andmestiku_nimi.csv', decimal=',')
````
NB! If by some reason code doesn't work try saving .csv file as .txt and then read it it with following command 
````bash
df = pd.read_csv('../andmestikud/andmestiku_nimi.txt', decimal=',', sep=';')
````
Optional part:
Rename date-related columns (optional, but helpful for clarity).
````bash
df = df.rename(columns={'DateOfBite': 'Date'})
````
Merge date information into a single DateTime column, and drop the originals.
Optional part:
````bash
df['DateTime'] = pd.to_datetime(
    df['year'].astype(str) + '-' + df['month'].astype(str) + '-' + df['day'].astype(str) + ' ' + df['time'].astype(str),
    format='%Y-%m-%d %H:%M:%S', 
    utc=True
)
df = df.drop(columns=['year', 'month', 'day', 'time'])
````
Export to Parquet
````bash
df.to_parquet('.../andmestikud/andmestiku_nimi.parquet', index=False)
````