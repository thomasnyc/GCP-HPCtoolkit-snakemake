#HPC Toolkit Slurm Snakemake demo

This repo demos the setup of Slurm cluster using HPC Toolkit and run the Sample Snakemake tutorial.

Snakemake tutorial
[https://snakemake.readthedocs.io/en/stable/tutorial/basics.html?highlight=scripts%2Fplot-quals.py#]

HPC toolkit
[https://github.com/GoogleCloudPlatform/hpc-toolkit]

##Setup of the HPC Toolkit

- Step 1: Install tools - gcc, terraform, packer
For Debian:
```sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install terraform
sudo apt install build-essential
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install packer
```

For Centos:
```
sudo yum -y install wget
sudo yum install -y yum-utils go
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo yum -y install terraform
curl -O https://dl.google.com/go/go1.18.2.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.18.2.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo yum -y install packer
wget https://github.com/cli/cli/releases/download/v2.11.3/gh_2.11.3_linux_amd64.rpm
sudo yum -y install gh_2.11.3_linux_amd64.rpm
```

- 2. Clone the HPC toolkit code from Github

```gh repo clone GoogleCloudPlatform/hpc-toolkit
```

- 3. Copy the yaml file in this repo into the hpc-toolkit directory

- 4. Run the blueprint creation process:

```./ghpc create demo-snakemake-tutorial.yaml
```

- 5. Run the Terraform init and apply:

This is the sample of terraform commands which shall be provided as part of the blueprint creation process. 
```  terraform -chdir=sm-tutor-demo/primary init
  terraform -chdir=sm-tutor-demo/primary validate
  terraform -chdir=sm-tutor-demo/primary apply
```

Copyright 2022 Google. This software is provided as-is, without warranty or representation for any use or purpose. Your use of it is subject to your agreement with Google. 
