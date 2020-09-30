# [Standard Devz Processes](../README.md) / InfraSec

Infrastructure and security engineering (infrasec) is the practice of
building secure, robust systems that are foundational to having reliable
applications and services. While infrastructure as code is a core area
for this practice, it also involves system design, [incident
response](../incident-response/README.md), and a number of other fields.

## Theory

- [InfraSec Practice Charter](charter.md)
- :lock: [InfraSec "Book" Club - Talk and Article Suggestions](https://docs.google.com/document/d/1X0GDtCMrPnl_Zdpo0qEtaxUW4SocxnZairCM9JQAcyo/edit)

## Practice

- [AWS](aws/README.md) — my primary cloud provider.
- [Terraform](terraform/README.md) — my primary infrastructure as code (IaC) tool.
- [Ansible](ansible/README.md) — For when I have to build non-container based images (e.g., AMIs).

### Tutorials

#### AWS

- [Setting Up Your AWS User](https://gitlab.com/webmaeistro/legendary-waddle/blob/master/docs/how-to/setup-new-user.md) — How to set up your AWS user in the Martin's experience internal infrastructure. You will need the assistance of someone with administrative privileges in my AWS organization to help you.
- [Your First Lambda Function](tutorials/your_first_lambda_function.md) — A guide to deploying your first AWS Lambda Function with Go and Terraform.

#### Security

- [One-Time Passwords](tutorials/one-time-passwords.md) — How to set up one-time passwords for gitlab with 1Password.
- [YubiKey Configuration Guide](tutorials/yubikey-configuration.md) — How to get and configure a YubiKey for use in commit signing.
- [YubiKey SSO](tutorials/yubikey-sso.md) — How to configure a Google Account to use YubiKey (for GSuite admins).

### Other topics

- [Alert Providers](alert-providers.md)
- [Project Teardown Guide](teardown.md)
- [SSL Certificates](certs.md)
