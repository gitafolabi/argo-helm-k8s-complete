# DevOps Tech Challenge Environment

> [!WARNING]
> Make sure dependencies are installed before provisioning the environment

## Requirements

- [homebrew](https://brew.sh/) to install dependencies
- [just](https://formulae.brew.sh/formula/just) to automate cluster setup
- [kind](https://formulae.brew.sh/formula/kind) to create a kubernetes cluster
- [helm](https://formulae.brew.sh/formula/helm) a template engine / package manager for kubernetes
- [kubernetes-cli](https://formulae.brew.sh/formula/kubernetes-cli) to operate kubernetes cluster

## Instructions

1. At this stage you might have received an assignment for technicall challenge, please *read it carefully* 🔍
2. Fork this repo! All the code changes will be in your repository as you'll be using GitOps 🧲
3. Once you've completed the challenge, create an archive of the repository with all the code changes you've implemented 📦
4. Although *you might have read this already in the challenge instructions*, the solution implemented needs to work with the automation provided, the fork repo **must be reachable publicly** to let ArgoCD do his magic! 🐙
5. The archive will be sent to the email address detailed in the assignment 📧

Good luck and happy coding! 🍀

## Create the environment

> [!WARNING]
> If you already use `kind`, be aware that a cluster with name `dev01` will be used and this automation will add some changes to it. Update the name of the environment in `justfile` file in case it matches with your environment


Once you've installed all the required dependencies, you can proceed to provision the kubernetes environment.

You can run any of the following commands:

```shell
$ just
Available recipes:
    argocd-url # 🐙 Prints ArgoCD instance url
    clean-up   # 🧻 Cleans up the provisioned environment
    default    # 📚 Information from recipes available
    provision  # 🚀 Provision a Kubernetes cluster with required dependencies
```

There're also available some hidden recipes in case you need to redeploy ingress-nginx or argocd helm charts:

```shell
$ just _check-nginx          # To check. install or update the ingress-nginx helm release

$ just _check_argocd         # To check, install or update the argocd helm release

$ just _kind-update_context  # To change kubernetes context to the right environment
```

## ArgoCD

ArgoCD is part of the components that will be installed by default in the cluster, to remove the hassle of having to deal with admin credentials and https, we've made some changes in the application to allow anonymous access as admin and avoid TLS, we know this is not secure but it is just to speed things up! ✈

You can get access to ArgoCD at [http://argocd.apps.127.0.0.1.nip.io](http://argocd.apps.127.0.0.1.nip.io)
