[![Python application test with Github  Actions test](https://github.com/Anindya711/udacity_cicd_project/actions/workflows/python-app.yml/badge.svg)](https://github.com/Anindya711/udacity_cicd_project/actions/workflows/python-app.yml)

# Overview
This project is part of Data Engineer for SHELL (IDA) scholarship program arranged by Udacity.
The goal of this project is to demonstrate CICD concepts using Microsoft Azure services.
It consists of a python based flask application to predict housing prices in Boston (Provided in a starter code).

This repositry demonstrate:
> Setting Azure Cloud Shell

> Enable GitHub actions to test a simple python based Continuous Integration flow

> Deploying the Flask app in Azure CloudShell

> Deploying the Flask app as a web server using Azure App Service.

> Demonstrate CI using GitHub actions for a sample python application.

> Demonstrate CD using Azure Devops pipeline.


## Project Plan
<TODO: Project Plan

* A link to a Trello board for the project
* A link to a spreadsheet that includes the original and final project plan>

## Instructions

<TODO:  
* Architectural Diagram (Shows how key parts of the system work)>

## Continuous Integration
### Setting Azure Cloud Shell
* First, we need to setup an azure cloud shell. We can find the azure cloud shell in the azure portal. We need to click on the azure cloud shell icon and provide additional details to open up a cloud shell. Once launched the cloud shell would look like this, 
<img width="1247" alt="Screenshot 2022-10-07 at 10 38 04 PM" src="https://user-images.githubusercontent.com/46273941/194612548-60e3477a-0662-40e1-a6c2-524574a3958d.png">

### Enable GitHub actions to test a simple python based Continuous Integration flow

 > ssh-keygen -t rsa

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run

* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
udacity@Azure:~$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application

> 

## Enhancements

<TODO: A short description of how to improve the project in the future>

## Demo 

<TODO: Add link Screencast on YouTube>


