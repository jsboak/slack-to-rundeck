# slack-to-rundeck
API Gateway (AWS) Definition to transpose Slack webhooks for Rundeck

In order to forward the webhook to _your_ Rundeck instance, either change the line in the YAML for the **URI**, or modify the **Endpoint URL** in the AWS Console after you've uploaded the API defintion:
<img width="1280" alt="Screen Shot 2021-09-21 at 12 55 50 PM" src="https://user-images.githubusercontent.com/11511251/134222729-948d137b-4de7-4364-955c-941c857414ae.png">


Follow this [doc](https://docs.aws.amazon.com/apigateway/latest/developerguide/import-export-api-endpoints.html) from AWS to import this yaml file to API Gateway.

**Note:** Make sure that you have selected **Rest API** as the type of API for your API Gateway.
