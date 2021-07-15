# Notes
Notes for different packages in Python.

## python basics
1. Move a file:
```
os.rename(source,destination)
```
2. Get a list of filenames in directory:
```
file_namelist = [os.path.basename(filepath) for filepath in glob.glob(./Directory/*)]
```
## pandas
1. Change column names:
```
df.columns = ['x','y',...]
```
2. Calculate daily return:
```
df['Daily Return'] = df['Close'].pct_change(1)
```
3. Change from timestamp (ms) to UTC date:
```
df['Date'] = df.apply(lambda x: datetime.datetime.utcfromtimestamp(x['Date']/1000), axis=1).strftime('%Y-%m-%d')
```
4. Change from timestamp (s) to UTC date:
```
df['Date'] = df.apply(lambda x: datetime.datetime.utcfromtimestamp(x['Date']), axis=1).strftime('%Y-%m-%d')
```
## ccxt
1. Get a exchange object by corresponding exchange ID:
```
exchange = getattr(ccxt, exchangeid)({
    'enableRateLimit': True,
})
```
2. Load exchange markets (essential for further operations):
```
exchange.load_markets()
```
3. Get exchange's available symbols (e.g 'BTC/USDT'):
```
symbols = exchange.symbols()
```
4. Fetch ohlcv data:
```
ohlcv = exchange.fetch_ohlcv(symbol='BTC/USDT', timeframe='1d', since='2013-04-28T18:47:21.000Z', limit=100)
df = pd.Dataframe(ohlcv, columns=['timestamp', 'Open', 'High', 'Low', 'Close', 'Volumn']
```
## torch

## pickle
1. Store a variable into a pickle file for further use:
```
with open('./pickle.pk', 'wb') as fi:
  pickle.dump(variable, fi)
```
2. Retrieve a variable from a pickle file:
```
with open('./pickle.py', 'rb') as fi:
  var = pickle.load(fi)
```
## datetime
























