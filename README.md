Here's the README file:

```markdown
# Cryptocurrency Market Data Automation Pipeline

This project pulls live cryptocurrency data from the CoinMarketCap API, automates data collection over time, processes the data for analysis, and generates visualizations to spot market trends.

## What This Project Does

The script connects to the CoinMarketCap API and fetches the top 15 cryptocurrencies by market cap. It can run automatically at set intervals to collect data over time, saving each fetch to a CSV file. After collecting the data, it calculates percentage changes across different time periods and creates charts showing how these cryptocurrencies are performing.

## Technologies Used

- Python 3.x
- Pandas for data manipulation
- Requests for API calls
- Seaborn and Matplotlib for visualizations
- CSV for data storage

## Installation

Clone the repository or download the script directly.

Install the required packages:

```bash
pip install requests pandas seaborn matplotlib
```

## Getting an API Key

You need a free API key from CoinMarketCap to run this script.

1. Go to coinmarketcap.com/api and sign up for a free account
2. Once logged in, go to your dashboard
3. Copy your API key
4. Replace the API key in the script with your own

The API key in the script is a placeholder. You need to use your own key.

## Running the Script

Save the script as a .py file and run it:

```bash
python crypto_tracker.py
```

The script will:

1. Fetch data from the API
2. Display the cryptocurrency data with prices and percentage changes
3. Save the data to a CSV file
4. Calculate average percentage changes for each coin
5. Show a chart comparing percentage changes across different time periods

## Continuous Data Collection

The script includes a loop that can run multiple times with set intervals. To enable continuous collection, uncomment this section in the code:

```python
for i in range(333):
    api_runner()
    print('API Runner completed')
    sleep(60)
```

The free API tier limits you to 333 requests per day. Running the full loop uses your entire daily limit.

## Understanding the Output

### CSV File

The script creates a CSV file with these columns:

- name - Cryptocurrency name (Bitcoin, Ethereum, etc.)
- symbol - Trading symbol (BTC, ETH, etc.)
- quote.USD.price - Current price in US dollars
- quote.USD.percent_change_1h - Percentage change over 1 hour
- quote.USD.percent_change_24h - Percentage change over 24 hours
- quote.USD.percent_change_7d - Percentage change over 7 days
- quote.USD.percent_change_30d - Percentage change over 30 days
- quote.USD.percent_change_60d - Percentage change over 60 days
- quote.USD.percent_change_90d - Percentage change over 90 days
- timestamp - When the data was collected

### Console Output

After running, the script prints the cryptocurrency data directly to the console.

### Chart

The script generates a point plot showing how each cryptocurrency performs across different time periods (24h, 7d, 30d, 60d, 90d).

## Fixing Common Issues

AttributeError: 'DataFrame' object has no attribute 'append'

This happens with newer versions of pandas. The solution is to replace .append() with pd.concat():

```python
df = pd.concat([df, df2], ignore_index=True)
```

Connection errors

If the script fails to connect, check your internet connection and verify your API key is correct. The free tier has rate limits, so if you run the script too many times in one day you might get blocked until the next day.

No chart showing

Add plt.show() after the plotting code:

```python
sns.catplot(x='percent_change', y='values', hue='name', data=df7, kind='point')
plt.show()
```

KeyError: 'percent_change'

This happens when the column rename fails. Make sure to use reset_index() before renaming:

```python
df5 = df5.reset_index()
df5 = df5.rename(columns={'level_1': 'percent_change'})
```

## Modifying the Script

Change how many cryptocurrencies to fetch

Find the parameters dictionary and change the limit value:

```python
parameters = {
  'start':'1',
  'limit':'50',
  'convert':'USD'
}
```

Change the collection interval

Modify the sleep value in the loop:

```python
sleep(30)
```

Change the output file location

Modify the file path in the CSV code:

```python
df.to_csv(r'C:\YourFolder\API.csv')
```

## Project Structure

```
project_folder/
│
├── crypto_tracker.py    # Main script
├── API.csv              # Generated output file
└── requirements.txt     # Package dependencies
```

## Notes for Your CV

This project demonstrates:

- Working with REST APIs and handling JSON responses
- Automating data collection tasks with Python
- Data cleaning and transformation using Pandas
- Time series analysis on financial data
- Creating charts for data presentation
- Handling errors like connection timeouts and rate limits

The project automates a task that would be tedious to do manually: checking crypto prices and percentage changes across multiple timeframes.

## License

Feel free to use and modify this code for your own projects.
```
