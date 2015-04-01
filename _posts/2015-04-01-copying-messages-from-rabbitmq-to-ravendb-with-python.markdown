---
layout: post_simple
title:  "Copying Messages from RabbitMQ to RavenDB with Python"
date:   2015-04-01 16:15:00

tags:
- ravendb
- rabbitmq
- python
---

Today I found myself needing to grab a copy of the messages in a [RabbitMQ](https://www.rabbitmq.com/) queue. After a few minutes of deliberation, I decided a quick and dirty way would be to use the [REST API provided by RabbitMQ](http://hg.rabbitmq.com/rabbitmq-management/raw-file/rabbitmq_v3_3_4/priv/www/api/index.html) to grab the messages and the [REST API provided by RavenDB](http://ravendb.net/docs/article-page/3.0/http/welcome) to shove them in to [RavenDB](http://ravendb.net). While it's perhaps not the most elegant solution, it is straight-forward and simple.

'''python
import sys
import json
import requests
import pprint

def dumpmessage():

    # RabbitMQ Stuff
    rabbit_url = 'http://myrabbitmqserver:15672/api/queues/myvhost/myqueue/get'
    rabbit_request_data = {'count': 1000, 'requeue': True, 'encoding': 'auto'}
    rabbit_request_json = json.dumps(rabbit_request_data)
    rabbit_request_headers = {'Content-type': 'application/json', 'Authorization': 'stuffgoeshere'}

    # RavenDB Stuff
    raven_url = 'http://myravendbserver:8080/docs'
    raven_request_headers = {'Raven-Entity-name': 'DumpedMessages'}

    rabbit_response = requests.post(rabbit_url, data=rabbit_request_json, headers=rabbit_request_headers)

    documents = rabbit_response.json()

    for document in documents:

        json_document = json.dumps(document)

        raven_response = requests.post(raven_url, data=json_document, headers=raven_request_headers)

        if raven_response.status_code != 201:
            pprint.pprint(raven_response.status_code)
            sys.exit('ERROR (' + str(raven_response.status_code) + '): ' + raven_response.text)

dumpmessage()
'''

The code itself is pretty easy to follow. In a nutshell:

1. Set up the RabbitMQ REST API request
2. Set up the RavenDB REST API request
3. Make a POST to RabbitMQ (in my case I'm limiting to 1000 and re-queuing) using [Requests](http://docs.python-requests.org/en/latest/)
4. Snag the JSON from the response (note that I should check for the HTTP response code, but I don't)
5. Iterate through each item and use the [JSON encoder and decoder](https://docs.python.org/2/library/json.html) in Python to turn the dictionary into a JSON string
6. Make a POST to RavenDB passing in the JSON serialized document
7. Check for an error and stop if something goes wrong

In about 30 lines of code (and it could be made shorter), I got the job done. Granted, it's not something everyone is likely to encounter, but it does demonstrate the power and usefulness of REST API's and a language like Python.
