# Cloning the Immersion Day repositories

1.  Clone the Mythical Mysfits Workshop Repository:
    
    In the bottom panel of your new Cloud9 IDE, you will see a terminal command line terminal open and ready to use. Run the following git command in the terminal to clone the necessary code to complete this tutorial:
    
    ```bash
    git clone https://github.com/aws-samples/amazon-ecs-mythicalmysfits-workshop.git
    ```
    
    After cloning the repository, you'll see that your project explorer now includes the files cloned.  
    In the terminal, change directory to the subdirectory for this workshop in the repo:
    
    ```bash
    cd amazon-ecs-mythicalmysfits-workshop/workshop-1
    ```
    
2.  Run some additional automated setup steps with the `setup` script:
    
    ```bash
    script/setup
    ```
    
    This script will delete some unneeded Docker images to free up disk space, populate a DynamoDB table with some seed data, upload site assets to S3, and install some Docker-related authentication mechanisms that will be discussed later. Make sure you see the "Success!" message when the script completes.
    
3.  Finally, we should configure our aws cli with our current region as default:
    
    ```bash
    export ACCOUNT_ID=$(aws sts get-caller-identity --output text --query Account)
    	export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r '.region')
    
    echo "export ACCOUNT_ID=${ACCOUNT_ID}" >> ~/.bash_profile
    echo "export AWS_REGION=${AWS_REGION}" >> ~/.bash_profile
    aws configure set default.region ${AWS_REGION}
    aws configure get default.region
    ```