# mock-greeting-provider project
This is a simple mock provider, it includes only one endpoint and requires no further setup.

It receives a request from the mock-greetings-resource and replies with a greeting.

It contains a simple jaeger instrumentation.


## Running on Kubernetes.
Use the Dockerfile.jvm to build an image and deploy the container on kubernetes.

Create a single service that points to 8080 as this is the open port, please note that the entrypoint should be as follows http://greetings-service-provider:8084 this will allow the greetings-service to connect to it.

Remember to annotate the deployment with "sidecar.jaegertracing.io/inject": "true"

it should look something like this.
apiVersion: apps/v1
kind: Deployment
metadata:
name: mock-greetings-resource
annotations:
"sidecar.jaegertracing.io/inject": "true" #