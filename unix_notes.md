## Unix Commands

## AWS EC2 Instance

Connect to my instance with:

ssh -i ~/Documents/BIMM143/bimm143_saket.pem ubuntu@ec2-18-246-209-91.us-west-2.compute.amazonaws.com

Secure Copy files between machines, in this case from our instance to our laptop

scp -i ~/Documents/BIMM143/bimm143_saket.pem ubuntu@ec2-18-246-209-91.us-west-2.compute.amazonaws.com:/home/ubuntu/work/bimm143/Class16Feb27/results.txt .



