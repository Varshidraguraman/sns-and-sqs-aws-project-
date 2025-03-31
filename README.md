
***How send the notification to our mail id using sns service***
*Go to the sns service and create the topic 
*Next go to the subscription and select the protocal as email and give ,mail id
*Go to our mail and approve the confirmation mail from the aws 
*Then click on the publish message and write the boby message then click publish message
***sqs creation steps***

* First open our aws account and go to the simple queue serice (sns)
*Click on create button ---------go for standard 
*Select the visibility queue as per our requirement
*And click on create
*Next go to the sendand recevie messages Write on boday part
*next click on start poll messages and you we will recieve messages for very visibility timeout
*******Connecting my s3 bucket with sqs service *******
**If anyone of our teammate create or delete the file in s3 bucket it will automatically send the messages to my sqs queue**

*Create one s3 bucket
*And go to s3 properties and Event notifications then create the events
*In the event types object creation select what ever field you need to mointer 
*Select the destination as sqs , next you will get error(API RESPONSE)
****Troubleshooting part****
*go o the sqs acess policy and edit it we need to allow s3 in sqs
*Go to the sqs documention in aws and cong the s3 bucket with sqs documention 
*Copy the poilcy generarter just replace with our sqs arn,s3 arn and account id
*And then go to sqs acess policy and replace with new one and save it.
{
  "Version": "2012-10-17",
  "Id": "example-ID",
  "Statement": [
    {
      "Sid": "example-statement-ID",
      "Effect": "Allow",
      "Principal": {
        "Service": "s3.amazonaws.com"
      },
      "Action": "SQS:SendMessage",
      "Resource": "arn:aws:sqs:ap-south-1:022499023963:test",
      "Condition": {
        "StringEquals": {
          "aws:SourceAccount": "022499023963"
        },
        "ArnLike": {
          "aws:SourceArn": "arn:aws:s3:::testvarshid"
        }
      }
    }
  ]
}
****ERROR will resolve****
done

