---
hide:
    toc: true
---

# RC Cloud Account Creation Procedures

{% from "tickets/_macro/template_config_table_rows.md.j2" import config_rows %}

Cloud accounts are currently created by the Ops team and are not linked to SSO. Follow the steps below to process a Cloud account request.

## How Do I Handle a Support Request?

###  Review the Use Case and Obtain Manager Approval

Cloud accounts are currently limited due to resource constraints, each request must receive Manager approval before proceeding.

1. Review the ticket to see whether the user has provided a use case. If the use case is not provided, ask the user to explain what they need the Cloud account for and what they plan to accomplish.
1. Determine whether the use case can be accomplished using existing resources, such as Cheaha, or through alternate solution.
1. If an alternative solution is not suitable, discuss the request with the Manager to determine whether the Cloud account request can be approved.
1. If approved, document the approval reason in the work notes and proceed with the next steps.

Reply with the following to create intial discussion, and wait for follow-up

#### Response to RC Cloud Account Request
```text
Greeting and welcome message here ...

Cloud accounts are currently limited due to resource constraints, so we evaluate the use case before approving requests. Could you please provide some details about your intended use of the Cloud account? This will help us determine whether your use case can be supported through Cloud or if we can provide the best possible alternative solution.
{{ office_hours }}
```

### Create a ServiceNow Task

1. Create a new [task](../../tickets.md#creating-a-servicenow-task) on the ticket giving the BlazerID or XIAS name for the person requesting the account. Use `Request to create Cloud account` as the short description and `Create Cloud account for <blazerid_or_XIAS>` as the description. Omit any `@uab.edu` string for BlazerIDs, but keep the email host for XIAS accounts.
1. Copy the task link from the main ticket page (looks like `TASK0000000`) and put in the Slack tickets channel something like `@rc-ops-grp <task_id> Request to create cloud account for <blazerid_or_XIAS>`. Make sure the task is an actual link to the task to make it easier for Ops.

## Creating a Template in ServiceNow

See [How Do I Create a Template?](../../snow_templates.md#how-do-i-create-a-new-template) for general instructions. Use the following table to guide filling out the fields.

{{ config_rows("account_cloud_create", "Response to RC Cloud account request") }}
|                     |           |          |                                                       |
| **Template Fields** |           |          |                                                       |
| Additional comments | text      | yes      | [Canned Response](#response-to-rc-cloud-account-request) |
| Assignment group    | drop-down | yes      | Research Computing
