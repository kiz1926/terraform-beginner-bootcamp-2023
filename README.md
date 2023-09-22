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
