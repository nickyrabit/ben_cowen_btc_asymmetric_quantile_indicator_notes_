# Documentation

## Purpose

This project turns Benjamin Cowen's asymmetric Bitcoin quantile model into a TradingView indicator. The goal is to make the model easier to inspect visually on a BTC chart.

The indicator plots several quantile bands that represent different parts of Bitcoin's modeled historical price distribution. This can help users compare current price action with the lower, middle, and upper regions of the model.

## Model Summary

The model is based on a quadratic quantile equation in log-time space:

```text
log10(price) = c + a*x + b*x^2
x = ln(days since Bitcoin genesis) - 7.9914
```

Each plotted band uses one set of published coefficients from the paper:

| Band | c | a | b |
| --- | ---: | ---: | ---: |
| Q1% | 2.837 | 2.578 | -0.0241 |
| Q10% | 2.933 | 2.552 | -0.0241 |
| Q25% | 3.004 | 2.554 | -0.0241 |
| Q50% | 3.214 | 2.482 | -0.1126 |
| Q75% | 3.562 | 2.283 | -0.3259 |
| Q95% | 3.897 | 1.964 | -0.3259 |
| Q99% | 4.028 | 1.904 | -0.3259 |

The lower-tail bands share the lower-tail curvature value. The upper-tail bands share the upper-tail curvature value. This reflects the paper's main finding that Bitcoin's upper-tail speculative peaks appear to compress more strongly over time than the lower-tail support region.

## TradingView Usage

1. Open TradingView in a browser.
2. Open a BTC chart, for example `BTCUSD` or `BTCUSDT`.
3. Open the Pine Editor panel.
4. Paste the code from `btc_asymmetric_quantile_indicator.pine`.
5. Save the script.
6. Click "Add to chart."
7. Switch the chart to log scale.

Recommended chart settings:

- Use a daily, weekly, or monthly timeframe for long-term context.
- Use log scale because the model is based on logarithmic price behavior.
- Use the status table to see the current regime and distance from the modeled median.

## Indicator Controls

The script includes these user inputs:

- `Show lower bands`: toggles Q1%, Q10%, and Q25%.
- `Show median`: toggles Q50%.
- `Show upper bands`: toggles Q75%, Q95%, and Q99%.
- `Fill bands`: toggles shaded areas between plotted bands.
- `Show status table`: toggles the table in the top-right corner.

## Limitations

This script uses fixed coefficients from the paper. It does not update, refit, or retrain the model from TradingView data.

The model describes historical distributional structure. It is not a prediction engine and does not guarantee that future Bitcoin prices will respect any band.

The paper itself notes important limitations, including the short number of complete Bitcoin market cycles and the fact that the model is price-only.

## References

- [Research Paper](https://www.benjamincowen.com/reports/asymmetric-tail-curvature-in-bitcoin-price-quantiles)
- [YouTube Explanation](https://www.youtube.com/watch?v=uFn3KUE-VTI&t=1211s)
- [Into The Cryptoverse](https://www.youtube.com/@intothecryptoverse)
- [Benjamin Cowen Website](https://www.benjamincowen.com/)
