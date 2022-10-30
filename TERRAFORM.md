# Terraform  ![Learn](https://img.shields.io/badge/Interview-Preparation-blueviolet?style=for-the-badge)

# Terraform Cheat Sheet

## Terraform Version

> terraform version
```
$ terraform version
Terraform v1.0.1
on darwin_amd64
```
## Terraform init (Initialize)

> terraform init
```
$ terraform init
Ask for input if necessary. If false, will error if input was required.
```

> $ terraform init -input=false

You can also change the backend details using -backend-config option. -reconfigure will reconfigure the backend, ignoring any saved configuration.

> $ terraform init -backend-config=PATH/TO/CONFIGURATION_FILE -reconfigure


## Terraform plan

The plan will check the configuration files (basically all the *.tf files in the directory) and will show you the items or changes going to made on target infrastructure or resources. Please note, this command will not actually perform the planned actions.

> $ terraform plan

You can optionally save the plan to a file, which you can then pass to the apply command to perform exactly the actions described in the plan.

> $ terraform plan -out plan.out

# Terraform get

Downloads and installs modules needed for the configuration given by PATH. get recursively downloads all modules needed, such as modules imported by modules imported by the root and so on. 

Module installation also happens automatically by default as part of the “terraform init” command, so you should rarely need to run this command separately.

> $ terraform get

You can update the already downloaded modules using -update=true option.

> $ terraform get -update=true

## Terraform apply

> terraform apply

apply will do the actual operation on the infrastructure resources. apply will show the plan and actions in detail.

> $ terraform apply
apply will ask for your confirmation to proceed with changes. You can use -auto-approve for auto-confirmation.

> $ terraform apply -auto-approve
You can pass different variables or variable files.

```
$ terraform plan -var="instancetype=t2.small"
$ terraform apply
$ terraform plan -var-file="custom.tfvars
$ terraform apply

```

You can use -target option to target specific resources, modules, or collections of resources.

> $ terraform apply -target="aws_s3_bucket_object.objects"

## Terraform destroy

> terraform destroy

Warning: destroy will delete all resource but with confirmation.

> $ terraform destroy

You can create a deletion plan as below.

> $ terraform plan –destroy

Use the -target to destroy a specific resource.

> $ terraform destroy -target="aws_s3_bucket_object.objects"

Also note, you can comment out the resource, then terraform will detect it as not part of config and will remove when you do plan or apply.

## Terraform Refresh

> terraform refresh

You can update the terraform state file with metadata that matches the physical resources they are tracking.

> $ terraform refresh

## Terraform show

> terraform show

Show the terraform state information in a human readable format. You can also use it for displaying information from plan file.

> $ terraform show

## Terraform validate

> terraform validate

You can check the syntax and validate the configuration using validate subcommand.

```
> $ terraform validate
Success! The configuration is valid.
```
## Terraform providers

> terraform providers

You can see the providers in use by the modules and configurations in your Terraform files.

> $ terraform providers

Providers required by configuration:
.
└── provider[registry.terraform.io/hashicorp/aws]

# Terraform State

> terraform state

terraform state has multiple subcommands to manage the terraform state. You can move, rm (delete), list or show the resource state.
```
Subcommands:
    list                List resources in the state
    mv                  Move an item in the state
    pull                Pull current state and output to stdout
    push                Update remote state from a local state file
    replace-provider    Replace provider in the state
    rm                  Remove instances from the state
    show                Show a resource in the state
 ```

> Example usages

1.  List state

```
$ terraform state list
aws_iam_user.lb
aws_instance.myec2
```

2.  Show resource

```
$ terraform state show aws_instance.myec2

```

3. Push terraform state to remote backend

```
$ tarraform state push
```
4. Pull the remote terraform state to a local copy

```
$ terraform state pull > terraform.tfstate
```
5.  Update and tell terraform that packet_device.worker has been renamed to packet_device.helper

```
$ terraform state mv packet_device.worker packet_device.helper

```
6. Move the resource block into the child module configuration.
```
$ terraform state mv packet_device.worker module.worker.packet_device.worker
```
7. Remove the resource from state but it will not remove the resource from cloud/provider.

```
$ terraform state rm aws_instance.myec2
```
8. Remove the resource from state but it will not remove the resource from cloud/provider. But next time when you run terraform plan or apply, Terraform will recreate the instance as again as the resource definition is still there.

```
$ terraform state rm aws_instance.myec2
Removed aws_instance.myec2
Successfully removed 1 resource instance(s).
```
## Terraform Graph

> terraform graph

graph will generate the visual graph of your infrastructure based on Terraform configuration files.

Outputs the visual execution graph of Terraform resources according to either the current configuration or an execution plan.

> $ terraform graph
The output of terraform graph will be in DOT format and you can use tools like dot to generate image files from dot files.

Prerequisites
```
Ubuntu OS
sudo apt-get install graphviz
# or 
RHEL OS
sudo yum install graphviz
```

> $ terraform graph | dot –Tpng > graph.png

## Terraform fmt

> terraform fmt
> 
Rewrites all Terraform configuration files to a canonical format with appropriate indentation and styling. (JSON files (.tf.json or .tfvars.json) are not modified.)

$ terraform fmt

## Terraform taint

> terraform taint

You can manually mark a terraform managed resource as tainted and forcing it to be destroyed and recreated on the next apply. terraform taint command will make modification in the tfstate file and recreate action will happen in next apply. Please note, terraform taint command will not modify the .tf file or the infrastructure.

> $ terraform taint aws_instance.myec2

## Terraform import

> terraform import

You can import your existing infrastructure into Terraform and manage using Terraform.

1. Importing VMWare VM to terraform

$ terraform import vsphere_virtual_machine.vm /DC1/vm/DEV/DEV2

Read detailed guide: How to Import Existing VMWare VM’s into Terraform

## Terraform Workspace

> terraform workspaces

Terraform Workspaces will help to manage same terraform configurations for different environments (eg: dev, staging, production) in the same project directory.

1.  Check the workspace

```
$ terraform workspace show
default
```
2. Create new workspace

```
$ terraform workspace new dev
Created and switched to workspace "dev"!
```
3.  List all workspaces
```
$ terraform workspace list
  default
* dev
```
4. Switch to a specific workspace
```
$ terraform workspace select dev
Switched to workspace "dev".
```
Terraform will create separate terraform.tfstate files in terraform.tfstate.d/WORKSPACE_NAME/ directories in the project directory.

```
$ tree terraform.tfstate.d/
terraform.tfstate.d/
├── dev
│   └── terraform.tfstate
├── prod
└── stage
    └── terraform.tfstate


3 directories, 2 files
```

You can use ${terraform.workspace} interpolation to dynamically use the workspace name inside your terraform configuration (*.tf). 

Eg: you can use it for selecting instance type from an array based on workspace.

1. Resources 
```
resource "aws_instance" "myec2" {
  ami           = "ami-0cd31be676780afa7"
  instance_type = lookup(var.instance_type,terraform.workspace)

}
```
2. Variables 

```
variable "instance_type" {
 type = map

 default = {
   default = "t2.nano"
   stage = "t2.nano"
   dev = "t2.micro"
   prod = "t2.large"
 }
}
```
Or you can use this ${terraform.workspace} for tagging the instance.
3. Tags
```
resource "aws_instance" "example" {
  # ... other arguments
  tags = {
    Name = "web-${terraform.workspace}"
  }
}
```

Refer Terraform Workspaces documentation for more details.

## Plugins 

Windows
```
Terraform Default Plugin Directories
Windows: %APPDATA%\terraform.d\plugins
```
All other systems
```
~/.terraform.d/plugins
Terraform Variable Assignment
```

## Terraform varaibles

You can pass variables to Terraform in different methods.

1. Environment variables – with a prefix TF_VAR_

$ export TF_VAR_instance_type=t2.micro

2. Command Line Flags

$ terraform plan -var="instancetype=t2.small"

3. From a variable file – use terraform.tfvars – terraform will load all variables from this file. If different var files to be used then,

$ terraform plan -var-file="custom.tfvars

4. Variable Defaults – can keep variable default in another .tf file.

$ cat variables.tf
```
variable "my_ip" {
default = "10.1.10.10/32"
}
```
if no value mentioned, then default value will be used.
if default value not defined, then terraform will ask for variable when you do apply or plan operation.

## Terraform Meta-Arguments

Terraform Meta-Arguments helps us in achieving certain requirements within the resource block. lets see all available meta arguments in Terraform 1 by 1 with examples.

> There are 5 Meta-Arguments in Terraform which are as follows

Meta-Arguments

```
depends_on
count
for_each
provider
depends_on
lifecycle
```

Terraform has a feature of identifying resource dependency. 

This means that Terraform internally knows the sequence in which the dependent resources needs to be created whereas the independent resources are created parallelly.

But in some scenarios, some dependencies are there that cannot be automatically inferred by Terraform. 

In these scenarios, a resource relies on some other resource’s behaviour but it doesn’t access any of the resource’s data in arguments.

For those dependencies, we’ll use depends_on meta-argument to explicitly define the dependency.

### depends_on 

depends_on meta-argument must be a list of references to other resources in the same calling resource.

This argument is specified in resources as well as in modules (Terraform version 0.13+).

```
resource "aws_iam_role" "role" {
  name = "demo-role"
  assume_role_policy = "..."
}
```
```
resource "aws_iam_instance_profile" "instance-profile" {
  # Terraform can infer automatically that the role must be created first.
  role = aws_iam_role.role.name
}
```
```
resource "aws_iam_role_policy" "policy" {
  name   = "demo-policy"
  role   = aws_iam_role.role.name
  policy = jsonencode({
    "Statement" = [{
      "Action" = "s3:*",
      "Effect" = "Allow",
    }],
  })
}
```
```
resource "aws_instance" "ec2" {
  ami           = "ami-a1b2c3d4"
  instance_type = "t2.micro"
  
  # Terraform can infer from this that the instance profile must
  # be created before the EC2 instance.
  iam_instance_profile = aws_iam_instance_profile.instance-profile

  # However, if software running in this EC2 instance needs access
  # to the S3 API in order to boot properly, there is also a "hidden"
  # dependency on the aws_iam_role_policy that Terraform cannot
  # automatically infer, so it must be declared explicitly:
  depends_on = [
    aws_iam_role_policy.policy
  ]
}
```

### count

In Terraform, a resource block actually configures only one infrastructure object by default. 

If we want multiple resources with same configurations, we can define the count meta-argument. 

This will reduce the overhead of duplicating the resource block that number of times.

*count* require a whole number and will then create that resource that number of times. 

To identify each of them, we use the *count.index* which is the index number corresponds to each resource. 

The index ranges from 0 to count-1.

This argument is specified in resources as well as in modules (Terraform version 0.13+). 

Also, count meta-argument cannot be used with for_each.

```
resource "aws_instance" "server" {
  # create four similar EC2 instances
  count = 4
  ami           = "ami-a1b2c3d4"
  instance_type = "t2.micro"
  tags = {
    # Usage of count.index in providing a distinct name for every Instance
    Name = "Server ${count.index}"
  }
}
```
```
output "instance_id" {
  # Select all instance id using * in place of index value
  value = aws_instance.server[*].id
}
```
### for_each

As specified in the count meta-argument, that the default behaviour of a resource is to create a single infrastructure object which can be overridden by using count, but there is one more flexible way of doing the same which is by using for_each meta argument.

The for_each meta argument accepts a map or set of strings. 

Terraform will create one instance of that resource for each member of that map or set. To identify each member of the for_each block, we have 2 objects

```
each.key: The map key or set member corresponding to each member.
each.value: The map value corresponding to each member.
```
This argument is specified in resources (Terraform version 0.12.6) as well as in modules (Terraform version 0.13+)

1. Example for map
```
resource "azurerm_resource_group" "rg" {
  for_each = {
    group_A = "eastus"
    group_B = "westus2"
  }
  name     = each.key
  location = each.value
}
```
2. Example for set
```
resource "aws_iam_user" "accounts" {
  for_each = toset( ["Developer", "Tester", "Administrator", "Cloud-Architect"] )
  name     = each.key
}
```

### provider

provider meta-argument specifies which provider to be used for a resource. 

This is useful when you are using multiple providers which is usually used when you are creating multi-region resources. 

For differentiating those providers, you use an alias field.

The resource then reference the same alias field of the provider as provider.alias to tell which one to use.

1. Default Provider
```
provider "google" {
  region = "us-central1"
}
```
2. Another Provider
```
provider "google" {
  alias  = "europe"
  region = "europe-west1"
}
```

3. Referencing the other provider
```
resource "google_compute_instance" "example" {
  provider = google.europe
}
```

### lifecycle

The lifecycle meta-argument defines the lifecycle for the resource. As per the resource behaviour, Terraform can do the following:

1. create a resource
2. destroy a resource
3. updated resource in place
4. update resource by deleting existing and create new

lifecycle is a nested block under resource that is used to customise that behaviour. 

Here are the following customisation that are available under lifecycle block

#### create_before_destroy: (Type: Bool)

For resource, where Terraform cannot do an in place updation due to API limitation, its default behaviour is to destroy the resource first and then re create it. 

This can be changed by using this argument. It will first create the updated resource and then delete the old one.

#### prevent_destroy: (Type: Bool)

This will prevent the resource from destroying. It is a useful measure where we want to prevent a resource against accidental replacement such as database instances.

### ignore_changes: (Type: List(Attribute Names))

By default, If Terraform detects any difference in the current state, it plans to update the remote object to match configuration. 

The ignore_changes feature is intended to be used when a resource is created with references to data that may change in the future, but should not affect said resource after its creation. 

It expects a list or map of values, whose updation will not recreate the resource. If we want all attributes to be passed here, we can simply use all.

1. Ignore tag changes and won't recreate this resource if tags are updated
```
resource "aws_instance" "example" {
  lifecycle {
    ignore_changes = [
      tags,
    ]
  }
}
```

## Data Sources

_Data sources_ allow Terraform to use information defined outside of Terraform,
defined by another separate Terraform configuration, or modified by functions.

#### Using Data Sources

A data source is accessed via a special kind of resource known as a _data resource_, declared using a `data` block:

```hcl
data "aws_ami" "example" {
  most_recent = true

  owners = ["self"]
  tags = {
    Name   = "app-server"
    Tested = "true"
  }
}
```

A `data` block requests that Terraform read from a given data source ("aws_ami") and export the result under the given local name ("example"). 

The name is used to refer to this resource from elsewhere in the same Terraform module, but has no significance outside of the scope of a module.

The data source and name together serve as an identifier for a given resource and so must be unique within a module.

#### Data Source Arguments

Each data resource is associated with a single data source, which determines the kind of object (or objects) it reads and what query constraint arguments are available.

Each data source in turn belongs to a [provider](/language/providers), which is a plugin for Terraform that offers a collection of resource types and data sources that most often belong to a single cloud or on-premises infrastructure platform.

Most of the items within the body of a `data` block are defined by and specific to the selected data source, and these arguments can make full use of [expressions](/language/expressions) and other dynamic Terraform language features.

However, there are some "meta-arguments" that are defined by Terraform itself and apply across all data sources. These arguments often have additional restrictions on what language features can be used with them, and are described in more detail in the following sections.

#### Data Resource Behavior

Terraform reads data resources during the planning phase when possible, but announces in the plan when it must defer reading resources until the apply phase to preserve the order of operations. 

Terraform defers reading data resources in the following situations:

* At least one of the given arguments is a managed resource attribute or other value that Terraform cannot predict until the apply step.
* The data resource depends directly on a managed resource that itself has planned changes in the current plan.
* The data resource has [custom conditions](#custom-condition-checks) and it depends directly or indirectly on a managed resource that itself has planned changes in the current plan.

#### Local-only Data Sources

While many data sources correspond to an infrastructure object type that is accessed via a remote network API, some specialized data sources operate only within Terraform itself, calculating some results and exposing them for use elsewhere.

For example, local-only data sources exist for
[rendering templates](https://registry.terraform.io/providers/hashicorp/template/latest/docs/data-sources/file),
[reading local files](https://registry.terraform.io/providers/hashicorp/local/latest/docs/data-sources/file), and
[rendering AWS IAM policies](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document).

The behavior of local-only data sources is the same as all other data sources, but their result data exists only temporarily during a Terraform operation, and is re-calculated each time a new plan is created.

#### Data Resource Dependencies

Data resources have the same dependency resolution behavior [as defined for managed resources](/language/resources/behavior#resource-dependencies).

Setting the `depends_on` meta-argument within `data` blocks defers reading of the data source until after all changes to the dependencies have been applied.

In order to ensure that data sources are accessing the most up to date information possible in a wide variety of use cases, arguments directly referencing managed resources are treated the same as if the resource was listed in `depends_on`. 

This behavior can be avoided when desired by indirectly referencing the managed resource values through a `local` value, unless the data resource itself has [custom conditions](#custom-condition-checks).

~> **NOTE:** **In Terraform 0.12 and earlier**, due to the data resource behavior of deferring the read until the apply phase when depending on values that are not yet known, using `depends_on` with `data` resources will force the read to always be deferred to the apply phase, and therefore a configuration that uses `depends_on` with a `data` resource can never converge. Due to this behavior, we do not recommend using `depends_on` with data resources.

#### Custom Condition Checks

You can use `precondition` and `postcondition` blocks to specify assumptions and guarantees about how the data source operates. The following examples creates a postcondition that checks whether the AMI has the correct tags.

``` hcl
data "aws_ami" "example" {
  id = var.aws_ami_id

  lifecycle {
    # The AMI ID must refer to an existing AMI that has the tag "nomad-server".
    postcondition {
      condition     = self.tags["Component"] == "nomad-server"
      error_message = "tags[\"Component\"] must be \"nomad-server\"."
    }
  }
}
```

Custom conditions can help capture assumptions, helping future maintainers understand the configuration design and intent. They also return useful information about errors earlier and in context, helping consumers more easily diagnose issues in their configurations.

Refer to [Custom Condition Checks](/language/expressions/custom-conditions#preconditions-and-postconditions) for more details.


#### Multiple Resource Instances

Data resources support [`count`](/language/meta-arguments/count) and [`for_each`](/language/meta-arguments/for_each) meta-arguments as defined for managed resources, with the same syntax and behavior.

As with managed resources, when `count` or `for_each` is present it is important to distinguish the resource itself from the multiple resource _instances_ it creates. 

Each instance will separately read from its data source with its own variant of the constraint arguments, producing an indexed result.

#### Selecting a Non-default Provider Configuration

Data resources support [the `provider` meta-argument](/language/meta-arguments/resource-provider) as defined for managed resources, with the same syntax and behavior.

#### Lifecycle Customizations

Data resources do not currently have any customization settings available for their lifecycle, but the `lifecycle` nested block is reserved in case any are added in future versions.

1. Example

A data source configuration looks like the following:

```hcl
# Find the latest available AMI that is tagged with Component = web
data "aws_ami" "web" {
  filter {
    name   = "state"
    values = ["available"]
  }

  filter {
    name   = "tag:Component"
    values = ["web"]
  }

  most_recent = true
}
```

## Description

The `data` block creates a data instance of the given _type_ (first block label) and _name_ (second block label). 
The combination of the type and name must be unique.

Within the block (the `{ }`) is configuration for the data instance. The configuration is dependent on the type; as with [resources](/language/resources), each provider on the [Terraform Registry](https://registry.terraform.io/browse/providers) has its own documentation for configuring and using the data types it provides.

Each data instance will export one or more attributes, which can be used in other resources as reference expressions of the form `data.<TYPE>.<NAME>.<ATTRIBUTE>`. 

For example:

```hcl
resource "aws_instance" "web" {
  ami           = data.aws_ami.web.id
  instance_type = "t1.micro"
}
```

#### Meta-Arguments

As data sources are essentially a read only subset of resources, they also support the same [meta-arguments](/language/resources/syntax#meta-arguments) of resources
with the exception of the [`lifecycle` configuration block](/language/meta-arguments/lifecycle).

##### Non-Default Provider Configurations

Similarly to [resources](/language/resources), when a module has multiple configurations for the same provider you can specify which configuration to use with the `provider` meta-argument:

```hcl
data "aws_ami" "web" {
  provider = aws.west

  # ...
}
```

