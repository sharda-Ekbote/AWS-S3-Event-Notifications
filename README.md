# AWS-S3-Event-Notifications
AWS S3 Event Notifications let you get alerts when things happen in your bucket—like object creates, deletions, restores, tagging, and lifecycle transitions. Notifications can be sent to SQS
Step 1: Login to aws management console and move to s3 dashboard.

Step 2: Select the bucket for event notification or create a new bucket.Here we will create a new bucket.

Step 3: To create a new bucket ,name the bucket that is globally unique,and select the region for it ,”ACLs disabled” in object ownership,block public level access and leave all the settings by default and click on “create Bucket”.

Step 4: after creating the bucket ,click on the bucket and go to its properties .In properties,go to event notification.

Step 5 : click on “create event notification”.for creating the event notification:
      ●	name the event .
      ●	prefix and suffix are optional(we not need here)  
      ●	select the event types ,as there are various options as per our requirements we can select multiple options but here we select  “All object create events”
      ●	Select the destination: as we have three options as destination (lambda,SNS or SQS).here we select SQS queue.

Step 6: now we have to select SQS for event notification so now first we have to create a SQS queue.

Step 7: to create a SQS ,search for SQS in the search bar and navigate to SQS dashboard.Then click on “create queue”.

Step 8: To create a queue:-
    ●	select the queue type as “Standard” 
    ●	name the queue
    ●	Manage configuration: you can change the configurations  but here we kept it by default
    ●	Encryption will be “disabled” and encryption key type will be “Amazon SQS key(SSE-SQS)” .
    ●	Access policy : choose the “advanced” access policy and we have to change the policy .To change the policy click on “policy generator to create a new policy.
    
Step 9: In policy generator ,select the “SQS queue policy” type of policy and then “allow” effect and principal will be “*” and actions your can select multiple but here for event notification we only need one action i.e.,”send message” then  paste the arn of your SQS queue in the ARN section.(for ARN,copy the arn of queue from default access policy).

Step 10: after pasting the ARN ,click on “add statement “ and then on “generate policy” .After that copy the policy and paste into the queue access policy.

Step 11: After updating the access policy of the queue ,click on save changes and leave all the settings by default and click on create queue.

Step 12: now,move to s3 event notification,and select the created SQS queue as destination and click on “create event notification”.

Step 13: After creating queue and event notification,click on your created queue and click on “send and receive messages”. And then to receive messages ,click on “poll for message”.
Step 14: after that you will get a message of s3 bucket .
Step 15: Now for testing purposes ,upload a file or folder in the s3 bucket and again navigate to the queue ,and click on “poll for messages”.You will get two messages :one for s3 bucket and second for uploading an object in the bucket.
Step 16: This is all how event notification works!!



