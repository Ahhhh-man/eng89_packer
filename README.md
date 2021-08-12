# Packer

## Install Packer
```terminal
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```
```terminal
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
```
```terminal
sudo apt-get update && sudo apt-get install packer
```
> Remark: If the above doesn't work, you may need to do them seperately.