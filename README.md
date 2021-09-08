# Project 2. Operationalizing Machine Learning in Azure

## Overview
This project is a second part of the Udacity Azure Machine Learning (ML) Nanodegree program. 
In this project, our interest is to build an ML model, deploy the model, and consume it through HTTP API. 
Data is bank marketing data. 
The data is used to build a binary classification model that predicts 
if a customer subscribes a term deposit (variable y) using the bank marketing data.
The model was built using Automated ML (AutoML) service in Azure ML Studio. 
The AutoML identified the best model of VotingEnsemble with the accuracy of ~0.92. 
This model was deployed and tested through HTTP API.

We built an ML pipeline using Azure ML SDK in Python. 
A HyperDrive is used to determine optimal hyperparameters for a logistic regression model 
that is implemented using scikit-learn library. 
The two hyperparameters: the inverse of regularization (C) and the maximum number of iterations (max-iter) 
were tested in this project.
The HyperDrive found out a pair of C~0.19 and max-iter=500.
The logistic regression model trained with the two hyperparameters showed the accuracy of ~0.91.
This optimized logistic regression model was then compared to the optimal model of VotingEnsemble from an Azure AutoML run.
The accuracy of the VotingEnsemble model was ~0.92, which showed slight improvement compared to the logistic regression obtained through HyperDrive.

## Architectural Diagram
*TODO*: Provide an architectural diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

A diagram for the model deployment and consumption through REST API.  
![BankMarketing Data is registered](/images/03_procedure_diagram.png)


Bank marketing data was uploaded into Datastore with the name of "BankMarketing Dataset". 
AutoML run on BankMarketing Dataset to build a classification model. 
The best model was deployed. 
Application Insight was enabled.
Output API was tested using Swagger. 
The model was tested by requesting outputs for the two inputs.

## Future work
I will make the pipeline multifunctional. 
It includes the interaction with the current data and checking the anomalies in the incoming dataset. 
The pipeline will be set up to automatically run whenever the accuracy becomes below a threshold such as 0.88.

## Key Steps
Bank Marketing Data is uploaded in datastore. Its name is "BankMarketing Dataset".  
![BankMarketing Data is registered](/images/registered_dataset_bankmarketing_00.png)

AutoML Run completed with the best model of VotingEnsemble with the accuracy of ~0.92.  
![Completion of AutoML run](/images/completed_automl_run_01.png)

The Best model named to be "automl-best-model" is deployed.  
![Best model is deployed](/images/bestmodel_VotingEnsemble_deployed_02.png)

Run logs.py.  
![run logs.py](/images/run_logs_03.png)

Running logs.py enabled Application Insights. RESTful API and Swagger URI are available.  
![Application Insights is enabled](/images/application_insights_enabled_04.png)

Swagger runs on localhost:8000 that the HTTP API methods and responses for the model.
![Swagger](/images/run_swagger_05.png)


endpoint.py runs against the API producing JSON output from the model. 
The result of endpoint.py is shown.  
![Endpoint](/images/08_result_endpoint.png)

### Key steps to Publish an ML Pipeline
A pipeline of Bank marketing data training was created in the notebook. 
While the pipeline was running, its status was checked and its RunDetails was periodically observed.  
After the completion, the pipeline was deployed. 
The endpoint of the deployed pipeline was checked.  

A running status of Pipeline that shows Bankmarketing data with the AutoML module  
![Created Pipeline](/images/10_pipeline_running.png)

Run Details is shown to be complete.  
![Run Details](/images/09_pipeline_complete.png)

A screen shot of Bankmarketing data with the AutoML module  
![Run Details](/images/09_pipeline_complete_01.png)

"Published pipeline overview" shows the active status of the published pipeline and its REST API.  
![Active Pipeline](/images/11_pipeline_published_active.png)

The pipeline was updated to run in schedule of every 2 hours.  
![Schedule Run Pipeline](/images/12_pipeline_published_active_scheduledrun.png)


## Screen Recording
A link to a screen recording of the project in action:  
https://youtu.be/XgZngK5Zx8c

* The screen cast shows the completion of AutoML model and the deployment of its best best (VotingEnsemble). 
* It shows the availablity of the model endpoint and how it is consumed.
* One sample request is shown.
* It shows AutoML pipeline is deployed at the end.

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
