# bnb-tracking

## to update the url and keywords, use the file goldenQuery.json

## to add a new ec2 instance to handle more requests:
1. lanuch an ec2 instance from AMI node_installed
1. add its elastic IP
1. add its IP to the db security group for db access
1. ssh and git pull the code
1. set up the cron jobs
   1. 0 15 * * * /usr/local/bin/node /home/ubuntu/airbnb/seo-tracking/rankcollector.js > /home/ubuntu/output/out.txt 2>&1
   1. 10 15 * * * /usr/local/bin/node /home/ubuntu/airbnb/seo-tracking/backup.js > /home/ubuntu/output/backup.txt 2>&1
1. add the instance id to the file instance.json
1. add the instance id to lambda function https://us-west-2.console.aws.amazon.com/lambda/home?region=us-west-2#/functions/bnb_start_stop?tab=configuration
1. stop the instance


## to update the capacity, use the file capacity.json
