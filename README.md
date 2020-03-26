# bnb-tracking
1. Each instance can handle 10 URLs per day, and each url contains 10 keywords.
1. Number of instances depending on the URLs we are going to track.
1. Instances will be started and stopped controlled by lambda functions.
1. Logs will be accessed through:
   1. https://backup-gethypeapp-com.s3-ap-northeast-1.amazonaws.com/seo_ranking/20200327/output.txt
   1. https://backup-gethypeapp-com.s3-ap-northeast-1.amazonaws.com/seo_ranking/20200327/output2.txt
   1. https://backup-gethypeapp-com.s3-ap-northeast-1.amazonaws.com/seo_ranking/20200327/output3.txt
   1. ...


## to update the url and keywords, use the file goldenQuery.json

## to add a new ec2 instance to handle more requests:
1. lanuch an ec2 instance from AMI bnb-rank-tracker
1. add its elastic IP
1. add its IP to the db security group for db access
1. [no need anymore] ssh and git pull the code
1. [no need anymore] set up the cron jobs
   1. 0 15 * * * /usr/local/bin/node /home/ubuntu/airbnb/seo-tracking/rankcollector.js > /home/ubuntu/output/out.txt 2>&1
   1. 10 15 * * * /usr/local/bin/node /home/ubuntu/airbnb/seo-tracking/backup.js > /home/ubuntu/output/backup.txt 2>&1
1. add the instance id to the file instance.json https://github.com/leo9/bnb-tracking/blob/main/instance.json
1. add the instance id to lambda function https://us-west-2.console.aws.amazon.com/lambda/home?region=us-west-2#/functions/bnb_start_stop?tab=configuration (DO NOT add i-00470bdcc73ce66e6 & i-0a7a433c7b9a51243 since these 2 instances need to be 24/7 running)
1. stop the instance


## to update the capacity, use the file capacity.json
