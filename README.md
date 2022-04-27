# OpenVPN Ephemeral Travis CI Template

## Overview
This repo provides an example template that supports a Travis CI pipeline building and destroying an OpenVPN EC2 server on demand. This template makes use of the [paulmarsicloud/openvpn-ephemeral/aws](https://registry.terraform.io/modules/paulmarsicloud/openvpn-ephemeral/aws/latest) Terraform Module.

Note: last testing of this template was unsuccessful with Travis CI, so your mileage may vary.

## Pre-requisites
In order to utilize this template repo, you will need an AWS Account with an IAM user that has programmatic access, and OpenVPN Connect on your local machine. You will also need to create a private S3 bucket for Travis CI to upload the Terraform state and OpenVPN profile files.

## Environment Variables
In order to use this template, simply clone/fork this repo, authorize Travis CI and update the following
1. The `TF_VAR_public_ip=<REPLACE ME> TF_VAR_region=<REPLACE ME>` variables in the [.travis.yml](/.travis.yml) file with your local public IP address (e.g. `curl 4.ipaddr.io`) and region you wish to run the OpenVPN service from.
2. The `<private S3 bucket name>` value with the private S3 bucket that will hold the Terraform state and OpenVPN profile files
2. In Travis CI go to your repo > More options > Settings > Environment Variables > Add environment variables for your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY_ID`
