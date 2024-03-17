
# Data Gathering Using API

This repository provides guidelines and code samples for gathering data from an API and integrating it into your Git repository.

## Overview

Data gathering from APIs is a common practice in various data-driven projects. APIs (Application Programming Interfaces) provide a structured way to access and retrieve data from external sources, enabling developers to automate the process of data collection.

In this repository, we'll cover the following aspects:

- Understanding APIs and their usage
- Steps to gather data from an API
- Integration of API data into your Git repository
- Best practices and considerations

## Getting Started

To get started with data gathering using an API for your Git repository, follow these steps:

Usage:
- Open the script named gather_data.py in your preferred code editor.
- Replace [API_KEY] with your actual API key or credentials required for accessing the API.
- Modify the parameters of the API request as needed, such as specifying the search query or defining additional filters.
- Run the script gather_data.py by executing python gather_data.py in your terminal or command prompt.
- The script will make requests to the API, retrieve movie data, and store it in a suitable format (e.g., JSON, CSV, etc.). You can customize the script to store the data in the format that best suits your requirements.
- Data Format:
The gathered movie data will typically include various attributes such as title, release year, genre, cast, director, ratings, and more, depending on the capabilities of the API being used.

## Example Code

Below is an example code snippet in Python demonstrating how to gather data from an API using the requests library:

```python
import requests

# API endpoint URL
url = 'https://api.themoviedb.org/3/movie/top_rated?api_key=8265bd1679663a7ea12ac168da84d2e8&language=en-US&page=1'

# API authentication (if required)
headers = {'Authorization': '8265bd1679663a7ea12ac168da84d2e8'}

# Make a GET request to the API
response = requests.get(url, params=params, headers=headers)

# Running this code to get data from all 428 pages and Check if the request was successful
for i in range(1,429):
    response = requests.get('https://api.themoviedb.org/3/movie/top_rated?api_key=8265bd1679663a7ea12ac168da84d2e8&language=en-US&page={}'.format(i))
    temp_df = pd.DataFrame(response.json()['results'])[['id','title','overview','release_date','popularity','vote_average','vote_count']]
    df = df.append(temp_df,ignore_index=True)
