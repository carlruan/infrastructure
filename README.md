# infrastructure For csye 6225 infrastructure

# AWS init

$ aws configure --profile=name  
$ export AWS_PROFILE=name  
$ export AWS_REGION=us-east-1

# Cloudforamtion

$ aws cloudformation create-stack --stack-name myvpc --template-body file://csye6225-infra.yml

# cloudformation update

$ aws cloudformation update-stack --stack-name myvpc --template-body file://csye6225-infra.yml

# cloudformation delete

$ aws cloudformation delete-stack --stack-name myvpc --template-body file://csye6225-infra.yml

# Cloudformation with AMI

$ aws cloudformation create-stack --stack-name finalTest --template-body file://csye6225-infra.yml --parameters ParameterKey=myImageId,ParameterValue=ami-0d978b6fb2786ba5a

# Cloudformation with IAM role

$ aws cloudformation create-stack --stack-name myvpc --template-body file://csye6225-infra.yml --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=myImageId,ParameterValue=ami-0d978b6fb2786ba5a

# Delete S3

$ aws s3 rm s3://ee9b7ac0.dev.kaifengruan.me --recursive

# Connect to RDS

$ sudo yum install mariadb -y
$ mysql -h csye6225.ccncdoynfjlc.us-east-1.rds.amazonaws.com -u csye6225 -p
$ SELECT id, user, host, connection_type FROM performance_schema.threads pst INNER JOIN information_schema.processlist isp ON pst.processlist_id = isp.id;

# import SSl

$ aws acm import-certificate --certificate fileb://prod_kaifengruan_me.crt --certificate-chain fileb://prod_kaifengruan_me.ca-bundle --private-key fileb://prod_kaifengruan_me.pem

$ aws cloudformation create-stack --stack-name myvpc --template-body file://csye6225-infra.yml --capabilities CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND --parameters ParameterKey=CertificateArn,ParameterValue=
