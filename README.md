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
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
