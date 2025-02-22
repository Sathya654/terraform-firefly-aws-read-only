# Firefly AWS ReadOnly Integration
# ![Firefly Logo](firefly.gif)

## Module contents

Firefly terraform module to integrate your aws environment to firefly.

### Prerequisites

- AWS CLI installed (version)
- The aws role running it should have permissions creation of roles in iam.

```shell script
curl --help
```

### Installation 

```hcl-terraform
provider "aws" {
    region     =  "us-east-1"
}


module "firefly-read-only" {
  source              = "https://github.com/gofireflyio/terraform-firefly-aws-read-only"
  firefly_access_key  = "YOUR_ACCESS_KEY"
  firefly_secret_key  = "YOUR_SECRET_KEY"
  role_external_id    = "YOUR_EXTERNAL_ID"
  is_prod               = false/true
}
```

### Installation with Event Driven

```hcl-terraform
provider "aws" {
    region     =  "us-east-1"
}


module "firefly-read-only" {
  source               = "https://github.com/gofireflyio/terraform-firefly-aws-read-only"
  firefly_access_key   = "YOUR_ACCESS_KEY"
  firefly_secret_key   = "YOUR_SECRET_KEY"
  role_external_id     = "YOUR_EXTERNAL_ID"
  is_prod              = false/true
  is_event_driven      = true
  event_driven_regions = ["us-east-1","us-east-2","us-west-1","us-west-2","af-south-1","ap-east-1","ap-south-1","ap-southeast-1","ap-southeast-2","ap-northeast-1","ap-northeast-2","ap-northeast-3","ca-central-1","cn-north-1","cn-northwest-1","eu-central-1","eu-west-1","eu-west-2","eu-west-3","eu-south-1","eu-north-1","me-south-1","sa-east-1"]
}
```

### Installation with Config Service

```hcl-terraform
provider "aws" {
    region     =  "us-east-1"
}


module "firefly-read-only" {
  source               = "https://github.com/gofireflyio/terraform-firefly-aws-read-only"
  firefly_access_key   = "YOUR_ACCESS_KEY"
  firefly_secret_key   = "YOUR_SECRET_KEY"
  role_external_id     = "YOUR_EXTERNAL_ID"
  is_prod              = false/true
  is_event_driven      = true
  event_driven_regions = ["us-east-1","us-east-2","us-west-1","us-west-2","af-south-1","ap-east-1","ap-south-1","ap-southeast-1","ap-southeast-2","ap-northeast-1","ap-northeast-2","ap-northeast-3","ca-central-1","cn-north-1","cn-northwest-1","eu-central-1","eu-west-1","eu-west-2","eu-west-3","eu-south-1","eu-north-1","me-south-1","sa-east-1"]
  use_config_service   = true
  config_service_regions = ["us-east-1","us-east-2","us-west-1","us-west-2","af-south-1","ap-east-1","ap-south-1","ap-southeast-1","ap-southeast-2","ap-northeast-1","ap-northeast-2","ap-northeast-3","ca-central-1","cn-north-1","cn-northwest-1","eu-central-1","eu-west-1","eu-west-2","eu-west-3","eu-south-1","eu-north-1","me-south-1","sa-east-1"]
  
}
```

### Add Event Driven to Existing Integration
In order to install event-driven for an existing firefly integration just call the module with:
```
exist_integration = true
```

### Remove Event Driven from Existing Integration
In order to remove event-driven for an existing integration just call the module with:
```
is_event_driven = false
exist_integration = true
```

### Optional
AWS credentials will be default unless adding one of the following params to the configuration:
```
profile = "YOUR_PROFILE"
```
OR
```
access_key = "YOUR_AWS_ACCESS_KEY"
secret_key = "YOUR_SECRET_KEY"
```
