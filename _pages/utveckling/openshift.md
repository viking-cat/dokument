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

### Login to OpenShift with CLI

1. On the OpenShift Apps page
2. Click you username in the top right corner
3. Select "Copy Login Command"
4. A new window will open and you have to login again by clicking the "DevSandbox" button
5. An empty page with the "Display Token" is displayed
6. Click "Display Token"
7. Copy the long text starting with "OC login" below "Login with this token"
8. Go to your powershell terminal and paste it in, then press enter

You should see information about Logged in with... and one or more projects being mentioned and one is already selected for you.

# Commands

<table>
    <thead>
        <tr>
            <th>Command</th><th>Notes</th>
            <th>Command</th><th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$ oc projects</td><td>Lists all projects</td>
            <td>$ oc project <name></td><td>Switch to named project</td>
        </tr>
        <tr>
            <td>$ oc new-project <name></td><td>Creates a new project</td>
            <td>$ oc delete <name></td><td>Deletes named resource like pod, container, file etc</td>
        </tr>
    </tbody>
</table>

# Annat

[Minishift](https://github.com/minishift/minishift)

{% include page-columns.html cols=2 content=capture_links %}
