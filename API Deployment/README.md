## Deployment API in Python
Once you have an accurate model deployed for production, you’ll want to use it to get predictions about new data. If you don’t find any Peltarion connector for the tools that you use, you can always use the Deployment API in any programming language.
This page will show you examples of how to work with the Deployment API from Python, but you can also find more explanations and examples in other languages from the Deployment API page.

## Prerequisites
You need to create a deployment from the deployment view. The deployment view will show you the information you need to use the Deployment API:

All the input and output names (and shapes) of your model

The URL and deployment token to use for your requests

The status of the deployment. Make sure it is enabled, or queries will be denied

## How to use sidekick
sidekick is our Python library to facilitate working with the Peltarion APIs. You don’t strictly need it and we’ll show you how to work without it, but it can make your life easier so we’ll also show you how to use it.

You can install sidekick directly from GitHub by using this command in a terminal:

pip install git+https://github.com/Peltarion/sidekick#egg=sidekick

In your Python code, you can then use:

import sidekick

client = sidekick.Deployment(url=<URL>, token=<token>)

#Print metadata about the input and output features
print("input:", client.feature_specs_in)
print("output:", client.feature_specs_out)

to load the module and print metadata about the deployment.

## Examples
Submitting tabular data
See how to submit tabular data in cURL.

Tabular data is data whose features could be submitted inside a CSV file (i.e., single numeric value, categorical, or text).

Here are examples for submitting one example.

Sidekick
import sidekick

query = [{"Type": "animal", "Sound": "Miaow", "Size": 0.26}]

client = sidekick.Deployment(url=<URL>, token=<token>)
response = client.predict_many(query)
print(response)

Python
Submit a JSON formatted string as payload:

import requests

url = <URL>
token = <token>
header = {'Authorization': 'Bearer {}'.format(token), 'Content-Type': 'application/json'}

payload = '{"rows": [{"Type": "animal", "Sound": "Miaow", "Size": 0.43}]}'
response = requests.request("POST", url, headers=header, data=payload)
print(response.json())

Note that payload is a text string, but header can be passed directly as a Python dictionary object. You can also pass the payload as a Python dictionary object by using the json argument instead of data:

Submit a Python dictionary object as payload:

payload = {"rows": [{"Type": "animal", "Sound": "Miaow", "Size": 0.43}]}
response = requests.request("POST", url, headers=header, json=payload)

## Submitting images
You can also submit examples that have images as some of their features. In this case, you can send images of any size and the platform will automatically resize them to the expected resolution according to the settings specified on the datasets view.
The submission is always done via a JSON formatted text string, so you need to transform the images into text. The following examples show how to create a payload that you can use as above when some features are examples.

Sidekick
import sidekick
from PIL import Image

query = [{'Feature Name': Image.open('images/Number_6.png')},
         {'Feature Name': Image.open('images/Number_7.png')}]

client = sidekick.Deployment(url='<URL>', token='<token>')
response = client.predict_many(query)

Python
import requests
import base64
import os

def encode_image(image_file, img_type):
    encoded_image = 'data:image/{};base64,'.format(img_type) + base64.b64encode(image_file.read()).decode('ascii')
    return encoded_image

# The path to the image file
img_path = "images/Number_6.png"
# The image extension, 'jpg' and 'png' are supported
img_type = os.path.splitext(img_path)[-1][1:]

with open(img_path, "rb") as image_file:      # read file as binary
    image_as_text = encode_image(image_file, img_type)

payload = {"rows": [{"Feature Name": image_as_text, "Sound": "Miaow", "Size": 0.43}]}

url = <URL>
token = <token>
header = {'Authorization': 'Bearer {}'.format(token), 'Content-Type': 'application/json'}

response = requests.request("POST", url, headers=header, json=payload)

## Submitting arrays
Models can work with features that are multi-dimensional arrays. To train such models, you can import NumPy files as parts of your datasets.

When working with a deployed model, multi-dimensional arrays are passed as two JSON key-value pairs:

The shape key provides a list representing the shape of the array

The data key provides a list of all the array values, in row major order

The following examples show how to provide data for a 10 by 10 by 3 array
Python
payload = {"rows": [{"Array feature": {"shape": [10, 10, 3]}, "data": [1, 2, 3, 4, <...>, 299, 300] }]}

If you have the data available as a NumPy array A, you can create the same payload like this:

payload = {"rows": [{"Array feature": {"shape": list(A.shape), "data": A.flatten().tolist()}}]}

header = {'Authorization': 'Bearer {}'.format(token), 'Content-Type': 'application/json'}

response = requests.request("POST", url, headers=header, json=payload)
print(response.json())

Sidekick
With sidekick, you can give the NumPy array directly in the query:

import sidekick
import numpy as np

input_data = np.random.rand(10,10,3) #Sample data

query = [{'Array feature': input_data}]

client = sidekick.Deployment(url='<URL>', token='<token>')
response = client.predict_many(query)
print(response)
## Working with responses
When you submit a request, you will get a standard HTTP code telling you if the operation was successful or not. A value in the two hundreds usually indicate success, and four to five hundred indicates an error.

When successful, you will also receive a JSON formatted string as the payload of the response. This string contains the predictions for the list of submitted examples, or an error message if there was a problem (e.g., one of the examples submitted contained invalid data).

After sending a prediction request, e.g.,

import requests

url = <URL>
token = <token>
header = {'Authorization': 'Bearer {}'.format(token), 'Content-Type': 'application/json'}

payload = '{"rows": [{"Type": "animal", "Sound": "Miaow", "Size": 0.43}]}'
response = requests.request("POST", url, headers=header, data=payload)

you can get the status code with status_code:

print(response.status_code)

and the JSON message with json():

print(response.json())

Numeric predictions
See how to handle numeric predictions in cURL.

For numeric predictions (single number), the value is returned directly. The message looks like this:

{'rows': ['output name': 0.3740423, 'output name': 6.784281]}
## Categorical predictions
See how to handle categorical predictions in cURL.

For categorical predictions, every possible category is returned as a key, and the associated value gives the probability of the example belonging to that class. For example:

{'rows': ['output name': {'cat': 0.98, 'dog': 0.005, 'train': 0.005, 'car':0.01 }, 'output name': {'cat': 0.001, 'dog': 0.001, 'train': 0.899, 'car':0.1 }]}
## Image predictions
See how to handle image predictions in cURL.

If the output of the model is an image, it is returned encoded as a text string.

Sidekick
Sidekick will automatically convert the response to a PIL image object:

url = '<URL>'
token = '<token>'

client = sidekick.Deployment(url=url, token=token)
response = client.predict_many(query)
response[0]['Image feature'].show()

Python
In Python, you can convert the JSON response to an image like this:

shape = response.json()['rows'][0]['Array feature']['shape']
data = response.json()['rows'][0]['Array feature']['data']
A = np.array(data)
A = np.reshape(A, shape)
print(A)

Array predictions
See how to handle array predictions in cURL.

Sidekick
Sidekick will automatically convert multi-dimensional array features to NumPy arrays:

url = '<URL>'
token = '<token>'

client = sidekick.Deployment(url=url, token=token)
response = client.predict_many(query)
print(response[0]['Array feature'])

Python
You can convert the JSON response to an a NumPy array with Python code like this:

shape = response.json()['rows'][0]['Array feature']['shape']
data = response.json()['rows'][0]['Array feature']['data']
A = np.array(data)
A = np.reshape(A, shape)