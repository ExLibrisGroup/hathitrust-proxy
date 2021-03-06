# Hathitrust Proxy

The [Hathitrust API](https://www.hathitrust.org/data) has two endpoints- a [Bibliographic API](https://www.hathitrust.org/bib_api) and a [Data API](https://www.hathitrust.org/data_api). The data API is restricted and requires a key and secret to access, which can be obtained using the [Hathitrust Key Service](http://babel.hathitrust.org/cgi/kgs/request). 

This repository is a proxy for the Hathitrust API, wrapping the requests in the OAuth 1.0a authentication scheme supported by the API. It is meant to be deployed to the AWS Serverless infrastructure, and includes a template for easy deployment. 

## Pre-Requisites
You must obtain a key/secret pair at the [Hathitrust Key Service](http://babel.hathitrust.org/cgi/kgs/request). The proxy expects the key and secret to be available in the `HATHITRUST_KEY` and `HATHITRUST_SECRET` environment variables.

## Authentication
This proxy was developed for use with [Ex Libris Cloud Apps](https://developers.exlibrisgroup.com). It includes an AWS API gateway authorizer function that validates the auth token provided by Cloud Apps. For more information, see the Cloud Apps documentation.

## Deploy to AWS
This app is available in the [AWS Serverless Application Repository](https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:523567452838:applications~hathitrust-proxy). Follow the instructions below to deploy it using your own AWS account and Hathitrust credentials.

1. Click to [Deploy the Serverless Application](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:523567452838:applications/hathitrust-proxy) from the AWS Console.
2. Fill out the parameters in the _Application settings_ section and click the _Deploy_ button.
3. AWS will create the necessary components. When it's complete, the wizard will indicate that the application has been deployed.
4. Click the _View CloudFormation stack_ link, then click the _Outputs_ tab to retrieve the URL of the proxy.
