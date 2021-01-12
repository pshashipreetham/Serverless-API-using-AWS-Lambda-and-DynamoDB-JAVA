# Serverless API using AWS Lambda (JAVA) and DynamoDB
This project contains source code and supporting files for a serverless application that you can deploy with the SAM CLI. It includes the following files and folders.
## Tool Required before start of this project:
1. Maven
2. Java 11 
3. SAM CLI [(install)](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)
4. AWS CLI [(install)](https://awscli.amazonaws.com/AWSCLIV2.msi)
5. POSTMAN Tool
6. OS: Windows 10 (can also be done on other Platforms if the Installation of AWS and SAM CLI's is done properly)<br />

**Note:** Don't Forget to setup the AWS CLI using the **AccessKey** and **SecretKey** which you will get when an IAM USER is created in the AWS
## Steps to make it run:
**Step 1:** Open the Powershell in the particular respective folder **ordersapi**<br>
**Step 2:** Use the following build command
```shell
sam build
```
**Step 3:** Use the following deploy command to package and deploy your application to AWS
```shell
sam deploy
```
**Note:** Here we are not using the **--guided** in the command since the repo files already built and deployed.

## Testing(If Deployed Successfully):
* Go to --> API Gateway in AWS --> ordersapi--> select **Stages** on the left side panel menu --> press on stages--> Copy the URL
* If Deployed Successfully you should see an GET and POST names in the **Resources** panel, as shown below:
```shell 
 /orders
GET
POST
```
* Open PostMan Tool 

### For Post Method:
* Select the POST method
* Paste the URL
* Select Body --> raw-->JSON and paste the following JSON data
```JSON
{
    "id": "1",
    "itemName": "dog",
    "quantity": 100
}
```
* Press **Send** <br/>

**Output:** <br>
```shell
Order ID: 123
```
**Note:** Make sure in Authorization select **TYPE** as  **AWS Signature** in the drop-down menu and don't forget to put the **AccessKey** and **SecretKey** which you will get when an IAM USER is created in the AWS which is also required to setup the AWS CLI. 

### For GET Method:
* Select the GET method
* Paste the URL
* Body --> None
* Press **Send**

**Output:** <br>
```JSON
{
    "id": "1",
    "itemName": "dog",
    "quantity": 100
}
```
**Note:** If more than one **POST** method is submitted using differnt id, itemName and quantity in the JSON, after that you use the **GET** Method then the output will be more than one JSON. For Example, the OUTPUT of **GET** method, after two many **POST** methods
```JSON
[
    {
        "id": 79,
        "itemName": "CAT",
        "quantity": 121
    },
    {
        "id": 78,
        "itemName": "dog",
        "quantity": 100
    }
]
```
## Resources:

See the [AWS SAM developer guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) for an introduction to SAM specification, the SAM CLI, and serverless application concepts.