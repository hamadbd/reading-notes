# Web Scraping with Python

Imagine you have to pull a large amount of data from websites and you want to do it as quickly as possible. How would you do it without manually going to each website and getting the data? Well, “Web Scraping” is the answer. Web Scraping just makes this job easier and faster. 

## Why is Web Scraping Used?
Web scraping is used to collect large information from websites. But why does someone have to collect such large data from websites? To know about this, let’s look at the applications of web scraping:

- Price Comparison: Services such as ParseHub use web scraping to collect data from online shopping websites and use it to compare the prices of products.
- Email address gathering: Many companies that use email as a medium for marketing, use web scraping to collect email ID and then send bulk emails.
- Social Media Scraping: Web scraping is used to collect data from Social Media websites such as Twitter to find out what’s trending.
- Research and Development: Web scraping is used to collect a large set of data (Statistics, General Information, Temperature, etc.) from websites, which are analyzed and used to carry out Surveys or for R&D.
- Job listings: Details regarding job openings, interviews are collected from different websites and then listed in one place so that it is easily accessible to the user.

## What is Web Scraping?
Web scraping is an automated method used to extract large amounts of data from websites. The data on the websites are unstructured. Web scraping helps collect these unstructured data and store it in a structured form. There are different ways to scrape websites such as online Services, APIs or writing your own code. In this article, we’ll see how to implement web scraping with python. 

## Is Web Scraping Legal?
Talking about whether web scraping is legal or not, some websites allow web scraping and some don’t. To know whether a website allows web scraping or not, you can look at the website’s “robots.txt” file. You can find this file by appending “/robots.txt” to the URL that you want to scrape. For this example, I am scraping Flipkart website. So, to see the “robots.txt” file, the URL is www.flipkart.com/robots.txt.

Why is Python Good for Web Scraping?
Here is the list of features of Python which makes it more suitable for web scraping.

1. Ease of Use: Python Programming is simple to code. You do not have to add semi-colons “;” or curly-braces “{}” anywhere. This makes it less messy and easy to use.
1. Large Collection of Libraries: Python has a huge collection of libraries such as Numpy, Matlplotlib, Pandas etc., which provides methods and services for various purposes. Hence, it is suitable for web scraping and for further manipulation of extracted data.
1. Dynamically typed: In Python, you don’t have to define datatypes for variables, you can directly use the variables wherever required. This saves time and makes your job faster.
1. Easily Understandable Syntax: Python syntax is easily understandable mainly because reading a Python code is very similar to reading a statement in English. It is expressive and easily readable, and the indentation used in Python also helps the user to differentiate between different scope/blocks in the code. 
1. Small code, large task: Web scraping is used to save time. But what’s the use if you spend more time writing the code? Well, you don’t have to. In Python, you can write small codes to do large tasks. Hence, you save time even while writing the code.
1. Community: What if you get stuck while writing the code? You don’t have to worry. Python community has one of the biggest and most active communities, where you can seek help from.

## How Do You Scrape Data From A Website?
When you run the code for web scraping, a request is sent to the URL that you have mentioned. As a response to the request, the server sends the data and allows you to read the HTML or XML page. The code then, parses the HTML or XML page, finds the data and extracts it. 

To extract data using web scraping with python, you need to follow these basic steps:

1. Find the URL that you want to scrape
1. Inspecting the Page
1. Find the data you want to extract
1. Write the code
1. Run the code and extract the data
1. Store the data in the required format 