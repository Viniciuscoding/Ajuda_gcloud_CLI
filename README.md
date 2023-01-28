# Ajuda_gcloud_CLI


## Cheatsheet



### Environment Variables
Environment variables, including GOOGLE_CLOUD_PROJECT, contains the name of our current Cloud project.
```
echo $GOOGLE_CLOUD_PROJECT
```

### Enabling APIs
Command to give your project access to the Compute Engine, Container Registry, and Vertex AI services:
```
gcloud services enable compute.googleapis.com \
                       containerregistry.googleapis.com \
                       aiplatform.googleapis.com \
                       cloudbuild.googleapis.com \
                       cloudfunctions.googleapis.com
```


