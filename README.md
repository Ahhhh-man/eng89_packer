# Packer

## Install Packer
```shell
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```
```shell
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
```
```shell
sudo apt-get update && sudo apt-get install packer
```
> Remark: If the above doesn't work, you may need to do them seperately.

## Setup file
```shell
sudo nano aws-ubuntu.pkr.hcl
```
```
packer {
  required_plugins {
    amazon = {
      version = ">= 0.0.2"
      source  = "github.com/hashicorp/amazon"
    }
  }
}

source "amazon-ebs" "ubuntu" {
  ami_name      = "eng89_aman_packer"
  instance_type = "t2.micro"
  region        = "eu-west-1"
  source_ami_filter {
    filters = {
      name                = "ubuntu/images/*ubuntu-xenial-16.04-amd64-server-*"
      root-device-type    = "ebs"
      virtualization-type = "hvm"
    }
    most_recent = true
    owners      = ["099720109477"]
  }
  ssh_username = "ubuntu"
}

build {
  name    = "eng89_aman_learn_packer"
  sources = [
    "source.amazon-ebs.ubuntu"
  ]
}
```

## Setup aws keys
```shell
export AWS_ACCESS_KEY_ID=YOUR_ACCESS_KEY
```
```shell
export AWS_SECRET_ACCESS_KEY=YOUR_SECRET_KEY
```

## Initialize Packer configuration
```shell
packer init .
```
```shell
packer fmt .
```
> Remark: you may need `sudo` if permission denied.
```shell
packer validate .
```
```shell
packer build aws-ubuntu.pkr.hcl
```