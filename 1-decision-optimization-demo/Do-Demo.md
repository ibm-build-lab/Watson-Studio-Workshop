# Decision Optimization Model Using IBM Watson Studio

## Introduction
This tutorial guides you through the process of building, running, and deploying a Decision Optimization model with IBM's Watson Studio. Decision Optimization models assist in solving complex business problems by making optimized decisions based on input data and predefined constraints.

## Prerequisites
- Access to IBM Watson Studio and Watson Machine Learning
- Basic understanding of prescriptive analytics (not mandatory)

## End Goals
Upon completing this tutorial, you will have:
- Created a project
- Added a Decision Optimization Experiment
- Associated a Watson Machine Learning Service
- Deployed a model
- Run various scenarios and reviewed their results

## Steps:

### 1. Project Creation
- Start Watson Studio and create a project.
- Choose 'Create an empty project', provide a name, and link to an object storage service.

### 2. Add Decision Optimization Experiment
- Inside the project, add a Decision Optimization experiment.
- Use the option to upload the necessary data files.

### 3. Link Watson Machine Learning Service
- On the 'Services and Integrations' page, add the Watson Machine Learning service.
- From the list, select your Watson Machine Learning instance and associate it with the project.

### 4. Create Deployment Space
- Identify a deployment space to associate with the experiment.
- If not available, create a new one and link it to your experiment.

### 5. Data Review and Modeling
- Use the Modeling Assistant to inspect your data, objectives, and constraints.
- Convert your business problem into a mathematical formulation to create an optimization model.

### 6. Run Scenarios
- Execute different scenarios with the model.
- Review the outcome after each scenario.

### 7. Deploy Model
- If satisfied with the scenario results, proceed to deploy your model.
- Save and promote your model to the created deployment space.
- Initiate a new deployment with appropriate hardware definition, and await the deployment status to change to 'Deployed'.

By following these steps we should be able to successfully complete a Decision Optimization task on Watson Studio. More detailed document available [here](https://dataplatform.cloud.ibm.com/docs/content/wsj/getting-started/get-started-do.html?audience=wdp)