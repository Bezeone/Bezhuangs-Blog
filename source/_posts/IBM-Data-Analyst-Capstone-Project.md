---
title: IBM Data Analyst Capstone Project
date: 2021-03-27
updated: 2021-03-27
group: going
tags: [Python]
categories: 人工智能与大数据
---

> In this course provided by IBM, I will assume the role of an Associate Data Analyst who has recently joined the organization and be presented with a business challenge that requires data analysis to be performed on real-world datasets. The capstone project will culminate with a presentation of your data analysis report, with an executive summary for the various stakeholders in the organization. I believe this project is a great opportunity to showcase Data Analytics skills, and demonstrate proficiency to potential employers. The following are the notes I took during this course.

<!--more-->

### Data Collection

#### Collecting Data Using APIs

- The `HTTP` protocol allows you to send and receive information through the web including webpages, images, and other web resources.

- Uniform resource locator(URL): the most popular way to find resources on the web

  - Scheme: `http://`
  - Internet address or Base URL: `www.ibm.com` 
  - Route location on the web server: `/images/IDSNlogo.png`

- Request

  - Request start line = `GET` method + location of the resource `/index.html` + `HTTP` version
  - Request header passes additional information with an `HTTP` request

- Response

  - Response start line = version number `HTTP/1.0` + a status code (200) meaning success, + a descriptive phrase (OK). 
  - Response header contains useful information
  - Response body containing the requested file an `HTML` document

- Requests in Python

  ```python
  import requests
  import os 
  from PIL import Image
  from IPython.display import IFrame
  url='https://www.ibm.com/'  #GET request //# Use single quotation marks for defining string
  r=requests.get(url)
  r.status_code  #status of the request
  print(r.request.headers)  #view request headers //r.request.body
  header=r.headers  #HTTP response header
  header['date']  #obtain the date
  header['Content-Type']  #obtain the type of data
  r.encoding
  r.text[0:100]  #view text
  path=os.path.join(os.getcwd(),'image.png')
  with open(path,'wb') as f:
      f.write(r.content)
  Image.open(path)
  ```

- Get Request with URL Parameters

  - You can use the `GET` method to modify the results of your query

  ```python
  url_get='http://httpbin.org/get'
  payload={"name":"Joseph","ID":"123"}  #To create a Query string, add a dictionary.
  r=requests.get(url_get,params=payload)
  r.url  #'http://httpbin.org/get?name=Joseph&ID=123'
  r.json()['args']  #key args in JSON format
  ```

- Post Requests

  - the `POST` request sends the data in a request body

  ```python
  url_post='http://httpbin.org/post'
  r_post=requests.post(url_post,data=payload)
  r_post.url 
  r_post.request.body
  r_post.json()['form']
  ```

#### Collecting Data Using Webscraping

- Review of Webscraping

  ```python
  from bs4 import BeautifulSoup  # this module helps in web scrapping.
  import requests  # this module helps us to download a web page
  url = "http://www.ibm.com"
  data  = requests.get(url).text  # get the contents of the webpage in text format and store in a variable called data
  soup = BeautifulSoup(data,"html5lib")  # create a soup object using the variable 'data'
  for link in soup.find_all('a'):  # in html anchor/link is represented by the tag <a>
      print(link.get('href'))
  for link in soup.find_all('img'):# in html image is represented by the tag <img>
      print(link.get('src'))
  ```

- Scrape data from html table

  ```python
  url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/datasets/HTMLColorCodes.html"
  data  = requests.get(url).text  # get the contents of the webpage in text format and store in a variable called data
  soup = BeautifulSoup(data,"html5lib")
  table = soup.find('table') # in html table is represented by the tag <table>
  for row in table.find_all('tr'): # in html table row is represented by the tag <tr>
      cols = row.find_all('td') # in html a column is represented by the tag <td>
      color_name = cols[2].getText() # store the value in column 3 as color_name
      color_code = cols[3].getText() # store the value in column 4 as color_code
      print("{}--->{}".format(color_name,color_code))
  ```

#### Exploring Data

- Load the dataset

  ```python
  import pandas as pd
  dataset_url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/LargeData/m1_survey_data.csv"
  df = pd.read_csv(dataset_url)
  ```

- Explore the dataset

  ```python
  df.head()  #Display the top 5 rows and columns from your dataset
  df.tail()
  df.shape[0]  #The number of rows in the dataset.
  df.shape[1]  #The number of columns in the dataset.
  df.dtypes  #Print the datatype of all columns.
  df["Age"].mean()  #Print the mean age of the survey participants.
  df["Country"].nunique()  #Print how many unique countries are there in the Country column.
  ```

### Module 2: Data Wrangling

- Finding Duplicates

  ```python
  import pandas as pd
  df = pd.read_csv("https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/LargeData/m1_survey_data.csv")
  df.duplicated(keep='first').sum()  #Find how many duplicate rows exist in the dataframe.
  duplicateRows = df[df.duplicated()]  #Show duplicated rows
  duplicateRows  
  df["Respondent"].duplicated(keep='first').sum()  #numbers of duplicate values in the column Respondent
  ```

- Removing Duplicates

  ```python
  df.drop_duplicates(ignore_index=True, inplace=True)  #Remove the duplicate rows from the dataframe.
  df.duplicated(keep='first').sum()  #Verify if duplicates were actually dropped.
  df.shape  #number of rows and columns left
  df["Respondent"].nunique  #numbers of unique rows left in the column Respondent
  ```

- Finding Missing Values

  ```python
  df.isnull().sum()  #Find the missing values for all columns.
  df["EdLevel"].isnull().sum()  #Find out how many rows are missing in the column EdLevel
  ```

- Determine Missing Values

  ```python
  df["WorkLoc"].value_counts()  #Find the value counts for the column WorkLoc.
  df["WorkLoc"].fillna(value="Office",inplace=True)  #Impute (replace) all the empty rows in the column WorkLoc with the value that you have identified as majority.
  df["WorkLoc"].isnull().sum()  #After imputation there should ideally not be any empty rows in the WorkLoc column.
  ```

- Normalizing Data

  ```python
  df["CompFreq"].unique()  #List out the various categories in the column 'CompFreq'
  df["CompFreq"].replace(to_replace="Yearly",value=1,inplace=True)  #If the CompFreq is Yearly then use the exising value in CompTotal
  df["CompFreq"].replace(to_replace="Monthly",value=12,inplace=True)  #If the CompFreq is Monthly then multiply the value in CompTotal with 12 (months in an year)
  df["CompFreq"].replace(to_replace="Weekly",value=52,inplace=True)  #If the CompFreq is Weekly then multiply the value in CompTotal with 52 (weeks in an year)
  df["CompFreq"].unique()
  df["CompFreq"].value_counts()
  df['NormalizedAnnualCompensation'] = df["CompTotal"] * df["CompFreq"]  #it makes comparison of salaries easy.
  df["Respondent"].nunique()
  df["ConvertedComp"].describe()
  df["ConvertedComp"].hist(figsize=(15,4))
  df['NormalizedAnnualCompensation'].median()
  ```

### Module 3: Exploratory Data Analysis

- Distribution
- Outliers
- Correlation

### Module 4: Data Visualization

- Visualizing Distribution of Data
- Relationship
- Composition
- Comparison

### Module 5: Dashboard Creation

- Dashboards

### Module 6: Presentation of Findings

- Final Presentation