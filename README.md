# Cheatsheet
Full documentation of gcloud is available in [gcloud CLI overview guide](https://cloud.google.com/sdk/gcloud)



### List
List the active account name
```
gcloud auth list
```
List the project ID
```
gcloud config list project
```

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


