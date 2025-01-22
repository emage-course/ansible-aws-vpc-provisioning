# ansible-aws-vpc
# AWS EC2 Infrastructure and Web Server Deployment using Ansible

Manipulating EC2 Instances with Ansible
EC2 is at the heart of AWS as the primary compute resource on the platform. Ansible provides several modules that allow us to interact with EC2 instances. Being able to provision and manipulate EC2 instances within Ansible allows for infrastructure automation to be built into a deployment strategy. This exercise will allow students to explore the EC2 functionality in Ansible.

This repository provides Ansible playbooks to set up AWS infrastructure and deploy a web server with an application. The project is divided into modular playbooks for better maintainability and clarity.

## Prerequisites

1. Install Ansible on your local machine. Refer to the [Ansible Installation Guide](https://docs.ansible.com/ansible/latest/installation_guide/index.html) for details.

2. Install the `amazon.aws` Ansible collection:
```sh
ansible-galaxy collection install amazon.aws
pip install --upgrade ansible
```

3. Configure AWS credentials and ensure they are accessible (e.g., via group_vars/aws_keys.yml or environment variables).
   
4. Ensure you have SSH access to the target EC2 instance with the correct key pair.

**File Structure**

* infrastructure_setup.yml: Sets up the AWS infrastructure (VPC, Subnet, Security Group, EC2 instance, etc.).
* webserver_installation.yml: Installs the Apache web server and deploys the application on the EC2 instance.
* deploy.yml: Parent playbook to execute the setup in sequence.

**How to Run**

1. Save each playbook into separate
   files:
   * deploy_all.yml (parent playbook)
  
2. Validate the playbooks for

### syntax:
```sh
ansible-playbook deploy_all.yml --syntax-check
```

3. Run the parent playbook to deploy the infrastructure and application:

```sh
ansible-playbook deploy_all.yml
```

**Notes**

* Replace any placeholder variables (e.g., AWS credentials, region, key pair name) with your actual values in the group_vars files or the playbooks themselves.
* Ensure you have the necessary IAM permissions to manage AWS resources.
* The deploy.yml playbook will automatically handle dependencies and execute the tasks in the correct order.

**Troubleshooting**

If you encounter any issues, verify the following:

* Ansible is installed and correctly configured.
* AWS credentials have sufficient permissions.
* The amazon.aws collection is installed:

```sh
ansible-galaxy collection list | grep amazon.aws

export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
export AWS_REGION="your_region"


brew install python
pip3 install virtualenv
python3 -m venv devops-ansible
source devops-ansible/bin/activate
```
