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


### Cloud Storage
Creating a bucket
```
BUCKET_NAME=gs://$GOOGLE_CLOUD_PROJECT-bucket
gsutil mb -l us-central1 $BUCKET_NAME
```

Compute service account access to this bucket<br>
_This ensures that Vertex Pipelines has the necessary permissions to write files to this bucket._
```
gcloud projects describe $GOOGLE_CLOUD_PROJECT > project-info.txt
PROJECT_NUM=$(cat project-info.txt | sed -nre 's:.*projectNumber\: (.*):\1:p')
SVC_ACCOUNT="${PROJECT_NUM//\'/}-compute@developer.gserviceaccount.com"
gcloud projects add-iam-policy-binding $GOOGLE_CLOUD_PROJECT --member serviceAccount:$SVC_ACCOUNT --role roles/storage.objectAdmin
```


### Compressed Tar Ball
Packaging a training folder into a compressed tar ball, and then store it in your Cloud Storage bucket.
```
BUCKET_NAME = "gs://qwiklabs-gcp-00-th1s1sat3st0ly"

! rm -f custom.tar custom.tar.gz
! tar cvf custom.tar custom
! gzip custom.tar
! gsutil cp custom.tar.gz $BUCKET_NAME/TRAINING_FOLDER_NAME.tar.gz
```
