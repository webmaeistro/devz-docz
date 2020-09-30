# [InfraSec](README.md) / Project Teardown Guide

When a project reaches the end of its lifetime and the client doesn't
want to continue it, I need to teardown all the infrastructure I've
created for the project -- sometimes on relatively short notice. This
guide is intended to provide a step-by-step procedure for tearing down
infrastructure I've created for a project and highlight any potential
sources of trouble.

<!-- toc -->

* [Terraform and AWS](#terraform-and-aws)
* [SSL certificates](#ssl-certificates)
* [CircleCI](#circleci)
* [gitlab](#gitlab)
* [1Password](#1password)

<!-- Regenerate with "pre-commit run -a markdown-toc" -->

<!-- tocstop -->

## Terraform and AWS

Your first task should be shutting down all the AWS infrastructure
you've built for your project. When you do this, you'll need to proceed
in basically the reverse order you created all the resources. Here are
some guidelines when tearing down Terraform namespaces:

* Tear down accounts that don't hold resources for organization-wide
  purposes first -- leave your infra, id, and org-root accounts for last.
* If you were using Atlantis to maintain a namespace, and you have this
  component in your `terraform.tf` `backend` configuration:

  ```text
  role_arn       = "arn:aws:iam::123456789000:role/atlantis"
  ```

  Then before you begin tearing down that namespace, you need to remove
  this line, run a `terraform apply`, and then do your `terraform destroy`.
  If you do not do this, then your `destroy` will fail and the state will
  become corrupted because you will destroy the role Terraform is using
  to perform the destroy. Doing the `terraform apply` allows Terraform to
  cleanly change the backend configuration first.
* Similarly, when tearing down the `admin-global` namespace, you should
  change your `.aws/config` profile for the account you're destroying to
  use the `OrganizationAccountAccessRole` with the `org-root` account as
  the `source_profile`. This prevents you from having the same problem
  when your `admin` role is destroyed.
* Do not destroy resources in the `admin-global` namespace until all
  other namespaces for the account except the `bootstrap` namespace have
  been torn down. Don't destroy `bootstrap` until `admin-global` has been
  torn down.
* When you are ready to tear down the `org-root` account, create an IAM
  user *without* Terraform, give it credentials and attach an MFA, and
  change your `org-root` profile to use those credentials. This will allow
  you to cleanly tear down the entire `org-root` account safely, otherwise
  you will delete the IAM user you are using to tear down the account in
  the middle of the `destroy` and corrupt the state.
* It's easiest to wait until all resources in all your accounts are
  destroyed to begin closing accounts; this will remove all the
  organization SCPs and let you remove accounts from the organization
  as you go.
* If your organization has an SCP applied to OUs which restricts editing billing data (which is a common practice for I), you will need to remove that SCP from accounts you're attempting to close first. You can do this either by removing the SCP from the affected OU or moving the account out of the affected OU.
* In order to completely close an account (aside from the `org-root`
  account), you'll need to go through the password recovery procedure for
  the root user account (ie, you need to try to log in with the email
  address for the account and click the "Forgot Password" link), then
  set up billing information for the account. Once you have done that,
  you can safely remove the account from the AWS Organization (either
  from the console or using the CLI) and then close it from the My
  Account panel.

## SSL certificates

For most projects, I'll hopefully be able to use AWS ACM certificates,
and those will get torn down with my Terraform teardown above. However,
if I've bought additional SSL certificates through another vendor, such
as SSLMate, I should revoke those certificates and close that account
as well.


## gitlab

Once you've torn down your AWS infrastructure and CircleCI, you can
shutdown your gitlab organization for the project. Here are the
guidelines for taking down your gitlab organization:

* Make sure the client has been able to make an archive of all
  repositories before you do anything else. Code I build for a client
  belongs to them, so I need to ensure they are able to keep a copy.
* If I are allowed (this varies based on the terms of the contract), I
  should make sure I keep an archive of any code repositories I want
  to retain.
* Delete any gitlab users that were created for CI/CD automation or other
  purposes. These are commonly created to allow CI/CD to access private
  repositories.
* Once the above steps have been completed, you can go into the settings
  for the gitlab organization and close it down. *This will delete all
  repositories in the organization*, so make sure you're ready for that
  before you do this.

## 1Password

*Deleting your 1Password account and vault for the project should be the
very last thing you do.* This is (hopefully) where you've kept all your
credentials for services, software, and accounts that this project uses,
so getting rid of this makes it *extremely* difficult to clean up anything
else you were using for your project. I recommend that you carefully
review the previous steps of this guide and look at the credentials kept
in 1Password to ensure that you've closed down everything else that you
are relying on 1Password for.
