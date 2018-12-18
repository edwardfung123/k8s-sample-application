This is an example application to demo how to Kubernetes. In this example, we
will build a paid service to convert csv to excel. The user will upload the csv
file and leave an email. The csv-to-excel conversion is done async. When the
conversion is done, we can send email back to the user and provide a link to
download the excel. The link will expire after a few hours.

# Services

1. Web UI - A form to upload csv and email. Link to download excel.
2. API - Upload csv and email.
3. Object storage system - Store the csv, excel.
4. Task Queue - Enqueue the conversion job.
5. Worker - Do the conversion job.
6. Email - Send email.
7. Database - Store the upload record.

# Useful commands

## Using the minikube docker

```
eval $(minikube docker-env)
```

## Undo and use back the machince's docker

```
eval $(docker-machine env -u)
```

## Get public IP

```
minikube ip
```
