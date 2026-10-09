Aws Terraform

Terraform is an open-source infrastructure as code (IaC) tool. 

What is IaC ?
It enables you to define, provision, and manage infrastructure across multiple cloud providers using a declarative configuration language. 

-=> It supports multi-cloud environments, allowing consistent and efficient infrastructure management. 

Terraform config 
- It uses .tf extension. 
- Format is HCL (Hashicorp config language) 
- Declarative language. 

-> Terraform supports JSON format also and the Hashicorp config language is very short compared to the JSON format language. 

- Terraform init
- Terraform plan 
- Terraform apply / destroy. 

BENEFITS :-
Consistency : Define infrastructure in code
Automation : Reduce manual work
Repeatable : replicate environments easily


State Management : 
The state file terraform.tfstate maintains a detailed record of the current state of managed resources. 
This state file can be stored locally or remotely, with remote storage options enabling collaboration by sharing the state across teams and environments. 


Multiple resources using : 
- count 
- for_each

Terraform modules :
Modules are containers for  multiple resources that are used together.
The module consists of a collection of .tf and / or .tf.json files kept together in a directory. 
Modules are the main way to package and reuse resource configurations with Terraform. 


Terraform Cloud is a managed service provided by Hashicorp that facilitates collaboration on Terraform configurations
=> providing features like:
- remote state management
- version control system (VCS) integration
- automated runs
- secure variable management

## Remember Terraform as a planner with a state file

Terraform configuration describes the desired infrastructure; `plan` compares that description with saved state and provider-observed resources; `apply` performs the approved changes. `terraform.tfstate` is not just a cache: it can contain resource identifiers and sensitive values, so protect it and use a secure shared backend with locking for team work.

Use modules to package repeatable designs, variables for controlled inputs, and outputs to expose useful results. Run format/validation and review the full plan before applying. Do not casually edit state or run destroy against a shared environment.

**Recall check:** A plan proposes replacing a database. What is the right next move? Stop, inspect why replacement is planned, confirm backups/retention and dependencies, and only then decide whether to apply.

Terraform is not an AWS service: these notes explain it as an IaC tool that can manage AWS and other providers.





