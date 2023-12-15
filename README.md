# Stock Analysis Project

## Overview

This repository contains a simple stock analysis project that utilizes Python and various libraries to analyze and visualize stock data for selected tech companies: Apple (AAPL), Google (GOOG), Microsoft (MSFT), and Amazon (AMZN).

## Prerequisites

Before running the analysis, make sure you have the required dependencies installed. You can install them using the following command:

```bash
pip install pandas matplotlib seaborn yfinance keras
```

## Usage

1. Clone the repository:

    ```bash
    git clone https://github.com/your-username/stock-analysis-project.git
    ```

2. Navigate to the project directory:

    ```bash
    cd stock-analysis-project
    ```

3. Run the analysis script:

    ```bash
    python stock_analysis.py
    ```

## Tech Stocks

The project focuses on the following tech stocks:

- Apple (AAPL)
- Google (GOOG)
- Microsoft (MSFT)
- Amazon (AMZN)

## Data Sources

The project utilizes the `yfinance` library to download historical stock data from Yahoo Finance for the selected tech companies.

- [Yahoo Finance](https://finance.yahoo.com/)

## Data Analysis and Visualization

### Volume and Moving Averages for Apple Stock

```python
# ... [previous code]

# Save the visualizations
plt.savefig('linear-relation_google.jpg')
plt.savefig('DailyRet_google_microsoft.jpg')
plt.savefig('pairplot_DailyRet.jpg')
plt.savefig('pairGride_DailyRet.jpg')
plt.savefig('Heatmap_DailyRet.jpg')
plt.savefig('Pairgrid_closePrice.jpg')
```

### Correlation Analysis and Risk vs. Returns

```python
# Calculate and plot the correlation matrix for closing prices of tech stocks
corr_matrix_closing = closing_df.dropna().corr()
sns.heatmap(corr_matrix_closing, annot=True)
plt.title('Correlation Matrix for Closing Prices')
plt.savefig('Heatmap_closePrice.jpg')

# Scatter plot for risk vs. returns
rets = tech_rets.dropna()
plt.scatter(rets.mean(), rets.std())
plt.xlabel('Expected Returns')
plt.ylabel('Risk')

# Annotate the scatter plot
for label, x, y in zip(rets.columns, rets.mean(), rets.std()):
    plt.annotate(
        label,
        xy=(x, y), xytext=(50, 50),
        textcoords='offset points', ha='right', va='bottom',
        arrowprops=dict(arrowstyle='-', connectionstyle='arc3,rad=-0.3', color='black'))

# Save the risk vs. return plot
plt.gcf().set_size_inches(10, 8)
plt.savefig('Risk-vs-Returns.jpg')
```

### LSTM-Based Stock Price Prediction for Google

```python
# ... [previous code]

# Training the LSTM model
regressor = Sequential()
# ... [previous code]
history = regressor.fit(X_train, y_train, epochs=100, batch_size=32, validation_split=0.1, callbacks=[checkpoint,early_stopping])

plt.plot(history.history['loss'], label='Training Loss')
plt.plot(history.history['val_loss'], label='Validation Loss')
plt.xlabel('Epochs')
plt.ylabel('Mean Squared Error')
plt.legend()
plt.show()

# ... [previous code]

# Making predictions on the test set
dataset_test = yf.download("GOOG", start, en)
print('GOT GOOGLES DATA')
real_stock_price = dataset_test.iloc[:, 1:2].values

# ... [previous code]

# Visualizing the results
plt.plot(real_stock_price, color='red', label='Real Google Stock Price')
plt.plot(predicted_stock_price, color='blue', label='Predicted Google Stock Price')
plt.title('Google Stock Price Prediction')
plt.xlabel('Time')
plt.ylabel('Google Stock Price')
plt.legend()

dpi_value = 300
plt.gcf().set_size_inches(10, 8)
plt.savefig('Pridicted-vs-real_google.jpg')
```

Feel free to further customize the README based on any additional insights, instructions, or features you'd like to highlight in your project.
```
