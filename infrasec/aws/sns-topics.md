# [AWS](README.md) / SNS Topics

I are using SNS topics as mainly a way to round messages and event to other services such as PagerDuty or Slack.

SNS Topics can quickly get confusing for what their intended purpose and their current role they as infrastructure matures. This document is an effort to provide a recommendation for how to use and organize SNS Topic to keep them tidy.

## Organization

### Naming

The main purpose of the SNS topics are for notifications to teams. The naming convention reflects that, closely followed by the AWS account type (Gov or Com) and action.

`<TEAM>-<ACCOUNT_TYPE>-<ACTION>`

Sample names:

* app-com-notification
* infra-gov-alert

### Actions

The action or subscription that each SNS topic handled is up to the engineer. Alert focused SNS topics can have multiple subscriptions such as Slack and PagerDuty.

## Sample

Here is a common setup for infra and app team for account type com (commercial).

![SNS Topics](images/doc-sns-topic.png)
