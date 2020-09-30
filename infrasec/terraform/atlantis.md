# [Terraform](README.md) / Atlantis

I're beginning to use Atlantis throughout projects at Martin's experience. There's more to come, but for now here are some helpful things to know.

## Tips and gotchas

* When resetting a gitlab personal token in Parameter Store, you will have to redeploy the Atlantis instance. Otherwise, the new credential will not be updated in the instance.
* I use [this](https://gitlab.com/terraform-aws-modules/terraform-aws-atlantis) Atlantis terraform module to spin up my instances. If you do not set the `atlantis_image` variable, you'll find `atlantis:latest` is used by default. This default is not recognized as updated when a new "latest" is released due to the word remaining unchanged. Therefore, I recommend you pass in a numbered version of the Atlantis docker image to the `atlantis_image` var.

## Links and other reading

