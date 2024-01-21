## Create GCP service account

```bash
gcloud config set project <GCP_PROJECT_ID>
gcloud auth application-default login

# Create service account
gcloud iam service-accounts create sa-crossplane-gcp-providers \
–description="Service account for the Crossplane GCP providers" \
–display-name="Crossplane GCP Provider Service Account"

# Download the credentials json file
gcloud iam service-accounts keys create gcp-credentials.json \
    --iam-account=sa-crossplane-gcp-providers@<GCP_PROJECT_ID>.iam.gserviceaccount.com

```

## Create secret

```bash
kubectl create secret generic gcp-creds -n upbound-system \ 
  --from-file=credentials=./gcp-credentials.json
```

## Assign compute admin role to SA

```bash
gcloud projects add-iam-policy-binding <GCP_PROJECT_ID> --member serviceAccount:crossplane-2@<GCP_PROJECT_ID>.iam.gserviceaccount.com --role roles/compute.instanceAdmin
```