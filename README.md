# Kite AI Trial Documentation

## Introduction

Welcome to Kite AI's trial documentation. Here, you'll find everything you need to know, from setting up your environment, to analyzing results. Have any questions? Feel free to reach out to us at any time.

If you're new to this, try out our Quick Start below. If you've done this before or need a more customized trial, view the documentation below.

## Quick Start

For this example, we'll be using Python to take user input, make a request to the API, and return a result, all in less than 20 lines of code.

### Setup

Ensure you have Python installed. Open your preferred text editor, or type `python` in the terminal.

### Requirements

The benefit of Kite AI is that it's as easy to set up as it is to use. Using a language like Python means you can use built-in libraries like `requests` and `json`.

Import these into the file.

```
# trial.py

import requests
import json
```

### Adding Data

You'll need an key to use the API, which should have been emailed to you. If you don't have this already, contact sales@kiteai.com to set up a demo.

Once you have the API key, add it as a variable to make it easy to identify or change later on.

```
api_key = 'insert_api_key'
```

Since we're just starting with the API, let's make it something we can play around with. For this, we'll use `raw_input`, or `input` if you're using `Python3`.

Additionally, we should make a dictionary including the phrase, in case we need to add more elements later on.

```
phrase = raw_input('Enter a phrase: ')

data = {
  'phrase': phrase
}
```

### Setting the headers

Now it's time to set the headers, where we include information like the `Content-Type` and API key. We'll make this a dictionary to so it's easy to digest.

```
headers = {
  'Content-Type': 'application/json',
  'x-api-key': 'insert_api_key'
}
```

### Making the request

Now, we're ready to make a request. Create a variable called `response`, and add the required data and headers.

```
response = requests.post('https://api.kiteai.com/predict', data=json.loads(data), headers=headers)
```

### Analyzing the results

We've made the request, now we can view the results. Making a `POST` request to `/predict` will return a response that looks like this:

```
{
    "is_abusive": false,
    "phrase": "Hey, this is pretty cool!",
    "success": true
}
```

It's return in `JSON`, so to access the elements we can call `response.json()` which will return the `is_abusive` value containing `true` or `false`.

```
is_abusive = response.json()['is_abusive']
```

### Printing the result

Once we have `is_abusive`, we can either print out the result, add it to a database, or more.

In this instance, we'll print it out.

```
print 'Phrase: ' + phrase + '\n' + 'is_abusive: ' + str(is_abusive)'
```

### Wrapping it all up

In less than 20 lines of code, we've built a program using Python that takes user input, analyzes it using Kite AI's API, and prints the result.

Your code should look like this:

```
# trial.py

import requests
import json

api_key = 'insert_api_key'

phrase = raw_input('Enter a phrase: ')

data = {
  'phrase': phrase
}

headers = {
  'Content-Type': 'application/json',
  'x-api-key': 'insert_api_key'
}

response = requests.post('https://api.kiteai.com/predict', data=json.loads(data), headers=headers)

is_abusive = response.json()['is_abusive']

print 'Phrase: ' + phrase + '\n' + 'is_abusive: ' + str(is_abusive)'
```

Running `trial.py` will look something like this:

```
$ python trial.py
Enter a phrase: Hey, this is pretty cool!
Phrase: Hey, this is pretty cool!
is_abusive: False
```

To learn more about the API endpoints and methods you can use, check out the documentation below. For support or questions, email one of our team members and we'll get in touch!
