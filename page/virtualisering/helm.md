---
top: false
parent: "virtualisering"
layout: page
title: "Helm"
---

# What is helm

# Helm Cheat Sheet

<pre>
# Installation och Avinstallation
$ helm repo add &#60;namn&#62; &#60;url&#62; &#60;flaggor&#62;  (Helm repo add)[https://phoenixnap.com/kb/helm-repo-add-update-remove]
                                                    Tillåter dig lägga till adressen till ett chart repository. Efteråt kan "namn" användas som en förkortning till att nå "url" adressen och alla charts där.
$ helm repo update                                  Uppdatera repon du har lagt till
$ helm search repo &#60;namn&#62;                           Du kan lista alla charts i "namn" efter att du har lagt till repositoriet.
$ helm repo remove &#60;namn&#62;                           Ta bort repot "nam" som du tidigare la till


$ helm install  &#60;namn&#62;  &#60;chart&#62; -f  &#60;values&#62;           (Helm Install)[https://helm.sh/docs/helm/helm_install/]
$ helm uninstall &#60;chart&#62;                            Uninstalls the helm chart from Kubernetes or Openshift (Helm Uninstall)[https://helm.sh/docs/helm/helm_uninstall/]
$ helm list                                         Lista alla installerade helm charts


# Configuration
$ helm pull &#60;namn/chart&#62;                            Laddar ner "chart" från repo med "namn" (konfigurerat med helm repo add) (Helm Pull)[https://helm.sh/docs/helm/helm_pull/]


# Information
$ helm get  &#60;resurs&#62;                                       [Helm Get](https://helm.sh/docs/helm/helm_get/)
$ helm get values &#60;release&#62;                                [Helm Get Values](https://helm.sh/docs/helm/helm_get_values/)

</pre>

{% include page-columns.html cols=2 content=capture_links %}
