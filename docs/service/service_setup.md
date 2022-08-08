# Service Setup

These instructions should be used when you have finished building your application on [cloud.rc](cloud.rc.uab.edu), and are ready to publish your application to be used outside campus.

## Firewall Exception
When you are ready to open ports to your application instance to the world, use the following steps:
* Go [here](https://uabprod.service-now.com/service_portal?id=sc_home)
* Click on Security Exception (Firewall Rule Change).
* Fill out the form:
  
    `Requester BlazerID`

    Fill out your blazerid. If you're making the request on someone else's behalf then use their blazerid.

    `Application Name`

    Specify the application name or the DNS entry for your application i.e. docs.uabgrid.uab.edu

    `Source IP Addresses`

    If your application would interact with particular IPs, then mention them here with a comma separator. If it should be open to anyone outside campus then use ``Any``

    `Destination IP Addresses`

    IP Address of your OpenStack instance.

    `Destination TCP Port List`

    Port that needs to be open. In case of a webapp request, you need to open 80,443

    `Destination UDP Port List (Enter N/A if not applicable)`

    N/A

    `Other Protocols (Enter N/A if not applicable)`

    N/A

    `System/Application Information`

    Check all that apply. 

    `What type of sensitive or restricted data is stored or processed?`

    Check all that apply. 

    `Select number of months needed for exception`

    Select as needed. 12 months is the maximum allowed timeline.

    `Justification/Description`

    Specify the reason you want to apply for security exception, and how the application would be used.

* Hit ``Submit`` button.


## DNS Record setup
Email [AskIT](mailto:askit@uab.edu?subject=DNS%20Request), and specify that you want to create a new A record for the IP address of you instance, and the DNS entry you requested a SSL certificate for.

