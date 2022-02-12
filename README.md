Slot machine demo:

1. Create Dynamo Db table `SlotPositionTable`
   - partition key: `slotPosition`
   - populate data using: `dynamo_data.js`
   - create policy - `polices/SlotPositionTableReadPolicy.json`
  
2. Create Lambda `SlotPullLambda`
   - create role for lambda
   - code from: `lambda_slotpulll.js`
   - test :)
   - create policy - `/polices/SlotPullLambdaInvokePolicy.json

3. Create Cognito Identity Pool
   - copy its identifier
   - configure role for unathenticated identity
  
4. create bucket `slot-machine-demo`
   - update static files with id of identity pool
   - sync files with bucket
   - enable static webside hosting
   - make bucket public

```
aws s3 mb s3://slot-machine-demo
aws s3 sync ./static s3://slot-machine-demo`
```