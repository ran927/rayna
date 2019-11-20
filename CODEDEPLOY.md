
# Installing the CodeDeploy agent on EC2
```
yum update -y
yum install -y ruby wget
wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install
chmod +x ./install
./install auto
service codedeploy-agent status
```


# create a bucket and enable versioning
# aws configure --profile aws-devops-testpj
```
aws s3 mb s3://aws-devops-testpj-ran --region us-east-1 --profile aws-devops-testpj
aws s3api put-bucket-versioning --bucket aws-devops-testpj-ran --versioning-configuration Status=Enabled --region us-east-1 --profile aws-devops-testpj
```

# deploy the files into S3
```
aws deploy push --application-name CodeDeployTestPJDemo --s3-location s3://aws-devops-testpj-ran/codedeploydemo/app.zip --ignore-hidden-files --region us-east-1 --profile aws-devops-testpj
```