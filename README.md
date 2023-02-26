# Project: Operationalizing Machine Learning

I have configured a cloud-based machine learning production model, deployed it, and used it in this end-to-end machine learning project on Microsoft Azure. I trained a machine learning model on the Bank Marketing Dataset using the AutoML feature of Azure Machine Learning Studio, deployed it into production using Azure Container Instance (ACI), and used REST APIs to consume it. Additionally, I created, released, and consumed a pipeline to fully automate the procedure.



## Architectural Diagram
![Architectural Diagram](https://user-images.githubusercontent.com/116864320/221395622-f62d3e3d-5532-43f3-83ad-13c32212155d.png)

The operational flow is depicted in the architectural diagram above. Let's clarify each action:

- Register The Dataset: Uploading the dataset into Azure Machine Learning Studio is required to register the dataset. Either the URL or an upload directly from a local folder can be used for this.
- AutoML Run: At this step, we configure the compute cluster, the type of machine learning task (in this case, classification), the exit criteria, etc. On our uploaded dataset, many models are trained using this.
- Deploy the best model: Here, using Azure Container Instance (ACI) or Azure Kubernetes Service (AKS), we choose the top-performing model from our AutoML run and deploy it into production.
- Enable logging and Application Insights: This can be carried out either during the model's deployment from the studio into production or thereafter using a Python script. This aids in monitoring the effectiveness of deployed models and the quantity of successful/failed requests.
- Consume Model Endpoints: After the model is deployed, a REST endpoint is created, allowing other services to communicate with the model. We are able to communicate with the deployed model and receive responses (predictions).
- Create and Publish a Pipeline: We can build and deploy a pipeline using a Jupyter Notebook and the Azure Python SDK. The working directory must contain a config.json file for this to work. We can completely automate the process of training and delivering our model using pipelines.


## Future Work

- Using a parallel run phase in the pipeline will help this project. 
- Testing a downloaded model in a local container. 
- Automating the entire workflow, from data preparation to machine learning jobs and deployment
- Using pipelines establishing a benchmark for ideal performance using the Apache Benchmark tool.

## Key Steps
**Authentication**: Within the course workspace, this was completed automatically. You must install the Azure Machine Learning Extension in order to interface with Azure Machine Learning Studio, which is a component of the az command, when working on your own Azure account. Once you have the Azure machine learning extension, you will need to create a Service Principal account and link it to the particular workspace you have chosen. 

**Automated ML Experiment**: This phase involved setting up an AutoML run and training many models using the Bank Marketing Dataset. Setting up a computing cluster, choosing the right machine learning problem, etc. is required. Our run has showed that `voting` ensemble is the model that performs the best.

**“Registered Datasets” in ML Studio shows "Bankmarketing" dataset**
![registered-datasets](https://user-images.githubusercontent.com/116864320/221395928-29744c36-0e08-48ca-97fa-1c51a5f6aea3.png)

**The experiment is shown as completed.**
![experiment-completion](https://user-images.githubusercontent.com/116864320/221395972-bb364a18-f77a-4f58-8102-90d0fa5d33e5.png)

**Best Model**
![best-model](https://user-images.githubusercontent.com/116864320/221396000-b016e0d8-6e1c-4aad-b1bf-965d88d0d44e.png)

**Deploy Best Model and Enable Logging:**We use Azure Container Instance (ACI) to deploy the best model from our AutoML run into production, and we have access to endpoints that other services can use to communicate with the model. In order to produce keys that other services can use to authenticate before interacting with our deployed model, we additionally enable authentication during deployment.

We are able to enable Application Insights and obtain logs after installing our best model (this can also be done during deployment).

**Endpoints section in Azure ML Studio, showing that “Application Insights enabled” says “true”**
![application_insights_true](https://user-images.githubusercontent.com/116864320/221396111-79e3fb42-dc90-4124-b019-626fcba9908f.png)

**Logging is enabled by running the provided logs.py script**
![deployment-logs](https://user-images.githubusercontent.com/116864320/221396134-f363d841-adbb-47ca-9855-d885b4403178.png)

**Swagger Documentation:** A tool for creating and documenting REST APIs is called Swagger. It can be utilised by different technologies to automate API-related operations as well as to exchange documentation among product managers, testers, and developers.

To establish a website that details the HTTP endpoint for a deployed model, Azure provides a swagger.json URL. Here, we used Swagger to consume our deployed model and display the contents of the model's API.

**Swagger runs on localhost showing the HTTP API methods and responses for the model**
![swagger](https://user-images.githubusercontent.com/116864320/221396255-9cccf404-983c-4bb4-b35f-fd35d3919322.png)

**Alter Data Dictionary From original endpoint.py**
Original endpoint.py code from github was missing the "Input" wrapper and had to be altered to produce results
![updated-endpoint py-result](https://user-images.githubusercontent.com/116864320/221396366-4f1b16a4-8aa4-43f2-8e61-f39c409f1a80.png)

**Endpoint.py output**
![python-endpoint py](https://user-images.githubusercontent.com/116864320/221396308-d9c7b43b-cc7c-45ab-97b8-007d5a4dbb73.png)

**Create, Publish, and Consume a Pipeline**: Here, we create, publish, and consume a pipeline as illustrated below using the Azure Python SDK and Jupyter Notebook

**The pipeline section of Azure ML studio, showing that the pipeline has been created**
![pipeline-created](https://user-images.githubusercontent.com/116864320/221396503-5181c3ef-fb50-4ab7-ae63-49a0fb9e6624.png)

**The Bankmarketing dataset with the AutoML module**
![pipeline-automated-ml](https://user-images.githubusercontent.com/116864320/221396571-2b087af3-706f-4e8e-a8ee-45ed8a87a554.png)

**The “Published Pipeline overview”, showing a REST endpoint and a status of ACTIVE**
![pipeline-endpoint](https://user-images.githubusercontent.com/116864320/221396606-ad64af83-1d23-466c-90fc-d07b7dabf1cb.png)

**A screenshot of the Jupyter Notebook is included in the submission showing the “Use RunDetails Widget” with the step runs**
![pipeline-run-details](https://user-images.githubusercontent.com/116864320/221396670-b932ec64-f050-4fae-b808-a1b858689d30.png)

**Pipeline Schduled Run**
![pipeline-scheduled-run](https://user-images.githubusercontent.com/116864320/221397076-96b3b853-8bdf-4f8f-b5e4-407d0429f67d.png)

**Pipeline EndPoints**
![pipeline-endpoints](https://user-images.githubusercontent.com/116864320/221397132-ba345c5e-b250-48cd-9bd2-01f2717b0bf3.png)

**Pipeline Automated ML**
![pipeline-automated-ml-1](https://user-images.githubusercontent.com/116864320/221397153-b06c7c0a-f4e2-4160-8f91-4ebc8ec33124.png)
![pipeline-automatedml-2](https://user-images.githubusercontent.com/116864320/221397157-d6c7b60b-10f3-4689-910d-e188dd2583ad.png)


## Screen Recording
Here a link to a screen recording of the project in action is provided. 
https://youtu.be/DRH5pTzNou4

I realised the recording was on recording my chrome window after the project timed out, what is missing is the API call to swagger which was made through command prompt available as proof in the screenshots above.