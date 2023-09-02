## AWS Cloud Cost Optimization - Identifying Stale Resources

**Identifying Stale EBS Snapshots**

In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

**Description :**

The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

* Create a EC2 instance -Ex Ubuntu
* Create a snapshot of volume 
	  - Ec2-Dashbord - snapshots - Create snapshot - Resource type - Volume
    - Select Volume ID(Which is used by created VM)
* Create a Lambda fuction 
   - Author from scrach - Keep default 
   - Function name: cost-optimization-ebs-snapshot (You can provide any name)
   - Runtime: Python 3.10 
   - Architecture : Nochanges 
   - Permission : By default, Lambda will create an execution role with permissions to upload logs to Amazon CloudWatch Logs. You can customize this default role later when adding triggers.   

* Code - code source - Test
* Copy code from : ebs_stale_snapshosts.py
* Click on deploy and then test
* configure test event
   - provide event name - test
   - Keep other options as default and save the event 
   - click on test it will fail with

  ```
  errorMessage": "An error occurred (UnauthorizedOperation) when calling the DescribeSnapshots operation: You are not authorized to perform this operation.",
  ```
  - Go to configuration tab edit timeout - change default to 10 sec (This is execution time)
  - configuration - permission- click on role - Add permissions- Attach policies
  - create a policy - select Ec2 - All EC2 action(For testing purpose providing all actions, you can select based on requirement)
  - resources -All and next provide name for policy - save it
  - Go back to role page attach newly created policy to role 
  - test the function : it will successfully execute but not delete snapshot as its used by active instance
  - For testing purpose - delete ec2 instance and test the function

  ```
  Function Logs
  START RequestId: 3a213eb1-1b02-441d-baa7-03b008a36bea Version: $LATEST
  Deleted EBS snapshot snap-0c72d5a161eb78642 as its associated volume was not found.
  
  ```
   You can do it using event driven using amazon eventbridge - to execute to schedule  
  
  







