## Pypoloniex
<i>Python wrapper for calling cryptocurrency data from Poloniex API</i>

[![PyPI version](https://badge.fury.io/py/pypoloniex.svg)](https://badge.fury.io/py/pypoloniex)
![Dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg)
[![GitHub Issues](https://img.shields.io/github/issues/Crypto-AI/Pypoloniex.svg)](https://github.com/Crypto-AI/pypoloniex/issues)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)


## Install
```python
pip install pypoloniex
```

## Code Examples

#### Get Coin Information in Realtime

```python
from pypoloniex import LoadPairs

# Load realtime data from Poloniex
sess = LoadPairs()

# Returns coin object
LTC = sess.getPair(market = 'BTC', coin = 'LTC')

# Quickview
print LTC
```

```text
Coin: LTC | Last Price: 0.00381908 btc
          | Percent Change: 1.155355% btc
          | ---
          | Low 24hr: 0.00333333 btc
          | High 24hr: 0.00386786 btc
          | ---
          | Base Volume: 985.88726255 btc
          | Quote Volume: 262468.09577289 ltc
```

```python
# All Coin object attributes
print LTC.id
print LTC.coin
print LTC.market
print LTC.lowestAsk
print LTC.low24hr
print LTC.highestBid
print LTC.high24hr
print LTC.last
print LTC.percentChange
print LTC.baseVolume
print LTC.quoteVolume
print LTC.isFrozen
```

```text
50
LTC
BTC
0.00381900
0.00333333
0.00381581
0.00386786
0.00381908
0.01155355
985.88726255
262468.09577289
0
```

#### Get Time Series Data

```python
# Create TimeSeries object
sess = TimeSeries()

# Parameters
pair = ('BTC', 'LTC')	 # (market, coin)
period = 86400           # candle stick period in seconds
start = '4/2/2014'		 # dd/mm/year
end =  '11/2/2014'       # dd/mm/year

# Get time series data from Poloniex and load into pandas dataframe
sess.getData(pair, period, start, end)

# Show dataframe with parameters
sess.show()
```

```text
Variables
Pair: ('BTC', 'LTC')
Period: 86400
Start: 4/2/2014
End: 11/2/2014

                  date    open     low    high   close  weightedAverage     volume  quoteVolume
0  04/02/2014 19:00:00  0.0252  0.0212  0.0268  0.0267         0.023584  10.866362   460.749730 
1  05/02/2014 19:00:00  0.0267  0.0250  0.0276  0.0266         0.025958   1.733980    66.798961  
2  06/02/2014 19:00:00  0.0276  0.0028  0.0276  0.0269         0.025350   8.315254   328.018899 
3  07/02/2014 19:00:00  0.0268  0.0203  0.0268  0.0263         0.025250   3.234224   128.087917 
4  08/02/2014 19:00:00  0.0263  0.0242  0.0263  0.0261         0.025720   2.392802    93.031692  
5  09/02/2014 19:00:00  0.0261  0.0248  0.0261  0.0261         0.025562   2.367759    92.628872  
6  10/02/2014 19:00:00  0.0256  0.0248  0.0262  0.0259         0.025384   2.292572    90.315636   
```

```python
# Export dataframe to csv
sess.toCSV('data.csv')

# Import dataframe from csv
sess = TimeSeries()
sess.fromCSV('data.csv')

# Return dataframe from TimeSeries object for manipulation
df = sess.data
```

#### Available Trading Pairs from Poloniex
```text
| BTC, RBY       | BTC, GRC       | BTC, BLK      | BTC, BBR       | XMR, NXT       
| BTC, UNITY     | BTC, NXC       | BTC, XRP      | BTC, XMR       | XMR, BLK       
| BTC, PINK      | BTC, BTCD      | BTC, NEOS     | BTC, SJCX      | XMR, ZEC       
| BTC, SYS       | BTC, LTC       | BTC, QBK      | BTC, VIA       | XMR, QORA      
| BTC, EMC2      | BTC, DASH      | BTC, BTS      | BTC, XEM       | XMR, DASH      
| BTC, C2        | BTC, NAUT      | BTC, DOGE     | BTC, NMC       | XMR, BBR       
| BTC, RADS      | BTC, ZEC       | BTC, SBD      | BTC, SDC       | XMR, BTCD      
| BTC, SC        | BTC, BURST     | BTC, XCP      | BTC, ARDR      | XMR, MAID      
| BTC, MAID      | BTC, XVC       | BTC, BTM      | BTC, HZ        | XMR, LTC       
| BTC, BCN       | BTC, BELA      | BTC, OMNI     | BTC, FLO       | XMR, BCN       
| BTC, REP       | BTC, STEEM     | BTC, NAV      | BTC, GAME      | USDT, REP      
| BTC, BCY       | BTC, ETC       | BTC, VOX      | BTC, PPC       | USDT, ZEC      
| BTC, FCT       | BTC, ETH       | BTC, XBC      | BTC, FLDC      | USDT, ETH      
| BTC, LBC       | BTC, CURE      | BTC, DGB      | BTC, MYR       | USDT, BTC      
| BTC, DCR       | BTC, HUC       | BTC, NOTE     | BTC, NSR       | USDT, ETC      
| BTC, AMP       | BTC, STRAT     | BTC, BITS     | BTC, IOC       | USDT, DASH     
| BTC, XPM       | BTC, LSK       | BTC, VRC      | ETH, STEEM     | USDT, NXT      
| BTC, NOBL      | BTC, EXP       | BTC, RIC      | ETH, ZEC       | USDT, LTC      
| BTC, NXT       | BTC, CLAM      | BTC, XMG      | ETH, REP       | USDT, XMR      
| BTC, VTC       | BTC, QORA      | BTC, STR      | ETH, LSK       | USDT, XRP      
| BTC, PASC      | BTC, QTL       | BTC, POT      | ETH, ETC       | USDT, STR  
```
