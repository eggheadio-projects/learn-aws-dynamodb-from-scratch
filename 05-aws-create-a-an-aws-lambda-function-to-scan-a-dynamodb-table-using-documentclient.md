# [Create a an AWS Lambda function to scan a DynamoDB table using DocumentClient](https://egghead.io/lessons/aws-create-a-an-aws-lambda-function-to-scan-a-dynamodb-table-using-documentclient?pl=learn-aws-dynamodb-from-scratch-21c3)

- We can use a lambda function to scan our table.

- We need to make sure that our lambda has the right permissions

  - Use IAM to add basic lambda permissions and DynamoDB readonly access to a new role.
  - Remember only give the least possible permissions
  - You can tag.
  - Give it a helpful name.

- Then create a lambda function that uses this existing role.

- We're going to use Node v12 and the DynamoDB document client. This is a high-level API that gives access to the DynamoDB instance without having to go through the console.

- First import the `AWS SDK` and create a new document client.

```js
const AWS = require("aws-sdk");
const dynamo = new AWS.DynamoDB.DocumentClient();
```

- Next, we create a function that will get all of the documents. We need to add a new environment variable for our table name.

```js
const getAllRecords = async () => {
  const scanResult = await dynamo
    .scan({ TableName: process.env.TABLE_NAME })
    .promise();

  return scanResult;
};
```

- We have to use the promise function so that `await` receives the promise it requires.

- Now, we can use this function in our handler.

```js
exports.handler = async (event) => {
  const data = await getAllRecords();

  const response = {
    statusCode: 200,
    body: JSON.stringify(data),
  };

  return response;
};
```

- We can use a test event to check that this correctly returns all of our records as we expect.

## Personal Take

It's good to remember the test ability within the AWS console - I think I would normally just write code to check. This is definitely something I need to keep in mind.
