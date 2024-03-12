
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

1. **Select an API**: Choose the API that provides the data you need for your project. Ensure that the API documentation is available and that you understand how to authenticate and make requests to the API endpoints.

2. **API Authentication**: If the API requires authentication (e.g., API keys, OAuth tokens), make sure to obtain the necessary credentials according to the API documentation.

3. **Data Gathering Script**: Write a script to interact with the API, make requests, and retrieve the desired data. You can use any programming language suitable for your project (e.g., Python, JavaScript, Ruby).

4. **Testing**: Test your data gathering script to ensure that it retrieves data correctly from the API and handles errors gracefully.

5. **Integration with Git**: Integrate your data gathering script into your Git repository. You can create a dedicated directory for scripts or place them in an appropriate location within your project structure.

6. **Documentation**: Document your data gathering process, including instructions for running the script, API usage details, and any dependencies required.

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
