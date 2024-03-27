# Jenkins Automation for Nice Website

### Usage
- Add new Item Pipeline
- Add parameters via "This project is parameterized" 
  * add `ip`
  * add `repository`
- Under Pipeline choose pipeline script from scm.
- Enter Repository URL and proper branch.

### Requirements
#### Plugins
  - Credentials
  - Build Parameters
  - Git Plugin


#### Parameters
  * `ip`: this is the IP address of your ec2 Instance.
  * `repository`:  this is the source code repository for the website.

