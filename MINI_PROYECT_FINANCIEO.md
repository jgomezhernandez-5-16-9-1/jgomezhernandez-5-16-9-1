- 👋 Hi, I’m @jgomezhernandez-5-16-9-1
- 👀 I’m interested in Finance & Marketing
- 🌱 I’m currently learning DATA S100TIST 
- 💞️ I’m looking to collaborate on financial and medicine sector
- 📫 How to reach me ... www.linkedin.com/in/jesúsgómezhhernández 
- 😄 Pronouns: He/Him
- ⚡ Fun fact: I love analyzing data trends while listening to classical music 🎵

"""MINI PROYECT FINANCIERO"""
import pandas as pd
import numpy as np
import datetime
import matplotlib.pyplot as plt
import yfinance as yf

from datetime import date, datetime, time, timezone

def get_stock_data(ticker,start,end):
    data = yf.download(tickers=[ticker], start=start, end=end)
    data.insert(0, "Ticker" , ticker)
    return data

    ticker = 'DIS'
start = datetime (2020, 1,1)
end = datetime.today()

d = get_stock_data(ticker,start,end)
d.head()

d=d.reset_index().pivot(index="Date", columns="Ticker", values="Close")
d.head()

SPY = get_stock_data("SPY",start,end)
IYW = get_stock_data("IYW",start,end)
VT = get_stock_data("VT",start,end)
DBA = get_stock_data("DBA",start,end)
TLT = get_stock_data("TLT",start,end)
PDBC = get_stock_data("PDBC",start,end)
IAU = get_stock_data("IAU",start,end)

SPY.info()

# Execute pivoting per data frame
SPY=SPY.reset_index().pivot(index="Date", columns="Ticker", values="Close")
IYW=IYW.reset_index().pivot(index="Date", columns="Ticker", values="Close")
VT=VT.reset_index().pivot(index="Date", columns="Ticker", values="Close")
DBA=DBA.reset_index().pivot(index="Date", columns="Ticker", values="Close")
TLT=TLT.reset_index().pivot(index="Date", columns="Ticker", values="Close")
PDBC=PDBC.reset_index().pivot(index="Date", columns="Ticker", values="Close")
IAU=IAU.reset_index().pivot(index="Date", columns="Ticker", values="Close")

stock=pd.concat([SPY, IYW, VT, DBA, TLT, PDBC, IAU],
                axis=1,
                join='outer')
stock.head()

plt.style.use('ggplot')
stock.plot(figsize = (20, 10))
plt.show()

covid=stock['2020-2-1':'2020-7-31']

plt.style.use('ggplot')
covid.plot(figsize = (20, 10))
plt.show()

x = covid.index
s_y = covid[['SPY']]
i_y = covid[['IAU']]
d_y = covid[['DBA']]
t_y = covid[['TLT']]

import matplotlib.pyplot as plt

fig, axs = plt.subplots(1, 3, figsize=(15, 5))
axs[0].plot(x, s_y)
axs[1].plot(x, i_y)
axs[2].plot(x, t_y)


fig.suptitle('Covid 19')

import pandas as pd
import numpy as np
import datetime
import matplotlib.pyplot as plt
import yfinance as yf

from datetime import date, datetime, time, timezone

def get_stock_data(ticker,start,end):
    data = yf.download(tickers=[ticker], start=start, end=end)
    data.insert(0, "Ticker" , ticker)
    return data

ticker = 'PDBC'
start = datetime(2020,1,1)
end = datetime.today()

df = get_stock_data(ticker, start, end)
df.head()

df.drop(['Ticker', 'High', 'Low', 'Open', "Close", "Adj Close"], axis=1, inplace=True)

df.head()

x = df.index
y = df['Volume']
plt.figure(figsize = (15,3))
plt.bar(x, y)
plt.show()

ticker = 'PDBC'
start = datetime(2020,1,1)
end = datetime.today()

df = get_stock_data(ticker, start, end)

fig = plt.figure(figsize=(12, 8))
top_grid = plt.subplot2grid((4,4), (0,0), rowspan=3, colspan=4)
bottom_grid = plt.subplot2grid((4,4), (3,0), rowspan=1, colspan=4)

top_grid.plot(df.index, df['Close'], label='Close')
bottom_grid.plot(df.index, df['Volume'], label='Volume')

plt.tight_layout()

plt.legend()
plt.show()

stock.head()

stock['SPY']

stock['SPY'].shift(1)

spy_dayily_pc=(stock['SPY']/stock['SPY'].shift(1)-1)*100

spy_dayily_pc

spy_dayily_pc.plot()

spy_dayily_pc=(stock['SPY']/stock['SPY'].shift(1)-1)*100

spy_dayily_pc.iloc[0] =0

plt.hist(spy_dayily_pc, bins = 50)
plt.show()

stock_dayily_pc=(stock-stock.shift(1))/stock.shift(1) * 100

stock_dayily_pc.head()

stock_d_cr=stock_dayily_pc.cumsum()

stock_d_cr

stock_d_cr.plot(figsize = (20, 10))

df_corr = stock_dayily_pc.corr()

df_corr

plt.imshow (df_corr, cmap ='hot', interpolation ='none')
plt.colorbar()
plt.xticks(range(len(df_corr)),df_corr.columns)
plt.yticks(range(len(df_corr)),df_corr.columns)

plt.gcf().set_size_inches(10,10)

plt.scatter(df_corr.SPY,df_corr.VT)
plt.show()

periods = 75

vol = stock_dayily_pc.rolling(window=periods).std()

vol

vol["SPY"].plot()
vol["TLT"].plot()
vol["DBA"].plot()

<!---
jgomezhernandez-5-16-9-1/jgomezhernandez-5-16-9-1 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
