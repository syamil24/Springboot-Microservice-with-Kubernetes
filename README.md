# Springboot-Microservice-with-Kubernetes

- This is SpringBoot Microservices Project with Docker and Kubernetes implementation
- JDK 11 is required for this project
- No database required as we will be using H2 In memory database.
- Make sure you already installed docker and minikube(for windows)
- For Linux, its up to you which Kubernetes engined you want to install such as kubeadm etc
- Follow below steps in order to run this project inside a kubernetes cluster
```
  # Build docker image and jar file for every microservices
  # go to every services folder and run:
  mvn install
  
  #After completing all build, push the image to dockerhub as we will fetch the image from the inside the Kubernetes configuration
  docker push YOUR_USERNAME/IMAGE_NAME:YOUR_TAG
  
  # Open your terminal and go iniside K8s Config folder. (Make sure your Kubernetes is up)
  # inside every yml you can change the docker image location to yours to verify if your image is working fine
  kubectl apply -f .
  
  # Once above command executed basically you are done !!!
  # Verify the service is up by using below commands
  kubectl get all
  kubectl get pods
  kubectl get deployments
  kubectl get svc
  minikube service list 

```

- Additionally you can try to execute the expose API but need to configure port forwarding first Solution are varies, my suggestion you can try use kube-forwarder and the API will be expose to your local machine and you can test it.
- Port forwarding only for dev environment, rarely port forwarding implemented in prod. For prod implementation you can use load balancer, ingress etc.
