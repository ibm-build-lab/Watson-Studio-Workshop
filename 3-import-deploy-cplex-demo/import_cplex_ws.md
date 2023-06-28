# Deploying a CPLEX export file on Watson Studio utilizing Waston Machine Learning

In this tutorial, we want to learn how to create a CPLEX .lp model, import, and deploy into Watson Studio and Watson Machine Learning.

## Prerequisites
- Access to IBM Cloud Pak for Data as a Service
- Access to the Jupyter Notebook example


## Steps:

### 1. Create a Scenario
- Create a project. Select 'Create an empty project', enter a project name, and click 'Create'.
- On the 'Manage' tab of your project, select the 'Services and integrations' section and click 'Associate service'. Select an existing Machine Learning service instance (or create a new one) and click 'Associate service'.
- On the 'Assets' tab of your project, click 'New asset'.
- Select 'Jupyter notebook editor' and from the tabs, click 'From URL'
- Provide a name ex 'Import CPLEX Demo' and in the notebook URL, copy and paste `https://github.com/ibm-build-lab/Watson-Studio-Workshop/blob/main/3-import-deploy-cplex-demo/CPLEX%20Import%20demo.ipynb` into the input box and click 'Create'


### 2. Create a Deployment Space
- Click on the hamburger menu in the top left and click 'Deployments'
- Click 'New deployment space +' and give it a name such as 'CPLEX import demo', select your existing cloud object storage or create a new one. Select an existing Machine Learning service instance (or create a new one) and click 'Associate service' Finally click 'Create' 

### 3. Updating the playbook
- Go back to your project, click on the notebook you created in section 1.
- In the top right hand corner, click the pencil icon to start editing the notebook.
- In block 3, add your API key from [here](https://cloud.ibm.com/iam/apikeys) and use the following url for the Dallas region: `https://us-south.ml.cloud.ibm.com`. It should look like:
```
wml_credentials = {
      "apikey": "HU****************************7N",
      "url": "https://us-south.ml.cloud.ibm.com"
}
```
- In block 9, add your deployment space name. If you chose my example, it will be 'CPLEX import demo'.
- In the top left hand corner, click the double right arrow icon and select 'Restart and Run All Cells'

### 4. Results
- Go to the deployments and click on your deployment space.
- You should now see the Burger Production model has been added to the assets and a deployment has been ran.
- Go to the Jobs tab and click on the default job and then the completed run. The log of it's run will be displayed.
