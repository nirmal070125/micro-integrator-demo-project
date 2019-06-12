# micro-integrator-demo-project

## Pre-requisites 
- Running k8s cluster with Ballerina sample - https://ballerina.io/learn/by-guide/restful-service/ running.

Use following command to build your micro-integrator docker image which contains your composite integration application. Note that `1301` below donates your image version.

```docker  build -t wso2/micro-integrator-demo:1301 .```

Update the k8s deployment with the new image;

```sed -i.bak 's#wso2/micro-integrator-demo:latest#wso2/micro-integrator-demo:1301#' k8s-deployment.yaml```

Redeploy the deployment to the k8s cluster;

```kubectl --namespace=wso2 apply -f k8s-deployment.yaml```

Invoke the service;

```curl  http://localhost:32100/myorders/orderid/100500```

`32100` is your service port which can be found via - ```kubectl get svc -n wso2```
