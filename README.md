# enos-serverless-function
This is the sample codes to create a serverless function and trigger in EnOS.

## Techology stack
- NodeJS
- EnOS Platform

## Prerequitsites

### Get the Kafka broker url 1 & 2, port, topic and consumer group id, save to .env file
This can be only obtained during the initial EnOS deployment.

### Create a serverless function
Follow the instructions below to create a serverless function:
- https://www.envisioniot.com/docs/app-development/en/latest/shc/howto/serverless/managing_function.html#creating-a-function-application

### Copy and paste index.js, package.json in the inline code editor of the serverless function
Follow the instructions below to copy and paste the codes.
- https://www.envisioniot.com/docs/app-development/en/latest/shc/howto/serverless/managing_function.html#editing-the-code-online

### Create a ConfigMap for the serverless function
Follow the instructions below to create a ConfigMap:
- https://www.envisioniot.com/docs/app-development/en/latest/shc/howto/container/configuring_configmap_secret.html#creating-a-config-map
- The key for the ConfigMap: .env
- The value for the ConfigMap: The key value pairs in the config/.env file

### Build & Publish the serverless function
Follow the instructions below to build and publish the serverless function
- https://www.envisioniot.com/docs/app-development/en/latest/shc/howto/serverless/managing_function.html#building-and-publishing-the-function-application
- Add the created ConfigMap.
- Mount Path: /home/app/config
- File Path: .env

### Add a trigger method - Kafka
- A Kafka cluster has to be configured during the EnOS deployment. Check with the infra team.
- Kafka topic: the topic specified in the .env file
- Kafka group id: the group id specified in the .env file
- API to trigger: /callback (See the callback api in index.js)

## How to run

### Test the trigger
- Invoke the /trigger api (See the trigger api in index.js)
- Go to the container pod and observe logs for callback triggered response