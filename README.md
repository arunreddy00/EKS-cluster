    aws --version

#It should be an older version.

#Download v2:

    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

#Unzip the file:

    unzip awscliv2.zip

#See where the current AWS CLI is installed:

#which aws

#It should be /usr/bin/aws.

#Update it:

    sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update

#Check the version of AWS CLI:

    aws --version

#It should now be updated.

#Configure the CLI:

    aws configure

#For AWS Access Key ID, paste in the access key ID you copied earlier.

#For AWS Secret Access Key, paste in the secret access key you copied earlier.

#For Default region name, enter us-east-1.

#For Default output format, enter json.

#Download kubectl:

    curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.18.8/2020-09-18/bin/linux/amd64/kubectl

#Apply execute permissions to the binary:

    chmod +x ./kubectl

#Copy the binary to a directory in your path:

    mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin

#Ensure kubectl is installed:

    kubectl version --short --client

#Download eksctl:

    curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

#Move the extracted binary to /usr/bin:

    sudo mv /tmp/eksctl /usr/bin

#Get the version of eksctl:

    eksctl version

#See the options with eksctl:

    eksctl help

#In the CLI, check the cluster:

    eksctl get cluster

#Enable it to connect to our cluster:

    aws eks update-kubeconfig --name dev --region us-east-1



eksctl create cluster --name test --region ap-south-1 --nodegroup-name standard-workers --zones ap-south-1a,ap-south-1b --node-volume-size 8 --node-private-networking  --node-type t2.medium --nodes 2 --nodes-min 1 --nodes-max 4 --managed
