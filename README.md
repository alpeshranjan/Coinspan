# Coinspan

Coinspan is a long-horizon look at historical cryptocurrency prices. A notebook and a Power BI dashboard compare market cap, closing prices, and moving averages, so a reader can see how a long hold in the largest coins differed from a wider set of smaller ones.

The prices run from each coin's start through 30 November 2021. This is historical analysis. It does not forecast a future price, and it is not investment advice.

## Live dashboard

The site is [https://black-dune-0c5f90200.1.azurestaticapps.net](https://black-dune-0c5f90200.1.azurestaticapps.net). The page embeds the Power BI report.

A short walkthrough of the site is here:

https://user-images.githubusercontent.com/58964309/178829978-e64d23e1-0e3d-4c3c-97bf-afc9c3f1d4ab.mov

## What is in the repo

| Path | Contents |
| --- | --- |
| `EDA for historic dataset/EDA_inv.ipynb` | Exploratory analysis of the daily prices |
| `EDA for historic dataset/final.csv` | Daily prices the notebook reads |
| `Dashboards/Dashboard.pbix` | Power BI report |
| `index.html` | Bootstrap page that embeds the dashboard |

## What the notebook charts

- Market cap of the five largest coins at the end of the series
- Closing prices of the largest coins, then the same chart with BTC removed, with BTC and ETH removed, and with BTC, ETH, and USDT removed, so smaller coins stay visible
- Candlesticks for BTC, ETH, USDT, BNB, and ADA
- The close against a 50-day and a 200-day moving average for those five coins
- Interactive area charts of the daily high and of market cap, with 1-month, 6-month, 1-year, and full-history ranges

## Dataset

The source archive holds daily prices for about 75 coins through 30 November 2021, plus `Current Crypto Leaderboard.csv` from that date. The leaderboard has market capitalization, rank, coin name, symbol, price, and a flag for whether that coin's history is in the price files.

Each price row has:

| Column | Meaning |
| --- | --- |
| Name | Coin name |
| Symbol | Ticker |
| High | Highest price that day |
| Low | Lowest price that day |
| Open | Opening price |
| Close | Closing price |
| Volume | Amount traded |
| Marketcap | Market capitalization on that date |

The leaderboard was meant to be refreshed monthly as the top 100 changed. The copy used here stops on 30 November 2021.

## What the notebook concludes

Using prices through November 2021, the closing notes say:

- Bitcoin led by market cap. Ethereum was about half of Bitcoin, and the other coins were much smaller. USDT was about a third of Ethereum.
- Bitcoin's 2021 high was about $60,000, far above Ethereum.
- A multi-year hold in BTC, ETH, and USDT was the part of this set that rewarded investors. The notes treat the smaller, more volatile names as poor long-term holds, and point at the USDT candlestick as an example of a long volatile stretch.

Those are observations on this dataset. They are not a model, and they do not describe prices after 30 November 2021.

## Stack

- Python, with pandas, NumPy, Matplotlib, Seaborn, and Plotly
- Power BI for the dashboard
- Bootstrap 5 for the page
- Azure Static Web Apps for the site
- An Azure virtual machine, used to work in Power BI

## Run it locally

Open `EDA for historic dataset/EDA_inv.ipynb`. The upload cell was written for Google Colab. Locally, `final.csv` is already in that folder, so skip the Colab upload and read the file from there.

```bash
pip install pandas numpy matplotlib seaborn plotly pandas-datareader
```

Open `Dashboards/Dashboard.pbix` in Power BI Desktop to edit the report. The public page already shows the published report.

## Deploy

A push to `main` publishes the static site through `.github/workflows/azure-static-web-apps-black-dune-0c5f90200.yml`.
