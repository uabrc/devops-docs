# Common Tickets

<!-- markdownlint-disable MD033 MD034 -->

## Account Registration

### General Cheaha Account Request

All UAB users can request their own Cheaha account by going to [https://rc.uab.edu](https://rc.uab.edu) and filling out a short form. No intervention on our end is required.

**Canned Response**:

> Hi,
>
> All UAB students, faculty, and staff can create their own Cheaha account by going to https://rc.uab.edu and filling out a short form. Once the form is complete, your account will be immediately ready for use. All accounts have 5 TB of personal space on the cluster. Please read through our Cheaha documentation at https://docs.rc.uab.edu/cheaha/getting_started/ to familiarize yourself with how the cluster operates. If you are able to create your account or run into any errors, please let us know in this ticket. Thank you

### Cloud Account Request

Cloud accounts must be created by Clyde or John as of now and is not linked with SSO. Go through the following steps:

1. Create a [task](#creating-a-servicenow-task) on the ticket giving the BlazerID or XIAS name for the person requesting the account. Commonly looks like `Create Cloud account for <blazerid_or_XIAS>`. Omit any `@uab.edu` string for BlazerIDs, but keep the email host for XIAS accounts.
2. Copy the task link from the main ticket page (looks like `TASK0000000`) and put in the Slack tickets channel something like `@rc-ops-grp <task_id> Request to create cloud account for <blazerid_or_XIAS>`. Make sure the task is an actual link to the task to make it easier on Ops.

**Canned Response**:

> Hi,
>
> I've passed this request along to our Ops team who should be able to create your account shortly. You will receive an email with instructions on how to activate the account and set your password once it's created. Cloud.RC is not currently connected to UAB's single sign-on so you can choose the same or different password from your BlazerID or XIAS account. Please go to our documentation at https://docs.rc.uab.edu/uab_cloud/ to familiarize yourself with Cloud. There is a tutorial on required setup steps before you're able to create any virtual machines. If you run into any issues, feel free to let us know in a new ticket. Thank you

### LTS Account Request

Cloud accounts must be created by Clyde or John as of now and is not linked with SSO. Go through the following steps:

1. Create a [task](#creating-a-servicenow-task) on the ticket giving the BlazerID or XIAS name for the person requesting the account. Commonly looks like `Create Cloud account for <blazerid_or_XIAS@host.edu>`. All personal accounts should include the email host (`@uab.edu` or otherwise)
2. Copy the task link from the main ticket page (looks like `TASK0000000`) and put in the Slack tickets channel something like `@rc-ops-grp <task_id> Request to create cloud account for <blazerid_or_XIAS@host.edu>`. Make sure the task is an actual link to the task to make it easier on Ops.

**Canned Response**:

> Hi,
>
> I've passed this request along to our Ops team who should be able to create your account shortly. You will receive an email with a set of access keys and instructions on how to use the account. Please visit our documentation at https://docs.rc.uab.edu/data_management/lts/ to familiarize yourself with LTS. If you run into any issues, feel free to let us know in a new ticket. Thank you

## Shared Space Requests

General rules for shared spaces across Cheaha, Cloud, and LTS:

- Each PI is always allowed one shared space on each platform for their lab, same for cores.
    - If a PI is also a core director, they are allowed to have a shared space for each on all platforms
    - Additional shared spaces within Cheaha and LTS are currently not permitted. Additional Cloud projects may be created on a case by case basis
- Quota increase policies vary based on the platform. See specific sections for more details.
- Shared space creation requests must come from a PI (have title of Assistant, Associate, or Full Professor) or core director (almost always Professor title but could vary)
    - Changes to project access must be requested either by the project owner or a data steward for that project.

If someone already has a shared space and is asking for a quota increase, refer to the [below section](#shared-space-quota-increases) for current policies and responses.

### Cheaha Project Space

**Example Ticket**: [RITM0694996](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3Dafe0e0a81bdd0a908a7821f2b24bcbf4%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D50%26sysparm_record_rows%3D5439%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_updated_on)

Cheaha spaces follow all of the general rules listed at the beginning of the [shared space section](#shared-space-requests).

1. Check their job title at the following places:

    1. The Outlook People menu. Search for the person's name or email in the search bar and it should pull up some information on them. This is useful since it works for both UAB and UABMC email addresses.

    2. The [UAB Directory](https://www.uab.edu/directory/). You'll need to authenticate to search for people, but you can enter either their name or their BlazerID. Their position should be listed in the results. See below for an example

        ![! Example directory entry with job title](res/example_uab_directory_entry.png)

    3. Search their name plus UAB in Google. Do some sleuthing around the UAB site.

2. Check if they already own a project space.

    1. You will need their BlazerID for this which is on the ticket if the original email came from their UAB email address. If it came from a UABMC or other address, you can use the UAB directory and search for them there.

    2. Open a terminal on Cheaha and run the following: `ll /data/project | grep <blazerid>`. If nothing shows up, they do not own a project space yet. If an entry does appear, check if it's a core account by searching the name of the project space. These projects are generally named exactly the same as the name of the core. If you're unsure about something, get assistance from William, Matt, or Prema or get clarification about the existing project space on the ticket.

3. If they meet the criteria for the project space, ask them what they would like the name of the project space to be as well as a list of BlazerIDs to have access to the space. Suggest project names such as the following:

    1. Their last name + 'lab', e.g. `warrinerlab`. Make sure that project name does not already exist

    2. Their BlazerID + 'lab'. This is used when the requester has a last name that is already used in another lab space name, e.g. `zhang`.

    If they already have another name they would like, that's fine. Suggest they keep names as brief as possible to help others remember and type the name.

4. Make sure all users mentioned in the ticket already have a Cheaha account before putting in the request with Ops.

    1. Can check by going opening a terminal on Cheaha and running `ls -d /data/user/[username]` for each username. If there are a bunch of users listed, you can also use a regex to list which ones exist like so `ls /data/user | grep -e '[user1]|[user2]|[user3]|...`. Go through the returned list and check which IDs are missing, if any.

5. Once everything above is confirmed, create a [task](#creating-a-servicenow-task) including the requested project name, the owner, and the members. The description usually looks like `Create Cheaha project space [project_name] assigned to [owner]. Add [members]`

6. Post the task ID along with the description to the `#tickets` channel adding `@rc-ops-grp`. Usually will look like `@rc-ops-grp TASK00000 Request to create Cheaha project [project_name] assigned to [owner]. Add [members]`

**Canned Response (Space Approved)**:

> Hi,
>
> We can get that project space created for you. Please give us a list of BlazerIDs for the people who should have access to the space as well as the name of the space. In general, we suggest names such as [[insert suggested names]], but we can use any name you prefer. Once we get that information, we can get everything set up for you.

**Canned Response (Space Denied Due To > 1 Project Space)**:

> Hi,
>
> I'm sorry, but due to storage constraints on Cheaha, we limit the number of project spaces to 1 per PI. If you need additional storage, we have our long-term storage platform available. If you don't have an account there, we can create a lab account with access to 75 TB of space. Let me know if that sounds good to you. Sorry again.

### Cloud Shared Space

**Example Ticket**: [RITM0694997](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3D63a72ce01b114a908a7821f2b24bcbb1%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D2%26sysparm_record_rows%3D57%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eshort_descriptionCONTAINSopenstack%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_updated_on)

RC does not currently have policies for OpenStack projects, the [general rules](#shared-space-requests) apply.

Go through the following steps to verify we can create a project:

1. Make sure the requester has a professor title, is a data steward for a PI, or is a core director.

2. Ask them for the name of the project as well as the BlazerIDs for anyone who needs access if not already provided. Anyone who needs access will first need to request a personal Cloud account.

    1. Cloud project names typically match Cheaha project names if one exists. Check if the PI owns a Cheaha project (open a terminal on Cheaha and run the following: `ll /data/project | grep <blazerid>`) and suggest that as a Cloud project name. Same thing applies for Core projects, they are most often named after the Core itself.

3. Ask `rc-ops-grp` if the requestor already has a project assigned to them or to the PI they are making the request for. Also ask if they have a personal Cloud account.

    1. If they already have an assigned project, check with William, Matt, or Prema to discuss whether an additional project should be approved in this case. Be sure to ask the requestor why they need an additional project if they already have one.

4. Create a [task](#creating-a-servicenow-task) on the ticket giving the project name, owner, and members. Commonly looks like `Create Cloud project <project_name> assigned to <owner>. Give <member_list> access`.

5. Copy the task link from the main ticket page (looks like `TASK0000000`) and put in the Slack tickets channel along with the description. Should look something like `@rc-ops-grp TASK0000000 Request to create Cloud project <project_name> assigned to <owner>. Give <member_list> access`.

**Canned Response (Space Approved)**:

> Hi,
>
> I've gone ahead and passed along the project request to our Ops team, they will be in contact with you after the space is created. Please make sure each member of the group has requested their personal Cloud account so we can add them to the group. Cloud projects have the same quota limits as individual accounts. If a quota increase is needed for a shared space, please submit another ticket explaining the situation and we would be happy to help as much as we can. Thank you.

**Canned Response (Space Denied)**:

> Hi,
>
> It looks like you already have a Cloud project assigned to you at [project_name]. We generally permit one Cloud project per lab/core with some exceptions. If you need another distinct project space, please explain why. We can also consider increasing the base allocation for your current project if that makes more sense for your situation, we would just need a general idea of how many more resources you expect to need. Let us know and we will be happy to help as much as we can. Thanks

### LTS Shared Space

**Example ticket**: [RITM0693695](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3De3653a4697c5c2500917316bf253afcf%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D5%26sysparm_record_rows%3D56%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eshort_descriptionCONTAINSLTS%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_updated_on)

LTS shared spaces follow the [same general rules](#shared-space-requests) as Cheaha project spaces.

Go through the following steps to verify we can create a project:

1. Make sure the requester has a professor title, is a data steward for a PI, or is a core director.

2. Check if they or the PI in case the requester is a data steward already owns a project space on Cheaha (open a terminal on Cheaha and run the following: `ll /data/project | grep <blazerid>`). If they do, propose the same name for the LTS project. If they do not, request a name for the space and if they would also like a Cheaha project created. LTS spaces are generally paired with Cheaha spaces for active and archived data or very large active datasets.

3. Ask `rc-ops-grp` if the requestor already has a project assigned to them or to the PI they are making the request for. Also ask if they have a personal LTS account. If they don't have a personal LTS account, that should also be created on this ticket.

4. Create a [task](#creating-a-servicenow-task) on the ticket giving the space name and owner. Will look generally like `Create LTS shared space [name] assigned to [owner]`.

    1. If the requester also needs a personal account, create a separate task on the same ticket following the instructions found [above](#lts-account-request).

5. Post the task(s) to `#tickets` along with the description. Will look something like `@rc-ops-grp TASK000000 Request to create LTS shared space [name] assigned to [owner]`.

**Canned Response (Space Approved)**:

> Hi,
>
> I've passed along your request to our Ops team who will contact you when the account has been created. Please read over our docs at https://docs.rc.uab.edu/data_management/lts/ to learn how to interact with LTS. The lab/core account will have separate access keys from your personal account so you will need to keep track of both sets. LTS lab/core accounts operate differently from Cheaha project spaces. You control access to every bucket in the account through policy files, you do not need to contact us to give a collaborator access to a bucket. Please read more about policy files on our LTS docs at https://docs.rc.uab.edu/data_management/lts/policies/. If you need any assistance setting up or applying the policy files, please come to our office hours on Mondays or Thursdays from 10-12 on Zoom. You can find links to those at https://docs.rc.uab.edu/#how-to-contact-us.

## Shared Space Quota Increases

As more data are created by our researchers, they will inevitably ask for increases to the amount of storage allocated to them on each platform as well as compute increases to Cloud account. Below are the quota increase policies for each platform in Research Computing.

- **Cheaha**: Quota increases are currently not approved on Cheaha for any reason due to storage constraints. If they need more space, direct them to LTS.
- **Cloud**: Quota increases for OpenStack are determined on a case by case basis depending on justification from the requester. Request assistance from Matt, William, or Prema.
- **LTS**: In order to increase an LTS project quota, a new node needs to be purchased by the lab or core. The node will be sold at cost determined by the manufacturer and will increase the quota to 133 TB. Nodes are supported for 5 year terms after which the node will need to be replaced at cost by the lab. Quotes can be requested at any time before committing to a purchase.

### Quota Increase Canned Responses

**Cheaha**:

> Hi,
>
> I'm sorry, but due to storage constraints on Cheaha, we are not currently increasing quota limits on Cheaha for any projects or users. If you need additional storage, we have our long-term storage platform available. If you don't have an account there, we can create a lab account with access to 75 TB of space. Let me know if you's like more information on that. Sorry again.

**Cloud**:

> Hi,
>
> We'd be happy to help as much as we can. Due to some compute and storage constraints on Cloud, please explain what the extra compute will be used for as well as an estimate of how much extra compute you believe you will need. We will talk it over with our Ops team and see if we can make it work. Let me know if you have any other questions as well.

**LTS**:

> Hi,
>
> Storage increases on LTS are possible through purchasing a full storage node. A full node has a capacity of 133 TB and is purchased at cost from Dell, our distributor. We will install the node and maintain it through its support EOL, typically 5 years. There will be no maintenance or power costs for you over that timeframe. If this option is something you would be interested in, we can ask Dell for a quote to share with you. The cost of these nodes varies over time so we don't have an accurate value for right now. Let us know what you think. Thank you

## Software Installation

In general, we do not want to install software as modules if we do not need to. Having something available as a module means we need to maintain and update it which is time-consuming. Most software researchers want to use is available via Anaconda/Pip and Docker, both of which are installable by the researcher. When dealing with these requests, we need to find the package first and test the installation process to make it seamless for the researcher. I generally check package availability in the following order:

1. Check conda for software package, google `conda <software_name>`
2. Check dockerhub for software, google `dockerhub <software_name>`. Can be used with singularity on the cluster
3. Check the current available modules to see if they missed it. Use `module spider` with part of the software name and see what appears.
4. Check the github repo or software website for installation instructions.

You will want to check on package versions as well as when the packages were last updated at each site to see if one source has a more recently updated version. If a specific older version is requested, you can test with that specific version as well as offer the option for the newer version depending on what they want.

### Conda/Pip Installation

**Example Ticket**: [RITM0667998](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3Df448fd171b52fd902e00eb93604bcb2a%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D12%26sysparm_record_rows%3D249%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eshort_descriptionCONTAINSinstall%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_created_on)

Try installing the requested package into a clean environment using the exact instructions on the package's anaconda.org page. If you need to use `pip` to install a package, make sure you install `pip` into the conda environment first to prevent the package from being saved in the `${HOME}/.local` folder. Installing pip will also install the newest version of Python by default. You will need to check on the package's PyPi page which versions of Python the package is compatible with. You can find this information at the bottom of the page in the Classifiers -> Programming Language section.

A simple example installing `samtools` from conda is shown below.

```bash
module load Anaconda3
conda create -n sam
conda activate sam
conda install bioconda::samtools
```

After installing the package, you can try to print the help message for the main function in the package (the `samtools` function in this example) to make sure the binary at least does that. The package's Github page should also ahve some general instructions on how to use the package along with some listed commands. You can also look in `${HOME}/.conda/envs/<environment>/bin` to see if one of the commands there looks important and try to print the help for it.

It's not important to make sure the full package runs perfectly. We almost never have the expertise nor the data necessary to test these pipelines fully. Making sure it prints a help message is the most we need to do. If the users have issues running it, they will let us know.

**Canned Response**:

> Hi,
>
> This package is available via Anaconda. You can install it using the following commands:
>
> \------------------------------------------------------------------
>
> module load Anaconda3<br>
> <insert full list of installation commands here\>
>
> \------------------------------------------------------------------
>
> Once the installation finishes, you'll be able to use the package using the following command: <insert tested help message command>. To use this package in other jobs, you do not need to install it again, you just need to load Anaconda3 and activate the environment created above. You can read more about Anaconda in our docs at https://docs.rc.uab.edu/workflow_solutions/using_anaconda/. Let us know if you run into any issues.

### Singularity

**Example Ticket:** [RITM0691497](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3Ddd5f58861bbc02108a7821f2b24bcbcd%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D1%26sysparm_record_rows%3D141%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eshort_descriptionCONTAINSmodule%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_created_on)

If a package or software isn't available via conda/pip, search on Dockerhub instead. Most containers from Dockerhub can be easily converted to Singularity containers on Cheaha. The downside is that it requires the user to learn a little bit of singularity, but it can make installation and use easier in the long run.

Search `<software> docker` to find potential matches on dockerhub. There may also be instructions for installing via Docker on the Github page so it helps to check there too. Containers can be created like so:

```bash
singularity pull fmriprep.sif docker://nipreps/fmriprep
```

If the entrypoint for a container is a command-line tool, you may be able to print the help for that tool with `singularity run`. Using the fmriprep example above, it would be `singularity run fmriprep.sif --help`. If it prints a help message and doesn't error, it should be fine. You can also use `singularity exec` or `singularity shell` commands to test if some parts of the container work correctly. Like with conda, don't worry about making sure a container run an entire pipeline correctly, the user will let us know if it doesn't.

**Canned Response:**

> Hi,
>
> This tool is available through Singularity, a container tool similar to Docker. A container packages up software and all its dependencies into a single file (a.k.a image) that can be run from one computing environment to another. We have documentation on how to use Singularity at https://docs.rc.uab.edu/workflow_solutions/getting_containers/#containers-on-cheaha. You can install the container using the following commands:
>
> \-----------------------------------------------------------------------------
>
> <insert singularity pull command\>
>
> \-----------------------------------------------------------------------------
>
> You can run the container using the following command: 'singularity run <container.sif> [add options here]'. If you need help running the container, please come to office hours on Monday or Thursday from 10-12 on Zoom and we would be happy to assist. You can find the Zoom links at https://docs.rc.uab.edu/#how-to-contact-us.

Note that you may need to change the example command based on what works. For example, if a container doesn't have an entrypoint, anything inside it will need to be run with `singularity exec <container.sif> <command> [options]` instead of `singularity run`. Make sure you have a baseline understanding about how to run something from that container before responding.

### Module Installation

**Example ticket:** [RITM0600320](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3Ddbb469f21b1ca114a8e26571604bcb77%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D12%26sysparm_record_rows%3D78%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eshort_descriptionCONTAINSupdate%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_created_on)

In almost every case where a piece of software is not available via conda or singularity, it will need to be installed as a module. In some rare instances, a user could install an `rpm`, `deb`, etc. package into their personal space, but this can be quite complicated. Ask Matt for details if you determine this is a potential solution.

If the software is licensed and has not already been installed, ask the user details about the license. Typical licensed software connects to a license server to distribute floating licenses or requires a license file installed in the module itself. Details on a license may also be included in the installation instructions. Licensed software typically restricts who can use it if the license is owned by a specific person, lab, or department. If that is the case, we need to know who should have access to the module as well.

1. Check if the software exists on [EasyBuild's supported software](https://docs.easybuild.io/version-specific/supported-software/). For example, here is an entry for the [R programming language](https://docs.easybuild.io/version-specific/supported-software/#r_1). It has up to version 4.3.3 available along with many older versions. Paid, licensed software is almost never found here. If it does not exist there, find a descriptive set of installation instructions on the software website or their Github repo.
2. Create an issue on our [cluster software repo](https://gitlab.rc.uab.edu/rc/cluster-software). Title should be something like `Install <software> Version <version_number>`
3. The issue description should contain the ticket number as well as a link to the easybuild site, a link to other installation instructions, or the instructions in an attached file. If the software is licensed, include details about how to set up the license and who should have access to the module.
4. Add the `Backlog` and other relevant labels to the issue. Submit the issue.

**Canned Response Prior to Installation:**

> Hi,
>
> We have passed this request along to our DevOps team. We do not have a definite timetable on when the module will be ready but will keep you updated as things progress. We appreciate your patience.

If your searching doesn't turn up any good installation instructions and those aren't included in the ticket, please ask the user to provide those instructions or point to a site where they can easily be found.

**Canned Response After Installation:**

> Hi,
>
> We have installed this under <insert full module name\>. You can load the module using the following command: 'module load <module\>'. Please test out the software and let us know if you run into any problems with it. Thank you

## Service Outage

**Example Ticket:** [RITM0690729](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3D7f72dc8197b442d00917316bf253af31%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D28%26sysparm_record_rows%3D2274%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5Eshort_descriptionCONTAINScheaha%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_created_on)

Some outages will occur over time, both planned and unplanned. We notify the community of planned outages beforehand. If you receive a ticket asking about a planned outage, you can respond with the email DevOps sent out if that addresses the question.

For unplanned outages, we generally don't have a great idea when service will be restored in the moment. Keep an eye on the `devops` channel or the channel related to the specific platform on Slack for updates from the Ops team. Otherwise, all tickets should receive a very general acknowledgement that we are aware of the issue and are working to resolve it.

**Canned Response:**

> Hi,
>
> We are aware of the current outage. Our team is working on restoring functionality as soon as possible. [Insert current status and timeframe if available]. We apologize for any inconvenience. Thank you.

### OOD Errors

**Example Ticket:** [RITM0694570](https://uabprod.service-now.com/nav_to.do?uri=%2Fsc_req_item.do%3Fsys_id%3Dd9beea331bcd82908a7821f2b24bcb84%26sysparm_record_target%3Dsc_req_item%26sysparm_record_row%3D1%26sysparm_record_rows%3D1%26sysparm_record_list%3Dassignment_groupDYNAMICd6435e965f510100a9ad2572f2b47744%5EnumberSTARTSWITHRITM0694570%5Eassignment_group!%3D4a687cd637f072c0cda353b543990ea8%5EORassignment_group%3D%5EORassignment_group%3D4a687cd637f072c0cda353b543990ea8%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5Ecat_itemNOT%2BIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5EORcat_item%3D%5EORcat_itemIN579212a93705a70024a67c1643990e84,61c24473db5650104ff1fd7aae961961,998fc4ec1b3aa5106bd68552604bcb3c%5Eopened_by%3De6c34574377371007114a6d2b3990e3a%5EORDERBYDESCsys_created_on)

Occasionally, there will be an OOD specific error that does not affect the cluster as a whole. This typically comes up as a `500 Internal Server` error. In this case, check if you also receive the error by going to both [https://rc.uab.edu](https://rc.uab.edu) and [https://rc.uab.edu/account](https://rc.uab.edu/account). Sometimes, the account creation service can have an issue while the main OOD will be fine so it's always good to check both.

If you don't see an error on either site yourself, have the user try to access OOD again using a Private Browser. If this still doesn't fix the issue, you can ask for assistance from Ops

If you also see an error, pass the error type along to rc-ops-team on Slack and let them know if it's happening for just the account page or for OOD as a whole.

## OOD App Specific Issues

As well as having errors that affect all jobs either on the cluster or just OOD, there are app specific errors that will appear and cause some issue for the user whether it's jobs failing (seen as a disappearing job card in the `My Interactive Sessions` page) or some function of the app not working the way the user thinks it should (installation errors for R packages in RStudio for example). These errors can vary both in origination and scope, but there are logs available for every OOD job started on the cluster for you to reference if the error is not immediately obvious from the ticket.

1. Ask the requester for the log files from a failed job as well as a copy of their `.bashrc` file that is loaded in every new session.

    1. The `.bashrc` is located at `$HOME/.bashrc` and must be added as a plain text file to the ticket.

    2. Have them follow the instructions [on our docs](https://docs.rc.uab.edu/cheaha/open_ondemand/ood_layout/#debugging-ood-job-failures) and attach a zip folder with the scripts and logs from the OOD job to the ticket. All of these files must be in a zip folder due to many of the files having a disallowed file type in SNow.

    **Canned Response Asking for More Details:**

    > Hi,
    >
    > We'd be happy to take a look. To help us, please follow the instructions at https://docs.rc.uab.edu/cheaha/open_ondemand/ood_layout/#debugging-ood-job-failures to retrieve the logs and scripts for a failed job. Zip those files and attach the zip folder to the ticket. As well, please attach your .bashrc as a plain text file to the ticket. You can find this file at $HOME/.bashrc

2. Check the `output.log` file for any error messages. Also check the `bashrc` for anything that stands out as particularly wrong.

3. See [common app errors](./common_app_errors.md) for further debugging instructions

## Addendums

### Creating a ServiceNow Task

When you need DevOps to complete something in order to address a ticket, create a Task in the ticket and use the Task ID when communicating with DevOps. You can create a task using the following steps:

1. Scroll down to the bottom of the ticket to the `Catalog Tasks` section. There will already be a task for the ticket as a whole. Click `New` to create a new task. This will open a new screen

    ![! Catalog Tasks section](res/snow_catalog_tasks.png)

2. Set the Assignment Group to `Research Computing`. Describe the task in the Short Description field. If necessary, add additional information to the Description box.

    ![! Creating a new task](res/snow_new_task_form.png)

3. Click `Submit` in the top right to finish creation. The new task will appear in the Catalog Tasks section with the original task now.

    ![! New task has been added to the catalog tasks](res/snow_new_task.png)

### Changing Ticket Requester

We like to have a record of who is submitting tickets over time which is usually tracked by ServiceNow. However, if a ticket is submitted from a non `@uab.edu` email, this will cause the `Requested For` field to show up as `Guest`. Unfortunately, this also happens for `@uabmc.edu` emails as well. If the person works at UAB in any capacity whether in the main university or any of the medical centers, they will have a record in the IDM database with a BlazerID. You can change update the `Requested For` field through the following steps.

1. When a request from a non `@uab.edu` email comes in, it will show like below:

    ![! Ticket showing requested for as Guest](res/snow_requested_for_guest.png)

    Click the information button next to the `Request` field (highlighted red above) and then click `Open Record` in the popup menu to open the Request page.

2. In the Request menu, click the magnifying glass next to the `Requested For` field to open an ID search window. It will look like below.

    ![! ServiceNow ID search with no one selected](res/snow_id_search_1.png)

3. Use one of the Name, Blazer ID, or UAB Medicine Email fields to search for the person who submitted the ticket.

    1. If you use a Name, it's possible multiple people appear if the name is common or that no one appears if the name they gave in the ticket is not their legal name entered in the database.

    2. It can also be difficult to search some international names due to different naming conventions based on their heritage. For example, some Asian countries place the family name before the given name, and some other countries commonly give a person more than 3 names. Some sleuthing may be required to make sure you're selecting the right person

    3. If you're in a situation where you're completely unsure which record to select, please ask the Requester for their Blazer ID. You can say it's necessary to get more information about the situation on whichever platform they are asking about as well.

    See below for an example of what appears when searching someone

    ![! SNow ID search with a result after searching a name](res/snow_id_search_2.png)

4. Click the name in the entry you want to assign as the ticket Requester for it to autofill their name and Blazer ID in the Request screen. Set the `Source` field to `Email` (most common, may also have been a phone-in, but very rare) and click `Update` in the top right.

5. If a person has an IDM entry but that entry doesn't have any information on their building or room assignment, those fields will be blank with a red star indicating you cannot update the ticket until those fields are filled in. You can just enter `?` into both of those fields.

6. Once everything is filled in to ServiceNow's satisfaction, you can click `Update` in the top right to save and exit the ticket or click `Save` to save your changes and keep the ticket open if you need to reply to them.

In the case where a person doesn't have an IDM entry (for instance if they are a XIAS user from a different institution), leave the field as Guest.
