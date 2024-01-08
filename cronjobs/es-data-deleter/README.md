# es-data-deleter

A Kubernetes Cronjob that deletes Elasticsearch data older than 15 days

## Deployment Steps

1. Clone this repository to your environment.

2. Build an Alpine Linux Docker image which contains the **curl** package:

```console
docker build -t REGISTRY_HOST/PATH:TAG .
```

3. Push the image to your image registry:

```console
docker push REGISTRY_HOST/PATH:TAG
```

4. Access your Kibana UI with an account that has administrative privileges.

5. On Kibana UI,
    - Go to **Management -> Stack Management -> Security -> API keys**.
    - Click on **+ Create API key**.
    - Name your API key and click on **Create API key** button.
    - On the Created API key section, select **Encoded** format and note the API key.

5. Open **cronjob-cm.yaml** file with a text editor, change **$EC_API_KEY** with the API key created in the previous step and save the file.

6. Apply the CronJob manifest:

```console
kubectl apply -f cronjob.yaml
```
