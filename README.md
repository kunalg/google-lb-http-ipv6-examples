# Examples for testing dual-stack changes to terraform module `terraform-google-lb-http`

These examples are copied from the main [terraform-google-lb-http](https://github.com/terraform-google-modules/terraform-google-lb-http/tree/master/examples/https-redirect) repo.

However, their source module is set to my own changes from [issue-112-dual-stack](https://github.com/kunal-g/terraform-google-lb-http/tree/issue-112-dual-stack) branch.
Idea is to exactly test the changes as requested in [this issue comment](https://github.com/terraform-google-modules/terraform-google-lb-http/pull/116#discussion_r530683051).

## Structure

There are 2 cases to be verified for IPv6 address changes - as outlined in the discussion thread:

1. new automatically allocated IPv6 address (folder: [new_ipv6](new_ipv6/https-redirect))
2. pre-created IPv6 address (either EIP in GCP or bring-your-own-address) (folder: [precreated_ipv6](precreated_ipv6/https-redirect))

I have also included exact changes I made to the `https-redirect` example in the corresponding `.diff` files.

The output from `terraform` commands is included in some `.txt` files in the respective example directories.

## How to run

To run the examples, change into the corresponding directory, edit the values in `test.tfvars` file (mainly, project id, region, zone and network_name) and run following commands:

```bash
$ terraform init
$ terraform plan -var-file=test.tfvars # to see the changes before applying them
$ terraform apply -var-file=test.tfvars # to finally apply the changes.
```

To destroy the infra created, run:

```bash
$ terraform destroy -var-file=test.tfvars
```
