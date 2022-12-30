# flux2_bootstrap

## Pre-Requisites

```bash
kubernetes cluster Setup
```

## kubernetes cluster - minikube
[minikube setup](https://github.com/Naresh240/kubernetes/blob/main/minikube-setup/README.md)

## Install Flux2

```bash
export VERSION_FLUX=0.30.2 
curl -LO https://github.com/fluxcd/flux2/releases/download/v${VERSION_FLUX}/flux_${VERSION_FLUX}_linux_amd64.tar.gz
tar -xvzf flux_${VERSION_FLUX}_linux_amd64.tar.gz
chmod +x flux 
mv flux /usr/bin/
```
  
## Bootstrap github with flux2

```bash
export GITHUB_TOKEN=XXXXXXXXXXXXXXXXXXXXXXXX
flux bootstrap github \
  --owner=Naresh240 \
  --repository=flux2_bootstrap \
  --branch=master \
  --path=bootstrap \
  --personal
```

## Flux Reconcile

```bash
flux reconcile source git flux-system                               ### Github Reconcile
flux reconcile kustomization infrastructure -n flux-system          ### kustomization Reconcile
```
