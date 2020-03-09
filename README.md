# Deploy Static Website to GCP Cloud Storage

This action helps you in deploying your static website to GCP cloud storage bucket. 

## Getting Started

Follow <a href="https://cloud.google.com/storage/docs/hosting-static-website">this guide</a> to get started. It give detailed instruction on how to make your bucket ready for deployment.

## How to use this Action?

On your workflow file,
```
- name: Deploy
  uses: actions/checkout@v2
  uses: abinmn/gcp-storage-bucket-action
  with:
    service_key: base64 encoded gcp service account key
    project: Name of the project that contains the storage bucket.
    home_page_path: Path of your homepage in cloud storage bucket
    error_page_path: Path of the 404 page to be shown
    build_folder: Path of the file to host. Use "${{ github.workspace }}" for the repository.
```

## base64 encode service key

Obtain the <a href="https://cloud.google.com/iam/docs/creating-managing-service-account-keys">service key</a> for your gcp bucket with the necessary permissions.

On linux ```base64 /path/to/key.json``` will give the base64 encoded version of the key. Save this key as a GitHub secret and use ```service_key: {{secrets.service_key(or whatever name you gave to the secret)}}```.
