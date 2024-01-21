## Provision

```bash
z crossplane-IaC
kubectl apply -f compute.claim.yaml

kubectl get compute -w
kubectl get labcomputes lab-compute -n lab -w
```

## Deprovision

```bash
kubectl delete labcomputes lab-compute -n lab 
```

## Update

```bash
kubeclt apply -f compositions/compute.yaml
```
