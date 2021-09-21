# slack-to-rundeck
API Gateway (AWS) Definition to transpose Slack webhooks for Rundeck

In order to forward the webhook to _your_ Rundeck instance, either change the line in the YAML for the **URI**, or modify the **Endpoint URL** in the AWS Console after you've uploaded the API defintion:
<img width="1280" alt="Screen Shot 2021-09-21 at 12 55 50 PM" src="https://user-images.githubusercontent.com/11511251/134222729-948d137b-4de7-4364-955c-941c857414ae.png">


Follow this [doc](https://docs.aws.amazon.com/apigateway/latest/developerguide/import-export-api-endpoints.html) from AWS to import this yaml file to API Gateway.

**Note:** Make sure that you have selected **Rest API** as the type of API for your API Gateway.

This will forward the Slack "slash commands" (or "Interactive Components") to your defined Rundeck webhook.  Within Rundeck, you can parse the Slack command's text to determine which Rundeck job to run, as well as for Job Options: 
<img width="1349" alt="Screen Shot 2021-09-21 at 1 29 59 PM" src="https://user-images.githubusercontent.com/11511251/134227976-0807c3f7-9c01-4125-b4f3-ed971d89c548.png">

Here's an example payload from Slack:
<img width="1347" alt="Screen Shot 2021-09-21 at 1 30 49 PM" src="https://user-images.githubusercontent.com/11511251/134228024-ab82799a-8037-427f-b3bc-85e545d8ca0c.png">

Import the `sample_rundeck_job.yaml` to Rundeck to see an example of how to transpose the Slack slash-command text into job options.
