# [Use a DynamoDB Scan operation (carefully) in AWS Console](https://egghead.io/lessons/aws-use-a-dynamodb-scan-operation-carefully-in-aws-console?pl=learn-aws-dynamodb-from-scratch-21c3)

- There are multiple ways to retrieve data with DynamoDB.

- The most straightforward is Scan.
  - This operates on the entire table and returns all of the relevant results up to 1MB.
  - This is fine for small collections but with millions of records this is going to be a very expensive operation.
  - Adding a filter _does not_ limit the number of records that are _read_ during a scan operation.
  - Even if we get a filtered list back, every record in the table is checked and then the filter is applied.

## Personal Take

Good warning here to be careful of the scan operation. I'd assumed that the filter was indeed only accessing those items, I had no idea that every item was being hit!
