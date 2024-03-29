# terraform-hcl-count
_this doc is used for training purposes, do not use in production_

# count 
- generate same resource for _count_ times
- repeat something
- count official documentation [LINK](https://www.terraform.io/docs/language/meta-arguments/count.html)

Use count in a resource to create the same resource _count_ times
```
resource "random_pet" "cat" {
    length = 1
    # count is three, means 3 strings will be generated
    count = 3
}
```


# Example
How to generate 3 random strings
```
git clone https://github.com/ionhashicorp/terraform-hcl-count.git
```

```
cd terraform-hcl-count
```

```
$ tree
.
├── LICENSE
├── README.md
├── main.tf           # <--- This file contains the HCL configuration
└── terraform.tfstate
```
[LINK](https://github.com/ionhashicorp/terraform-hcl-count/blob/main/main.tf) to main.tf

Process of creating the random strings:
```
terraform init
```
```
terraform plan
```
```
terraform apply -auto-approve
```


# Sample output

```
$terraform init

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/random...
- Installing hashicorp/random v3.1.0...
- Installed hashicorp/random v3.1.0 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
$ 
```
```
$terraform plan

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # random_pet.cat[0] will be created
  + resource "random_pet" "cat" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

  # random_pet.cat[1] will be created
  + resource "random_pet" "cat" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

  # random_pet.cat[2] will be created
  + resource "random_pet" "cat" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

Plan: 3 to add, 0 to change, 0 to destroy.

───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform apply"
now.
$
```

```
$ terraform apply -auto-approve

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # random_pet.cat[0] will be created
  + resource "random_pet" "cat" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

  # random_pet.cat[1] will be created
  + resource "random_pet" "cat" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

  # random_pet.cat[2] will be created
  + resource "random_pet" "cat" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

Plan: 3 to add, 0 to change, 0 to destroy.
random_pet.cat[1]: Creating...
random_pet.cat[0]: Creating...
random_pet.cat[2]: Creating...
random_pet.cat[2]: Creation complete after 0s [id=stud]
random_pet.cat[1]: Creation complete after 0s [id=hedgehog]
random_pet.cat[0]: Creation complete after 0s [id=rat]

Apply complete! Resources: 3 added, 0 changed, 0 destroyed.
$
```
