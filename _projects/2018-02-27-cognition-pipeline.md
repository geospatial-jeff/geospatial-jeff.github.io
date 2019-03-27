---
title: 'Cognition-Pipeline'
subtitle: ''
date: 2019-02-27 00:00:00
description: Python framework for building serverless, event-driven, pipelines with the AWS ecosystem.
featured_image: '/images/cognition-pipeline/cover.png'
---
I've been developing a lot of serverless applications recently, and the [Serverless Framework](https://serverless.com/) has been helping a lot.  It's a widely-adopted open source toolkit written in Node.js for building and deploying serverless applications via configuration YAML files and code snippets.  The first application I experimented with was a simple REST API and my developer experience with the framework was great.  After successfully completing several smaller applications, I decided it was time to try building a larger application made up of multiple services each defined by their own Serverless application.  As the application grew bigger it quickly became very large and difficult to manage, I found myself in configuration hell.  I looked online for solutions and found that a lot of other developers were running into similar problems.

## Cognition-Pipeline
[Cognition-Pipeline](https://github.com/geospatial-jeff/cognition-pipeline) is a python infrastructure-as-code framework which abstracts the components of an AWS serverless application to provide an object-oriented interface for building customized data processing pipelines with Serverless Framework.  The application is deployed and executed exactly how it is written!

#### Building an Application
An application is made up of [lambda functions](https://github.com/geospatial-jeff/cognition-pipeline/blob/master/docs/Functions.ipynb), [event triggers](https://github.com/geospatial-jeff/cognition-pipeline/blob/master/pipeline/events.py), and [resources](https://github.com/geospatial-jeff/cognition-pipeline/blob/master/docs/Resources.ipynb).  The simplest possible application looks like this:

```python
from pipeline import Pipeline, events

# Application object
class MyFirstApplication(Pipeline):

    def __init__(self):
        super().__init__()

    @events.invoke
    def hello_world(self, event, context):
        print("Hello World!")

app = MyFirstApplication()

# Lambda handler
hello_world = app.hello_world

# Deploy handler
def deploy():
    app.deploy()
```
An application is defined from the `pipeline.Pipeline` object.  A lambda function is created by defining a method inside the `pipeline.Pipeline` object decorated with an event trigger.  The decorator determines how the lambda function is triggered.  All that is required to build a functioning application is a `pipeline.Pipeline` object with at least one lambda function.  If we want the application to interact with other AWS resources we may define a resource using the classes within the `pipeline.resources` module.  The below example defines a DynamoDB resource and uses an AWS API Gateway trigger.

```python
from pipeline import Pipeline, events
import uuid
import json

# Define and instantiate resources
class MyTable(resources.DynamoDB):

    def __init__(self):
        super().__init__()
        self.add_attribute('id', 'S')
        self.add_key('id', 'HASH')

table = MyTable()


class MySecondApplication(Pipeline):

    def __init__(self):
        super().__init__(resources=[table]) # Pass resources into init

    @events.http(path="app/create", method="post", cors="true")
    def put_table(self, event, context):
        payload = {
          'id': str(uuid.uuid1()),
          'data': json.dumps(event)
        }
        table.put(payload)

app = MySecondApplication()

put_table = app.put_table

# Deploy handler
def deploy():
    pipeline.deploy()
```
When a POST request is sent to the `app/create` endpoint of the application, the payload sent with the request will be inserted into the DynamoDB table.  We could extend this example to build a fully capable REST API.

#### Deployment
Once the application is ready, it is deployed through the `pipeline.deploy()` method which creates a Serverless Framework `configuration.yml` file describing the application.  Deploying the application then follows the standard Serverless deployment workflow.  If the application file has a deploy handler, as in the above examples, you may use the command line function `pipeline-deploy <pipeline_directory>` to build the application and deploy to AWS.  The deploy handler may also be used to declare changes to your application before deployment, as shown [here](https://github.com/geospatial-jeff/h3-dynamodb-geodatabase/blob/master/usa_cities_db/handler.py).

#### Future Work
The framework is in development and provides support for [limited resources and events](https://github.com/geospatial-jeff/cognition-pipeline/blob/master/docs/supported-features.ipynb).  I use the framework quite frequently, and will be adding more resources and events as I need them in my workflow.  The framework is essentially a wrapper of CloudFormation and has a standardized interface which makes it quite easy to extend!
