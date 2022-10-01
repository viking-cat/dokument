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

<pre>
# Users
$ oc login -u &#60;username&#62;                                    Attempts to login with the named user
$ oc login --token=&#60;token&#62; --server=&#60;address:port&#62;          Login with token to server
$ oc logout                                                 Logs out current user
$ oc whoami                                                 Shows the current user


# Projects
$ oc projects                                               Lists all projects
$ oc project &#60;name&#62;                                         Switch to named project
$ oc new-project &#60;name&#62;                                     Creates a new project

# Config Maps
$ oc get cm                                                 Lists all config maps
$ oc get configmap                                          Lists all config maps
$ oc explain configmap                                      Documentation about config maps
$ oc create configmap message-map &#60;arguments&#62;               Create a configmap called "message-map" in templates folder with arguments, ex:
                                                            oc create configmap message-map --from-literal MESSAGE="Hello from configmap"
$ oc create configmap file-map --from-file=&#60;arguments&#62;      Creates a configmap called "file-map" from file
                                                            oc create configmap file-map --from-file=MESSAGE.txt
$ oc create configmap pods-example --from-file &#60;folder&#62;     Creates a configmap called "pods-example" from folder
                                                            oc create configmap pods-example --from-file pods
$ oc get -o yaml cm/message-map                             See contents of configmap
$ oc set env dc/hello-world --from cm/message-map           "Consume" config map, or simply apply config map on to hello-world deployment


# Deployments
$ oc new-app &#60;address&#62; --as-deployment-config               Launch deployment config, ex
                                                            oc new-app quay.io/practicalopenshift/hello-world --as-deployment-config
                                                            Address can also point at a git repository and will automaticall trigger a build in that case
$ oc new-app &#60;address&#62; --name demo-app --as-deployment-config    Change label from "app=hello-world" to "app=demo-app"
                                                            Changing label allows for multiple deployments of same thing that can be created and deleted separately
    $ oc logs -f buildconfig/hello-world                    Follow the build process
$ oc get dc                                                 Get deployment configs
$ oc get istag                                              Get image stream tags
$ oc delete dc/hello-world                                  Remove the deployment config named hello-world
$ oc describe dc/hello-world                                Get information about the hello-world decployment config
$ oc delete all -l app=hello-world                          Delete all resources with the "app=hello-world" label (-l argument)
                                                            Recommended cleanup method
$ oc get -o yaml dc/hello-world                             See YAML for deployment config
$ oc rollout latest dc/hello-world                          Rollout new version of deployment config (upgrade)
$ oc rollback dc/hello-world                                Rollback one deployment config version backwards (downgrade)


# Services
$ oc explain svc                                            Service documentation
$ oc get svc                                                Get services
$ oc expose --port 8080 pod/hello-world-pod                 Exposes POD inside the OC cluster (not externally accessible)
$ oc expose svc/hello-world                                 Expose hello world PODs service externally, use OC Status to see generated address
$ oc delete svc/hello-world                                 Removes the hello-world service


# Pods
$ oc status                                                 The status of OpenShift right now
$ oc get pods                                               Get information about PODs
$ oc create -f &#60;yaml&#62;                                       Creates pod based on local yaml file
$ oc delete pod &#60;pod&#62;                                           Removes POD
$ oc rsh &#60;pod&#62;                                              Open shell into POD
    exit                                                        Type exit inside shell to leave the PODs shell
    env                                                         See all environment variables (IP etc)
$ oc get pods --watch                                       See live in another terminal how the state of pods changes


# Secrets
$ oc get secret                                             List all secrets
$ oc create secret &#60;pod&#62; &#60;name&#62; --from-literal &#60;key value pair&#62;                     Creates a secret of "type" with "name", followed by "key-value-pair", example:
                                                            oc create secret generic message-secret --from-literal MESSAGE="Secret Message"
$ oc get -o yaml secret/message-secret                      Inspect secret with name "message-secret"
$ oc set env dc/hello-world --from secret/message-secret    Update dc/hello world with secret (which contained MESSAGE="Secret Message") this will overwrite old MESSAGE


# Replication Controller
$ oc get rc                                                 See replication controllers


# Resources
$ oc delete &#60;name&#62;                                          Deletes named resource like pod, container, file etc
$ oc delete all -all                                        Complete cleanup


# Help
$ oc help                                                   Basic commands
$ oc explain &#60;thing&#62;                                        Explains about the "thing", ex $ oc explain pod
$ oc explain &#60;thing&#62;.&#60;detail&#62;                               Explains more about the "detail" of the "thing", ex $ oc explain pod.spec
</pre>

# Annat

[Minishift](https://github.com/minishift/minishift)

{% include page-columns.html cols=2 content=capture_links %}
