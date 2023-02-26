# Monitor Kubernetes Workshop

Hands-on workshop on how to monitor Kubernetes and containerized applications with the Elastic.

## Packer Setup for Strigo

The workshop will be hosted on Strigo. 

### Strigo

To build an AWS AMI for [Strigo](https://strigo.io), use [Packer](https://packer.io). Using the [Ansible Local Provisioner](https://packer.io/docs/provisioners/ansible-local.html) you only need to have Packer installed locally (no Ansible). Build the AMI with `packer build packer.json` and set up the training class on Strigo with the generated AMI and the user `ubuntu`.

If things are failing for some reason: Run `packer build -debug packer.json`, which will keep the instance running and save the SSH key in the current directory. Connect to it with `ssh -i ec2_amazon-ebs.pem ubuntu@ec2-X-X-X-X.eu-central-1.compute.amazonaws.com`; open ports as needed in the AWS Console since the instance will only open TCP/22 by default.

### Configuration

The base image is [Canonical, Ubuntu, 18.04 LTS, amd64 bionic image build on 2023-02-15](https://eu-west-1.console.aws.amazon.com/ec2/home?region=eu-west-1#ImageDetails:imageId=ami-027ceacf6a9f484c3) and is configured using the `configure.yml` Ansible script.

The AMI image is shared by default with the Strigo account as specified by [their documentation](http://help.strigo.io/en/articles/1941452-use-custom-lab-images).
