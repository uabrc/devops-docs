# Common Tickets

## Account Registration

### General Cheaha Account Request

All UAB users can request their own Cheaha account by going to [https://rc.uab.edu](https://rc.uab.edu) and filling out a short form. No intervention on our end is required.

**Canned Response**:

```text
Hi,

All UAB students, faculty, and staff can create their own Cheaha account by going to https://rc.uab.edu and filling out a short form. Once the form is complete, your account will be immediately ready for use. All accounts have 5 TB of personal space on the cluster. Please read through our Cheaha documentation at https://docs.rc.uab.edu/cheaha/getting_started/ to familiarize yourself with how the cluster operates. If you are able to create your account or run into any errors, please let us know in this ticket. Thank you
```

### Cloud Account Request

Cloud accounts must be created by Clyde or John as of now and is not linked with SSO. Go through the following steps:

1. Create a [task](#addendum-creating-a-servicenow-task) on the ticket giving the BlazerID or XIAS name for the person requesting the account. Commonly looks like `Create Cloud account for <blazerid_or_XIAS>`. Omit any `@uab.edu` string for BlazerIDs, but keep the email host for XIAS accounts.
2. Copy the task link from the main ticket page (looks like `TASK0000000`) and put in the Slack tickets channel something like `@rc-ops-grp <task_id> Request to create cloud account for <blazerid_or_XIAS>`. Make sure the task is an actual link to the task to make it easier on Ops.

**Canned Response**:

```text
Hi,

I've passed this request along to our Ops team who should be able to create your account shortly. You will receive an email with instructions on how to activate the account and set your password once it's created. Cloud.RC is not currently connected to UAB's single sign-on so you can choose the same or different password from your BlazerID or XIAS account. Please go to our documentation at https://docs.rc.uab.edu/uab_cloud/ to familiarize yourself with Cloud. There is a tutorial on required setup steps before you're able to create any virtual machines. If you run into any issues, feel free to let us know in a new ticket. Thank you
```

### LTS Account Request

## Software Installation

1. Check conda for software package, google `conda <software_name>`
2. Check dockerhub for software, google `dockerhub <software_name>`. Can be used with singularity on the cluster

## Service Outage

### OOD Errors

RITM0694570

## Addendum: Creating a ServiceNow Task
