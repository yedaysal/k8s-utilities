# s3-file-uploader

Amazon S3 File Uploader Kubernetes CronJob

## Deployment Steps

1. Create an Alpine Linux Docker image which contains AWS CLI:

**Dockerfile**:

```
FROM alpine:latest

RUN apk add --no-cache aws-cli
```

**Build command**:

```console
docker build -t REGISTRY_HOST/PATH:TAG .
```

2. Push the image to the image repository:

```console
docker push REGISTRY_HOST/PATH:TAG
```

3. Create a configMap from the existing AWS CLI config file (*~/.aws/config*):

```console
kubectl create configmap aws-cli-config --from-file=path/to/your/aws/cli/config/file
```

4. Create a secret from the existing AWS CLI credentials file (*~/.aws/credentials*):

```console
kubectl create secret generic aws-cli-credentials --from-file=path/to/your/aws/cli/credentials/file
```

5. Change the "CHANGEME" value for the **image** key to image URL.

6. Change the "CHANGEME" value for the **imagePullSecrets** key to image pull secret.

7. Apply the *cronjob.yaml* manifest:

```console
kubectl apply -f cronjob.yaml
```