# AWS Application Dollar Monitoring - S3 Writer For Athena
[![serverless](http://public.serverless.com/badges/v3.svg)](http://www.serverless.com)
[![Build Status](https://travis-ci.org/ServerlessOpsIO/aws-admi-s3-writer.svg?branch=master)](https://travis-ci.org/ServerlessOpsIO/aws-adm-s3-writer)
[![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause)

Application Dollar Monitoring provides granular AWS spend tracking. This will write items from [AWS Application Dollar Monitoring](https://github.com/ServerlessOpsIO/aws-application-dollar-monitoring/) so AWS S3 for analysis with AWS Athena or AWS Quicksight.

**This requires [AWS Application Dollar Monitoring]() to be deployed first.** This will subscribe to the SNS topic of that service and publish messages produced by it to S3.

![System Architecture](/diagram.png?raw=true "System Architecture")

## Deployment
### Application Deployment
Clone of this repository by using [Serverless Framework](https://serverless.com/).

```
$ npm install -g serverless
$ npm install
$ serverless deploy -v
```
### Application Dolar Monitoring Setup
You must deploy the [AWS Application Dollar Monitoring](https://github.com/ServerlessOpsIO/aws-application-dollar-monitoring/) service first.  That provides the billing report and ingestion pipeline.  This repository will subscribe to the message topic provided by that service.

## Usage
Once a report is run and Glue crawler has run, the `line_items` table will be available in the application_dollar_monitoring database.  Use [AWS Athena](https://aws.amazon.com/athena/) or [AWS Quicksight](https://aws.amazon.com/quicksight/) to query the data.
