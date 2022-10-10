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

* A link to a Trello board for the project => https://trello.com/b/CPy6L1Pe/azure-cicd-project
* A link to a spreadsheet that includes the project plan => https://github.com/Anindya711/udacity_cicd_project/blob/main/project-schedule.xlsx

## Instructions

* Architectural Diagram

<img width="816" alt="Screenshot 2022-10-09 at 12 32 18 PM" src="https://user-images.githubusercontent.com/46273941/194742758-9d7130a5-9a83-42b7-a91f-c0d5d54f0aa3.png">

## Continuous Integration
### Setting Azure Cloud Shell
* First, we need to setup an azure cloud shell. We can find the azure cloud shell in the azure portal. We need to click on the azure cloud shell icon and provide additional details to open up a cloud shell. Once launched the cloud shell would look like this, 
<img width="1247" alt="Screenshot 2022-10-07 at 10 38 04 PM" src="https://user-images.githubusercontent.com/46273941/194612548-60e3477a-0662-40e1-a6c2-524574a3958d.png">

### Creating a sample makefile to test local setup
 * For this, we need to first clone our personal github repo to the azure cloud shell. We would communicate between cloud shell and github using ssh keys, so we would need to first create the ssh keys. Please follow the following steps to clone the github repo to the azure cloud shell.
 ```
 ssh-keygen -t rsa
 ```
 * Copy the contents of id_rsa.pub and create a new SSH key in personal github account. Paste the content there.
 * Clone the github repo to azure cloud shell.
  ```
  git clone git@github.com:Anindya711/udacity_cicd_project.git
  ```
  <img width="1247" alt="Screenshot 2022-10-07 at 10 38 04 PM" src="https://user-images.githubusercontent.com/46273941/194612548-60e3477a-0662-40e1-a6c2-524574a3958d.png">
  
 * Then follow the steps mentioned in the udacity classroom lessons to create Makefile and requirements.txt in the github project.
 * Follow the below steps to create a python3 based virtual environment. Note, we might have to downgrade azure cloud shell python version to 3.7 to make this project work without any issues.

```
python3 -m venv ~/.udacitydevops
source ~/.udacitydevops/bin/activate
```
<img width="708" alt="Screenshot 2022-10-08 at 10 09 58 PM" src="https://user-images.githubusercontent.com/46273941/194718057-c4ece7be-6b9e-4954-bd10-b5c0c671a22d.png">

* Follow along the steps mentioned in the classroom to create the project scaffolding.
* run the following commands to test if the setup is working.

```
 make all
```
<img width="1792" alt="Screenshot 2022-10-08 at 10 16 20 PM" src="https://user-images.githubusercontent.com/46273941/194718312-f661ea9a-0074-4c96-beb8-d97494721680.png">

### Enable GitHub actions to test a simple python based Continuous Integration flow

* We would test continuous integration using GitHub actions.
* First, enable Github actions in the github website repo.
* Then, Replace yml code
Replace the pythonapp.yml code with the following scaffolding code.

name: Python application test with Github Actions
```
on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Python 3.6
      uses: actions/setup-python@v1
      with:
        python-version: 3.6
    - name: Install dependencies
      run: |
        make install
    - name: Lint with pylint
      run: |
        make lint
    - name: Test with pytest
      run: |
        make test
        
  ```
  * Screenshot of successful test.
  
 <img width="1790" alt="Screenshot 2022-10-08 at 10 32 53 PM" src="https://user-images.githubusercontent.com/46273941/194719026-5b9ed732-d731-4157-a6b8-da5cd9d3b0c6.png">
 
 ### Deploying the Flask app in Azure CloudShell
 
 * Next, we would test the Flask app locally in the azure cloud shell.
 * As per instructions, first we need to copy all the flask starter code from this repo to our project repo. https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/tree/master/C2-AgileDevelopmentwithAzure/project/starter_files
 * Execute the following command in the cloud shell.
 ```
 python app.py
 ```
 <img width="1288" alt="Screenshot 2022-10-08 at 10 47 40 PM" src="https://user-images.githubusercontent.com/46273941/194719582-7c63bdd9-34d1-4ec0-aedb-6af811f39c92.png">

* run the following command in a different cloud shell tab. We can see the shell script returning correct output.

```
./make_prediction.sh 
```
<img width="964" alt="Screenshot 2022-10-08 at 10 49 22 PM" src="https://user-images.githubusercontent.com/46273941/194719668-c061473b-db65-4944-aa77-e1c283c06855.png">

 ### Deploying the Flask app as a web server using Azure App Service
 [![Build Status](https://dev.azure.com/jayani1617/udacity-cicd-project/_apis/build/status/Anindya711.udacity_cicd_project%20(1)?branchName=main)](https://dev.azure.com/jayani1617/udacity-cicd-project/_build/latest?definitionId=6&branchName=main)
 
 * Create an azure web app from azure cloud shell. We can specify the python version while spinning up the webapp.

```
az webapp up -n ani-devops-webapp -g anidevops --runtime "PYTHON:3.7"
```
<img width="1355" alt="Screenshot 2022-10-08 at 11 57 00 PM" src="https://user-images.githubusercontent.com/46273941/194722168-d3d212ee-abd9-4162-8cac-8377916ea467.png">

* Once, the webapp is up and running, we can test the deployment by going to the website.
<img width="1530" alt="Screenshot 2022-10-08 at 11 55 51 PM" src="https://user-images.githubusercontent.com/46273941/194722141-a1ce343b-cb40-4131-9abe-f8a7bdfc20b9.png">

### Creating the Azure Devops pipeline
* We can see the app is now deployed to azure app service. Now, the final part of the project is to build a azure devops pipeline for continuous delivery.
More information on this process can be found [here](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl). The basic steps to set up the pipeline are:

* Go to https://dev.azure.com and sign in. Create an Azure Devops organization for hosting the project.
  Create a new private project. -Create a new service connection to Azure Resource Manager, select subscription and the app service.
  Create a new pipeline linked to your GitHub repo and select Python to Linux Web App on Azure to reuse existing template.

Screenshot of the azure devops pipeline successful run:
<img width="1521" alt="Screenshot 2022-10-09 at 12 08 09 AM" src="https://user-images.githubusercontent.com/46273941/194722588-e73bc28d-1fb5-43b9-b83e-70870f454f01.png">

Screenshot of the flask app output:
<img width="893" alt="Screenshot 2022-10-09 at 12 08 41 AM" src="https://user-images.githubusercontent.com/46273941/194722607-6c24e24c-058d-4543-963a-97469d870cd7.png">

Screenshot of azure website after updating the github code:

<img width="1102" alt="Screenshot 2022-10-09 at 10 14 05 AM" src="https://user-images.githubusercontent.com/46273941/194738509-295f113b-3041-44c7-b3c2-3937f44be069.png">

* Output of streamed log files from deployed application

<img width="1789" alt="Screenshot 2022-10-09 at 10 17 24 AM" src="https://user-images.githubusercontent.com/46273941/194738568-4e1039a5-8ced-4a6f-9057-26ed6c9255a7.png">

## Load Test
We will use locust to load test our website.
First install locust using below command.
```
pip install locust
```
Then, create a simple locust file to do our test.
And then run this command to start locust
```
locust --f locustfile.py
```
Once it starts, it will open in localhost:8089 location. We can go there and do load testing.
Here is a screenshot of our locust ui.

<img width="1792" alt="Screenshot 2022-10-10 at 8 14 19 PM" src="https://user-images.githubusercontent.com/46273941/194892743-568a2aef-5b08-4016-848d-44c18fa91938.png">

<img width="1787" alt="Screenshot 2022-10-10 at 8 14 46 PM" src="https://user-images.githubusercontent.com/46273941/194892829-df84a229-b8b9-4664-8b08-f329331d46c1.png">


## Enhancements
* We can try to build more on the website to make it user friendly. We can create a small webapp to test the predictions based on user input.
* We can try to improve model performance.

## Demo 

https://www.youtube.com/watch?v=yszTTINcu1g


