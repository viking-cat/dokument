---
layout: page
title: "OpenShift Training"
---

# Installation

## Docker Desktop

Installera [Docker Desktop](https://www.docker.com/) på datorn.

## Openshift

1. Register at [RedHat](https://www.redhat.com/)
2. Start a sandbox at [Openshift Sandbox](https://developers.redhat.com/developer-sandbox) (30-day limited)
    1. Click the "Start using your Sandbox" button
    2. It will ask for a verification code, choose the phone verification link instead.
    3. Fill in your phone number, wait for the SMS
    4. Once SMS arrives, return to verification code dialouge (if needed, should be a link)
    5. Verify with the code that your received
    6. Click the "Start using your Sandbox" button again
    7. On the new page, select Login with "DevSandbox"
    8. You might get one or more pages with more stuff you need to confirm

Might be possible to easily return with the [OpenShift Apps](https://openshiftapps.com) link
 
### OC CLI

1. Click the "question mark" in the top right corner, next to your user name
2. Select "Command Line Tools" from the dropdown
3. Download the "Download oc for Windows for x86_64"
4. Extract the "oz.zip" file
5. Copy the "oc.exe" file to a permanent folder like "c:\users\abc123\oc-folder"
6. Append the "c:\users\abc123\oc-folder" to the PATH environment variable of the system
7. Click OK button on each window to close them

Test the installation by opening PowerShell and run the "oc" command.

You should get a lot of OpenShift information inside the PowerShell terminal.

# Annat

[Minishift](https://github.com/minishift/minishift)

{% include page-columns.html cols=2 content=capture_links %}
