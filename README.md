# Google Stock Price Forecasting with an LSTM

An educational time-series forecasting experiment that uses a stacked Long Short-Term Memory (LSTM) network to model the opening price of Google stock from historical daily market data.

This notebook is a learning-oriented reproduction and adaptation of the tutorial linked in the [Acknowledgements](#acknowledgements) section. It is not a trading system and should not be used for financial decisions.

## Experiment overview

- **Dataset:** daily Google stock data in `GOOG.csv`
- **Inputs:** Open, High, Low, Close, and Volume
- **Target:** next opening price represented by the first feature
- **Training period:** observations before January 1, 2019
- **Test period:** observations from January 1, 2019 onward
- **Sequence length:** 60 trading days
- **Model:** four stacked LSTM layers with dropout followed by a dense output layer
- **Training configuration:** Adam optimizer, mean squared error, 50 epochs, batch size 32

The final notebook visualization compares the predicted and observed series over the test period.

## Repository structure

```text
.
|-- GOOG.csv                  # Historical OHLCV data
|-- STOCK PREDICTION.ipynb    # Preprocessing, training, inference, and visualization
|-- requirements.txt
`-- README.md
```

## Setup

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt
jupyter notebook "STOCK PREDICTION.ipynb"
```

The notebook trains the model from scratch, so execution time depends on the available CPU or GPU.

## Limitations

- The data ends in October 2019 and is retained to reproduce the original experiment.
- The notebook visualizes predictions but does not implement walk-forward validation, backtesting, transaction costs, or a comparison with naive baselines.
- Market prices are non-stationary and influenced by information that is not present in historical OHLCV data.
- A production-quality study should report MAE/RMSE, use multiple temporal folds, compare against simple baselines, and test stability across assets and market regimes.

## Acknowledgements

This repository adapts the workflow presented in the [Google Stock Price Prediction using RNN-LSTM tutorial](https://youtu.be/arydWPLDnEc). The conceptual explanation of LSTMs also references Christopher Olah's article, [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/). Historical data was obtained from Yahoo Finance.

## Disclaimer

This project is for educational purposes only and does not constitute financial advice.
