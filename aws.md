### Configure aws
```
aws configure
```

### List regions
```
aws ec2 describe-regions --output table
```

### Create security group
```
aws ec2 create-security-group --group-name workshop --description "Security group for workshops"
```

### Rule for security group
```
aws ec2 authorize-security-group-ingress --group-name workshop --protocol tcp --port 22 --cidr 0.0.0.0/0
```

### Create crypto keys for SSH
```
aws ec2 create-key-pair --key-name workshop --query "KeyMaterial" --output text > workshop.pem

chmod 400 workshop.pem
```

### List public DNS name of instances
```
aws ec2 describe-instances --query 'Reservations[].Instances[].PublicDnsName' --output text
```
