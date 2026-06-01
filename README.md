# Bitcoin Asymmetric Quantile Bands for TradingView

This repository contains a Pine Script v5 TradingView indicator that visualizes Bitcoin asymmetric quantile bands based on Benjamin Cowen's 2026 working paper, "Asymmetric Tail Curvature in Bitcoin Price Quantiles."

The indicator is intended as an analytical charting tool. It is not financial advice, not a trading system, and not a live re-estimation of the paper's model.

## What It Is

The script plots fixed Bitcoin price quantile bands on a TradingView chart:

- Q1%, Q10%, Q25%: lower-tail bands
- Q50%: median band
- Q75%, Q95%, Q99%: upper-tail bands

These bands are meant to help visualize where Bitcoin's current price sits relative to the historical quantile model described in the paper.

## How It Works

The indicator uses the paper's published full-sample coefficients and applies this model:

```text
log10(price) = c + a*x + b*x^2
x = ln(days since Bitcoin genesis) - 7.9914
```

The lower, median, and upper bands use different coefficient sets. The main idea is that Bitcoin's lower-tail behavior and upper-tail speculative behavior may curve differently over time. In the paper, the lower tail is close to a traditional power-law path, while the upper tail bends downward more strongly as Bitcoin matures.

## How To Use In TradingView

1. Open TradingView.
2. Open a Bitcoin chart, such as `BTCUSD`, `BTCUSDT`, or another BTC pair.
3. Open the Pine Editor.
4. Copy the contents of `btc_asymmetric_quantile_indicator.pine`.
5. Paste the code into Pine Editor.
6. Click "Add to chart."
7. Use log scale for the clearest long-term view.

The script includes inputs to show or hide lower bands, the median, upper bands, fills, and the status table.

## Files

- `btc_asymmetric_quantile_indicator.pine`: TradingView Pine Script indicator.
- `docs.md`: Additional notes about the model, usage, and limitations.

## References

- [Research Paper](https://www.benjamincowen.com/reports/asymmetric-tail-curvature-in-bitcoin-price-quantiles)
- [YouTube Explanation](https://www.youtube.com/watch?v=uFn3KUE-VTI&t=1211s)
- [Into The Cryptoverse](https://www.youtube.com/@intothecryptoverse)
- [Benjamin Cowen Website](https://www.benjamincowen.com/)

## Disclaimer

This project is a visualization of a published research model. It should be used for education, research, and chart analysis only. It does not predict future prices and should not be used as a standalone basis for trading or investment decisions.
