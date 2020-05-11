# [Add a new item to a DynamoDB table in AWS Console using JSON editor](https://egghead.io/lessons/aws-add-a-new-item-to-a-dynamodb-table-in-aws-console-using-json-editor?pl=learn-aws-dynamodb-from-scratch-21c3)

- We can create items directly in the AWS Console using a JSON editor.

- Click Create Item in the items pane of the DynamoDB console.

- Change from Tree->Text in the top left.

- We can paste in the JSON object. Exactly like before, we only _have_ to provide our primary key as the type that we provided when we created the table - every item has to have a unique lesson title

- The DB doesn't save our data as JSON, rather it use DynamoDB JSON.

- In the text view, you can click the checkbox to see how the JSON will be rendered in DynamoDB JSON. Equally, you can flick back to the Tree mode to see if it has been rendered as you'd expect.

## Personal Take

Being able to switch back and forth between JSON/DynamoDB JSON/Tree view is really helpful to make sure that the code you're writing to create items is the correct format and doing what you expect.
