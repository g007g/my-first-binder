# to pick the stocks
import pandas as pd
import matplotlib.pyplot as plt

def calculate_macd(prices, short_period=12, long_period=26, signal_period=9):
    # Calculate the short-term exponential moving average (EMA)
    short_ema = prices.ewm(span=short_period, adjust=False).mean()
    
    # Calculate the long-term exponential moving average (EMA)
    long_ema = prices.ewm(span=long_period, adjust=False).mean()
    
    # Calculate the MACD line
    macd_line = short_ema - long_ema
    
    # Calculate the signal line (EMA of the MACD line)
    signal_line = macd_line.ewm(span=signal_period, adjust=False).mean()
    
    # Calculate the MACD histogram
    macd_histogram = macd_line - signal_line
    
    return macd_line, signal_line, macd_histogram

# Example usage:
# Assuming you have a DataFrame 'df' with a 'Date' column and 'Close' column representing the stock prices

# Read stock prices from a CSV file or database
df = pd.read_csv('stock_prices.csv')

# Convert the 'Date' column to a pandas datetime object
df['Date'] = pd.to_datetime(df['Date'])

# Set the 'Date' column as the index
df.set_index('Date', inplace=True)

# Calculate the MACD
macd_line, signal_line, macd_histogram = calculate_macd(df['Close'])

# Plotting the MACD line, signal line, and histogram
plt.figure(figsize=(10, 6))
plt.plot(macd_line, label='MACD Line')
plt.plot(signal_line, label='Signal Line')
plt.bar(macd_histogram.index, macd_histogram, label='MACD Histogram')
plt.legend()
plt.title('MACD Indicator')
plt.xlabel('Date')
plt.ylabel('MACD Value')
plt.show()
