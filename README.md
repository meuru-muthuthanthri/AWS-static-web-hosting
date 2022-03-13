# AWS-static-web-hosting

### Set up static web hosting ###

* Set up the Certificate

    ```yml
    aws cloudformation create-stack \
    --stack-name mySiteCertificate \
    --region us-east-1 \
    --parameters ParameterKey=DomainName,ParameterValue=site.example.com ParameterKey=HostedZoneId,ParameterValue=12345 \
    --template-body file://certificate.yml
    ```

* Set up the static web hosting

    ```yml
    aws cloudformation create-stack \
    --stack-name staticHostingStack \
    --parameters ParameterKey=DomainName,ParameterValue=site.example.com ParameterKey=MainDomainName,ParameterValue=example.com ParameterKey=certificateARN,ParameterValue=<ARN> \
    --template-body file://staticHosting.yml
    ```
