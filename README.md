terraform-coreos-ami
====================

*THIS MODULE IS DEPRECATED*

Please see: https://github.com/terraform-community-modules/tf_aws_coreos_ami

Terraform module to get the current set of publicly available coreos AMIs.

This module grabs all of the AMIs listed at:

    https://coreos.com/docs/running-coreos/cloud-providers/ec2/

and then looks up the one you want given the input variables.

Input variables:

  * region - E.g. eu-central-1
  * channel - stable/alpha/beta 
  * virttype - hvm/pv

Outputs:

  * ami_id

Example use:

    module "ami" {
      source = "github.com/bobtfish/terraform-coreos-ami"
      region = "eu-central-1"
      channel = "stable"
      virttype = "hvm"
    }

    resource "aws_instance" "core" {
      instances = 5
      ami = "${module.ami.ami_id}"
      instance_type = "m3.8xlarge"
    }

