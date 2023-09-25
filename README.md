# Terraform Beginner Bootcamp 2023

##Semantic Versioning

This project is going to utilize semantic versioning for its tagging. [semver.org](https://semver.org/)

The general format:

**MAJOR.MINOR.PATCH**, eg. `1.0.1`

- **MAJOR** version when you make incompatible API changes 
- **MINOR** version when you add functionality in a backward compatible manner 
- **PATCH** version when you make backward compatible bug fixes

## Install Terraform CLI

### Considerations with the Terraform CLI changes
The Terraform CLI instructions have changed due to gpg keyring changes. So we needed to refer to the latest install CLI instructions via Terraform Documentation and change the scripting for install.

[Install Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

### Refactoring into Bash Scripts

While fixing the Terraform CLI gpg depreciation issues we notice that bash scripts steps were a considerable amount more code, so we decided to create a bash script to install the Terraform CLI.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli)

- This will keep the Gitpod Task file tidy.
- This will allow us an easier time to debug and execute manually Terraform CLI install.
- This will allow portability for other projects.


https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

https://en.wikipedia.org/wiki/Shebang_(Unix)

### Linux permissions

In order to make our bash scripts executable we need to change linux permissions for the script to be executable, ie 

chmod u+x ./bin/install_terraform_cli

https://en.wikipedia.org/wiki/Chmod

https://www.gitpod.io/docs/configure/workspaces/tasks


### Working with Env Vars

We can list out all Environment Variables (env vars) using the `env` command.

We can filter specific env vars using grep eg. `env | grep AWS_`

In the terminal we can set using `export HELLO=`world`

In ther termincal we unset using `unset HELLO`

#### Printing Vars

We can print an env var using echo eg. `echo $HELLO`

### Scoping of Env Vars

When you open up a new bash terminal in VSCode it willnot be aware of env vars that you have set in another window.

If you want env vars to persist across all bash terms that you open you need to set env vars in your bash profile eg. `bash_profile`

### Persisting env vars in gitpod

We can persist env vars into gitpod by storig the in gitpod secrets storage.
```
gp env Hello= `world`
```

#Terraform BAsics

### Terraform registry

Terraform sources their providers and modueles from the Terraform registory which is located at [registry.terraform.io] (https://registry.terraform.io/)

- **Providers** is an interface to APIs that will allow you to create resources in terraform.
- **Modules** is a way to make large amount of terraform code modular, portable and sharable.

### Terraform Console

We can see a list of all the Terraofrm commands by typing `terraform`

###Terraform Init

At the start of a new terraform project we will run `terraform init`

### Terraform Plan

This will generate out a changeset about the state of our infrastructure and it tells us what will be changed. 

### Terraform Apply

This will run the Plan and above and spin up the infrastructure. Apply should prompt us to confirm the apply, in order to automatically approve an apply we can provide the auto approve flag eg `terraform apply --auto approve` 

`.terraform.lock.hcl` contains the locked versioing for the providers or modules that should be used with this project. 

The Terraform Lock File should be committed to your version control system, eg Github.

### Terraform State Files 

`.terraform.tf.state` contain information about the current state of your infrastructure.

This file **should not be committed** to your VSC.

