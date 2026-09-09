---
hide:
    toc: true
---

# RCS Account Creation Procedures

{% from "tickets/_macro/template_config_table_rows.md.j2" import config_rows %}

RCS account creation is self-managed. All eligible UAB and XIAS people can create an RCS account by visiting <https://rc.uab.edu> and filling out a form. Eligibility is verified as part of the automated account creation process.

## How Do I Handle a Support Request?

Reply with the following, then close the ticket.

```text
Greeting and welcome message here ...

You can create a Research Computing Systems (RCS) account by visiting <https://rc.uab.edu> and filling out a short form. All UAB students, faculty, and staff are eligible to create an account. External collaborators with XIAS accounts may also be eligible, with some restrictions. For more information, please visit our "RCS Account Creation" documentation at <https://docs.rc.uab.edu/account/rcs/create/>. Be sure to check the "Next Steps" section when you've created your account to see what services and platforms we offer.

If you need additional support in the future ...
```

## Creating a Template in ServiceNow

See [How Do I Create a Template?](../../snow_templates.md#how-do-i-create-a-new-template) for general instructions. Use the following table to guide filling out the fields.

{{ config_rows("account_rcs_create", "Response to RCS or Cheaha account request") }}
|                     |           |          |                                                       |
| **Template Fields** |           |          |                                                       |
| Additional comments | text      | yes      | [Canned Response](#how-do-i-handle-a-support-request) |
| Assignment group    | drop-down | yes      | Research Computing                                    |
