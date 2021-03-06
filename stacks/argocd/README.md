Getting Started after launching your Argo CD 1-Click App

After you have downloaded your kube config file, and are able to successfully connect to your DigitalOcean Kubernetes cluster (see https://cloud.digitalocean.com/kubernetes/clusters/ if you haven’t connected to your cluster) follow the instructions below to start using Argo CD.

## Argo CD CLI

Download and install the latest Argo CD version from https://github.com/argoproj/argo-cd/releases/latest.

Also available in Mac Homebrew; this can be installed with the following commands:

`brew tap argoproj/tap`
`brew install argoproj/tap/argocd`

## Login using the Argo CD CLI

Login as the `admin` user. The initial password is autogenerated to be the pod name of the Argo CD API server. This can be retrieved with the command:

`kubectl get pods --all-namespaces`

You'll see output similar to the following: 

```bash
NAMESPACE             NAME                                           READY   STATUS    RESTARTS   AGE
argocd                argocd-application-controller-df7d7867-nfsdw   1/1     Running   0          6m2s
argocd                argocd-dex-server-c54bcbcb4-rztdb              1/1     Running   0          6m2s
argocd                argocd-redis-78c9595d44-8cdkr                  1/1     Running   0          6m2s
argocd                argocd-repo-server-759bbb5f59-lz5lx            1/1     Running   0          6m2s
argocd                argocd-server-754cd4956f-wz48w                 1/1     Running   0          6m2s
kube-system           cilium-7zmcm                                   1/1     Running   0          4h10m
kube-system           cilium-kbx9c                                   1/1     Running   0          4h9m
...etc
```

The `argocd-server-xxxxxxxxxx-xxxxx` is the initial password. 

Using the initial password, login to Argo CD's LoadBalancer IP or hostname:

`argocd login <ARGOCD_CLUSTER>`

Change the password using the command:

`argocd account update-password`

## Login using the web UI

Visit your Argo CD 1-Click App web UI on the LoadBalancer IP or hostname. Login using the same credentials as above. 

## Using Argo CD 

You're now ready to define your applications, configurations, and environments. Get started via the Argo CD documentation here: https://argoproj.github.io/argo-cd/
