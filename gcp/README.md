## Create secret

```bash
kubectl create secret generic gcp-creds -n upbound-system \ 
  --from-file=credentials=./gcp-credentials.json
```

## Assign compute admin role to SA

```bash
gcloud projects add-iam-policy-binding personal-332605 --member serviceAccount:crossplane-2@personal-332605.iam.gserviceaccount.com --role roles/compute.instanceAdmin
```