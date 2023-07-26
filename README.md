# Kubernetes Workshop Image

Packer code to build an AWS AMI with Minikube for workshops on how to monitor Kubernetes and containerized applications with the Elastic.

## Packer Setup for Strigo

The workshop will be hosted on Strigo. 

### Strigo

> Note: You need Packer v1.9.2+ to build this image

To build an AWS AMI for [Strigo](https://strigo.io), use [Packer](https://packer.io). Using the [Ansible Local Provisioner](https://packer.io/docs/provisioners/ansible-local.html) you only need to have Packer installed locally (no Ansible). Build the AMI with `packer build packer.json` and set up the training class on Strigo with the generated AMI and the user `ubuntu`.

If things are failing for some reason: Run `packer build -debug packer.json`, which will keep the instance running and save the SSH key in the current directory. Connect to it with `ssh -i ec2_amazon-ebs.pem ubuntu@ec2-X-X-X-X.eu-central-1.compute.amazonaws.com`; open ports as needed in the AWS Console since the instance will only open TCP/22 by default.

### Configuration

The base image is [Ubuntu 20.04 LTS, amd64 focal image](https://eu-west-1.console.aws.amazon.com/ec2/home?region=eu-west-1#ImageDetails:imageId=ami-0f98d0975afb795c7) and is configured using the `configure.yml` Ansible script.

The AMI image is shared by default with the Strigo account as specified by [their documentation](http://help.strigo.io/en/articles/1941452-use-custom-lab-images).
