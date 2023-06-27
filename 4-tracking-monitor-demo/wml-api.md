# Watson Machine Learning API for Monitoring Models, Deployments, and Jobs

This is a brief walkthrough on how to utilize the WML WPI via curl commands to connect and obtain information about the various assets in Wastson Studio.

## Steps:

### 1: Generating an IAM token
- Obtain your IBM Cloud API key [here](https://cloud.ibm.com/iam/apikeys)
- Run the command:
```
curl "https://iam.bluemix.net/identity/token" \
  -d "apikey=YOUR_API_KEY_HERE&grant_type=urn%3Aibm%3Aparams%3Aoauth%3Agrant-type%3Aapikey" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Authorization: Basic Yng6Yng="
```
- The output will look similar to:
```
{
   "access_token": "****** obtained IAM token ******************************",
   "refresh_token": "**************************************",
   "token_type": "Bearer",
   "expires_in": 3600,
   "expiration": 1554117649,
   "scope": "ibm openid"
}
```

### 2: Models
- Obtaining all the models by substituting the space_id with a deployment space and/or project_id
```
curl -X GET 'https://us-south.ml.cloud.ibm.com/ml/v4/models?space_id=<string>&project_id=<string>&version=2020-09-01' \
  -H "Authorization: bearer TOKEN-HERE"

```
- Use the output to retrieve a specific model by utilizing the model_id
```
curl -X GET 'https://us-south.ml.cloud.ibm.com/ml/v4/models/:model_id?space_id=<string>&project_id=<string>&rev=<string>&version=2020-09-01' \
  -H "Authorization: bearer TOKEN-HERE"
```
- You can then check the metrics and many other options as seen from the [api docs](https://cloud.ibm.com/apidocs/machine-learning#models-get)


### 3: Deployments
- Obtain all the deployments to get a specific deployment_id by replacing the space_id
```
curl --location --request GET 'https://us-south.ml.cloud.ibm.com/ml/v4/deployments?space_id=<string>&version=2020-09-01' \
  -H "Authorization: bearer TOKEN-HERE"
```

- Use the output to retrieve a specific model by utilizing the deployment_id
```
curl --location "{url}/v4/deployments/{deployment_id}" \
  -H "Authorization: bearer TOKEN-HERE"
```
- You can then check the status and many other options as seen from the [api docs](https://cloud.ibm.com/apidocs/machine-learning#deployments-get)

### 4: Jobs
- Obtain all the jobs to get a specific job_id by replacing the space_id
```
curl --location --request GET 'https://us-south.ml.cloud.ibm.com/ml/v4/deployment_jobs?space_id=<string>&version=2020-09-01' \
  -H "Authorization: bearer TOKEN-HERE"

```
- You can then check the logs, scoring  and many other options as seen from the [api docs](https://cloud.ibm.com/apidocs/machine-learning#deployment-jobs-list) 