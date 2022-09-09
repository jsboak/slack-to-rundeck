# slack-to-rundeck
API Gateway (AWS) Definition to transpose Slack webhooks for Rundeck

## Create API Gateway

In order to forward the webhook to _your_ Rundeck instance, either change the line in the YAML for the **URI**, or modify the **Endpoint URL** in the AWS Console after you've uploaded the API defintion:
<img width="1280" alt="Screen Shot 2021-09-21 at 12 55 50 PM" src="https://user-images.githubusercontent.com/11511251/134222729-948d137b-4de7-4364-955c-941c857414ae.png">

Follow this [doc](https://docs.aws.amazon.com/apigateway/latest/developerguide/import-export-api-endpoints.html) from AWS to import this yaml file to API Gateway.

**Note:** Make sure that you have selected **Rest API** as the type of API for your API Gateway.

This will forward the Slack "slash commands" (or "Interactive Components") to your defined Rundeck webhook.  Within Rundeck, you can parse the Slack command's text to determine which Rundeck job to run, as well as for Job Options: 
<img width="1349" alt="Screen Shot 2021-09-21 at 1 29 59 PM" src="https://user-images.githubusercontent.com/11511251/134227976-0807c3f7-9c01-4125-b4f3-ed971d89c548.png">

Copy the **Invoke URL** from the **Stages** tab:
![Screen Shot 2022-09-08 at 6 03 27 PM](https://user-images.githubusercontent.com/11511251/189251031-21c333c1-1911-4d12-8856-11c11dd4b236.png)


## Create Slack App
The next step is to create a basic Slack app that allows you to define your Slash commands.  Documentation for setting that up is [here](https://api.slack.com/interactivity/slash-commands).  

Paste the **Invoke URL** from the API Gateway into the Slash command **Request URL**:
![Screen Shot 2022-09-08 at 6 05 54 PM](https://user-images.githubusercontent.com/11511251/189251120-64a1ddaa-7785-4c9d-9dea-2e99e1c4b00f.png)

## Usage
Here's an example payload from Slack:
<img width="1347" alt="Screen Shot 2021-09-21 at 1 30 49 PM" src="https://user-images.githubusercontent.com/11511251/134228024-ab82799a-8037-427f-b3bc-85e545d8ca0c.png">

Import the `sample_rundeck_job.yaml` to Rundeck to see an example of how to transpose the Slack slash-command text into job options. 
This is what the corresponding slash command would look like for this sample job:

<img width="595" alt="Screen Shot 2021-09-23 at 5 09 37 PM" src="https://user-images.githubusercontent.com/11511251/134599523-8f228535-e568-46eb-b6ba-fc790b45ea24.png">

<img width="605" alt="Screen Shot 2021-09-23 at 5 10 18 PM" src="https://user-images.githubusercontent.com/11511251/134599527-96c59199-8000-4d5e-b119-080134aa773e.png">
