# Docker Usage 
1. Login
```
docker login --username='YOUR_USERNAME@docker'
```
2. Pull Docker Image 
```
docker pull modulusmath/market_sales
```
3. Run Docker Image 
```
$ docker run -i -t modulusmath/market_sales  python3.7 market_sales.py  -s GOOG

Retrieving HTML for  GOOG
Parsing HTML
Pulling Data out of HTML

GOOG had 59,730.0 M revenue in 2013 4 GR Rate =  16.76%
GOOG had 65,830.0 M revenue in 2014 3 GR Rate =  19.03%
GOOG had 73,590.0 M revenue in 2015 2 GR Rate =  22.83%
GOOG had 89,730.0 M revenue in 2016 1 GR Rate =  23.73%
GOOG had 111,020.0 M revenue in 2017 0 GR Rate =  0.00%

GOOG had 12,160.0 M Net Income in 2013 4 GR Rate =  1.01%
GOOG had 13,400.0 M Net Income in 2014 3 GR Rate =  -1.88%

<SNIP FOR LENGTH>
```

#### OR ####

3. Run from insider  the container

```
docker run -i -t modulusmath/market_sales  bash

appuser@f308fe3de651:/$ python3.7 ./market_sales.py  -s GOOG 
Retrieving HTML for  GOOG
Parsing HTML
Pulling Data out of HTML
<SNIP FOR LENGTH>
```

## Timings: 

### Getting data from the Web

```
appuser@11f6e8db4d97:/$ time python3.7 ./market_sales.py -m web -k -s AAPL
Retrieving HTML for  AAPL
Parsing HTML
Pulling Data out of HTML

AAPL had 183,240.0 M Revenue in 2014 4 GR Rate =  9.75%
AAPL had 231,280.0 M Revenue in 2015 3 GR Rate =  4.75%

<SNIP>

real	0m5.648s
user	0m2.204s
sys	0m0.462s
```

### Getting data from your local cache after saving with -k (above)

```
appuser@11f6e8db4d97:/$ time python3.7 ./market_sales.py -m local  -s AAPL
AAPL had 183,240.0 M Revenue in 2014 4 GR Rate =  9.75%
AAPL had 231,280.0 M Revenue in 2015 3 GR Rate =  4.75%
AAPL had 214,230.0 M Revenue in 2016 2 GR Rate =  11.39%
AAPL had 228,570.0 M Revenue in 2017 1 GR Rate =  16.29%
AAPL had 265,810.0 M Revenue in 2018 0 GR Rate =  0.00%
<SNIP>

real	0m1.059s
user	0m1.000s
sys	0m0.048s
```
