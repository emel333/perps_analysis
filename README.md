# perps_analysis
Competitive analysis for perpetual futures exchanges

### Target exchanges so far: MCDEX, perpetual protocol

According to Glassnode, perpetual futures "have become the preferred source of leverage," and are dominating total futures volume. Here, I'm analyzing perpetual future protocols to gain a sense for what's happening.

# Process & Tools Used

<ul>
    <li>Queried Perpetual V2 Optimism Subgraph via The Graph, using GraphiQL</li>
    <li>Gathered a sample of 1000 trader position changes, as JSON files, querying with respect to two time ranges: 1) at the beginning of the trading history (NOV/DEC 2021) as well as the most recent trade history (JUN 2022)</li>
    <li>Uploaded the files to Jupyter notebook</li>
    <li>Performed EDA using Pandas and Plotly</li>
    <li>Did light work to anonymize trader info by taking the last two of trader addresses to create a new column</li>
</ul>

# Findings:

## One trader had multiple occasions of 10+ transaction hashes in a single second

Multiple traders were shown to have traded numerous times in a single second, suggesting a significant presence of high-frequency trading (HFT). Trader Tc7 had 16, 14, 13, and 11 txHashes in a single second, respectively.

![alt text](https://github.com/emel333/perps_analysis/blob/main/visuals/trades_per_second.png "Trades Per Second: Perpetual Protocol v2 (sample size:1000 trades)")

https://github.com/emel333/perps_analysis/blob/main/visuals/trades_per_second.png

## The majority of traders either take losses or break even

Despite presense of HFT, most traders didn't fare well, with a mean realizedPnl of -0.709529. The visuals below help to paint the picture as well.

![alt text](https://github.com/emel333/perps_analysis/blob/main/visuals/perpv2PNL.png "Perpetual Protocol v2 (sample size - 1000 trades): Trader Profit & Loss")

![alt text](https://github.com/emel333/perps_analysis/blob/main/visuals/perpv2_trade_viz.png "Perpetual Protocol v2 (sample size -- 1000 trades): Trade Activity Visual")