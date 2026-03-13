## Unix Commands

curl: download files from web or ftp
wget: download files from web
tar -zxvf :UnTar (unpackage) Tar archive files
gunzip: unzip files
$PATH: the places (dirs) to look for programs

## AWS EC2 Instance

Connect to my instance with:

ssh -i ~/Documents/BIMM143/bimm143_saket.pem ubuntu@ec2-18-246-209-91.us-west-2.compute.amazonaws.com

Secure Copy files between machines, in this case from our instance to our laptop

scp -i ~/Documents/BIMM143/bimm143_saket.pem ubuntu@ec2-18-246-209-91.us-west-2.compute.amazonaws.com:/home/ubuntu/work/bimm143/Class16Feb27/results.txt .

## Class 17 Instance

ssh -i ~/Documents/BIMM143/bimm143_saket.pem ubuntu@ec2-54-190-193-107.us-west-2.compute.amazonaws.com

export KEY=~/Documents/BIMM143/bimm143_saket.pem
export SERVER=ubuntu@ec2-54-190-193-107.us-west-2.compute.amazonaws.com

ssh -i $KEY $SERVER
scp -r -i $KEY $SERVER:~/*_quant .

