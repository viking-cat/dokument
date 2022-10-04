---
top: false
parent: "virtualisering"
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
$ oc describe project/&#60;name&#62;                                Get detailed informaiton about project

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
$ oc new-app myproject/hello-world --as-deployment-config   Now creates DC from existing image steam instead of remote
$ oc get dc                                                 Get deployment configs
$ oc get istag                                              Get image stream tags
$ oc delete dc/hello-world                                  Remove the deployment config named hello-world
$ oc describe dc/hello-world                                Get information about the hello-world decployment config
$ oc delete all -l app=hello-world                          Delete all resources with the "app=hello-world" label (-l argument)
                                                            Recommended cleanup method
$ oc get -o yaml dc/hello-world                             See YAML for deployment config
$ oc rollout latest dc/hello-world                          Rollout new version of deployment config (upgrade)
$ oc rollback dc/hello-world                                Rollback one deployment config version backwards (downgrade)

$ oc set triggers dc/hello-world                            Outputs the triggers... (?)
$ oc set triggers dc/hello-world --remove --from-config     Removes the "from-config" trigger from deployment config
$ oc set triggers dc/hello-world --from-config              Adds the "from-config" trigger to the deployment config
$ oc set triggers dc/hello-world --remove --from-image hello-world:latest           Removes the "from-image" trigger from deployment config
$ oc set triggers dc/hello-world --from-image hello-world:latest -c hello-world     Adds the "from-image" trigger to the deployment config for container...(?)
$ oc set deployment-hook dc/hello-world --pre -c hello-world -- /bin/echo Hello from hook   Adds a pre deployment hook
$ oc get events                                             To find and see pre-hook output
$ oc set probe dc/hello-world --liveness --open-tcp=8080    Sets a probe that tries to connect to port 8080 to verify that it is alive


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
$ oc delete &#60;name&#62;                                          Deletes named resource like pod, container, file etc
$ oc delete all -all                                        Complete cleanup
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


# Builds & Buildconfig
$ oc start-build bc/hello-world                             Start a build (happens in pods so oc get pods --watch can be used for a bit of info)
$ oc cancel-build bc/hello-world                            Cancels an ongoing build
$ oc get build                                              List all the builds (builds runs in pods)
$ oc logs -f build/hello-world-1                            See the log of a specific build (get build to find names of builds)
$ oc new-build &#60;address&#62;                            Builds an image from "source", detailed example command below:
                                                            oc new-build https://gitlab.com/practical-openshift/hello-world.git
$ oc get buildconfig                                        List the buildconfigs
$ oc logs -f buildconfig/hello-world                        See the log of a specific buildconfig
$ oc get -o yaml buildconfig/hello-world                    See the content of the buildconfig for hello-world

# Image Streams & Tags
$ oc get is                                                 See image streams
$ oc describe is/hello-world                                Inspect image stream
$ oc import-image &#60;image path&#62;                              Adds an image stream, see example below:
                                                            oc import-image --confirm quay.io/practicalopenshift/hello-world
                                                            **output mentions "local" can it use something from drive?**
                                                            oc new-app myproject/hello-world --as-deployment-config
                                                            Now creates DC from existing image steam instead of remote 
$ oc delte is/hello-world                                   Delete an image stream
$ oc get istag                                              See image stream tags
$ oc describe istag/hello-world:latest
$ oc tag &#60;old&#62; &#60;new&#62;                                        Create a new tag for resource
                                                            oc tag quay.io/image-name:tag image-name:tag


# Volumes
$ oc describe cm/cm-volume
$ oc set volume dc/hello-world --add --mount-path /empty-dir-demo --type emptyDir       This creates a volume of emptyDir type
$ oc create configmap cm-volume --from-literal file.txt="CM File Contents"              Step 1: Create configmap
$ oc set volume dc/hello-world --add --mount-path /cm-dir --configmap-name cm-volume    Step 2: Mounts configmap as volume


# Scaling
$ oc scale dc/hello-world --replicas 3                              Sets how many identical pods should run in the ... namespace (?)
$ oc autoscale dc/hello-world --min 1 --max 10 --cpu-percent 80     
$ oc get hpa                                                        HPA = Horizontal Pod Autoscale


# Help
$ oc help                                                   Basic commands
$ oc explain &#60;thing&#62;                                        Explains about the "thing", ex $ oc explain pod
$ oc explain &#60;thing&#62;.&#60;detail&#62;                               Explains more about the "detail" of the "thing", ex $ oc explain pod.spec
</pre>

# Annat

[Minishift](https://github.com/minishift/minishift)

{% include page-columns.html cols=2 content=capture_links %}
