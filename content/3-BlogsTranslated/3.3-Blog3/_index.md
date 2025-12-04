---
title: "Blog 3 (English Version)"
date: "2025-09-09T19:53:52+07:00"
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# Designing Serverless Integration Patterns for Large Language Models (LLMs)  
**Author:** Chris McPeek  
**Published:** October 4, 2024  
**Categories:** Amazon Bedrock, AWS Lambda, AWS Step Functions, Serverless  

_This article includes contributions from Josh Hart (Principal Solutions Architect) and Thomas Moore (Senior Solutions Architect)._

---

This article explores **best-practice integration patterns** for using **large language models (LLMs)** in **serverless applications**. These approaches help optimize performance, resource usage, and resiliency when integrating generative AI into your serverless architectures.

---

# Overview of Serverless, LLMs, and the Example Scenario

Organizations of all sizes are now leveraging LLMs to build next-generation generative AI applications that unlock new customer experiences.

Serverless technologies such as:

- **AWS Lambda**
- **AWS Step Functions**
- **Amazon API Gateway**

…enable teams to go from idea to production quickly, without needing to manage servers. The **pay-for-use** billing model also supports flexible scaling with optimized cost.

The examples in this article use **Amazon Bedrock**, a fully managed service that provides access to **foundation models (FMs)** via API. Similar principles apply when using LLMs hosted with other services such as Amazon SageMaker.

The example scenario illustrates using an LLM to generate engaging marketing content for launching a new family SUV model. Images used in the marketing content were generated using **Amazon Titan Image Generator**, as shown below.

---

# Direct Invocation from AWS Lambda

## Calling Amazon Bedrock directly from Lambda

The simplest serverless integration pattern is invoking Bedrock directly from a Lambda function using the AWS SDK.  
Below is a Python example using `boto3` to call the `InvokeModel` operation:

```python
import json
import boto3
brt = boto3.client(service_name='bedrock-runtime')

def lambda_handler(event, context):
    body = json.dumps({
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 1000,
        "messages": [{
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "Create a 500 word car advert given these images and the following specification: \n {}".format(event['spec'])
                },
                {
                    "type": "image",
                    "source": {
                        "type": "base64",
                        "media_type": "image/jpeg",
                        "data": event['image']
                    }
                }
            ]
        }]
    })

    modelId = "anthropic.claude-3-sonnet-20240229-v1:0"
    response = brt.invoke_model(
        body=body,
        modelId=modelId,
        accept="application/json",
        contentType="application/json"
    )

    response_body = json.loads(response.get("body").read())

    return {
        "statusCode": 200,
        "body": response_body["content"][0]["text"]
    }
