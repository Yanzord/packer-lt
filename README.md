# Packer Lightning Talk (LT)

This repo has the code for a packer LT. Slides are [here](https://docs.google.com/presentation/d/1c83ruz2rpCY1r6OWEOSfKOb-w5OIvWNYuMemJHBmwgE/edit?usp=sharing). 

It contains a template file to create a docker image with nodejs and a simple Hello World application and another template file to create a Ubuntu AMI with OpenJDK 8 installed in AWS.

The key objective is to show how packer easily solves the problem of having multiples types of images for multiples types of platforms, each with its particularity and complexity.

## Setup

Download and install [Packer](https://learn.hashicorp.com/tutorials/packer/getting-started-install).

For _template_dockerhub.json_ you'll need a dockerhub account and a dockerhub repository created, change the repository attribute inside _template_dockerhub.json_ to your repository.

For _template_aws.json_ you'll need an AWS account.

## Execution

Set the ```DOCKER_HUB_USERNAME``` and ```DOCKER_HUB_PASSWORD``` environment variables and run

```
$ packer build \
    -var "docker_hub_username=$DOCKER_HUB_USERNAME" \
    -var "docker_hub_password=$DOCKER_HUB_PASSWORD" \
    template_dockerhub.json
```

Set the ```AWS_ACCESS_KEY_ID``` and ```AWS_SECRET_ACCESS_KEY``` environment variables and run

```
$ packer build \
    -var "aws_key_id=$AWS_ACCESS_KEY_ID" \
    -var "aws_secret_access_key=$AWS_SECRET_ACCESS_KEY" \
    template_aws.json
```