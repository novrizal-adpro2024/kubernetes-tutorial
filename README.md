# Module 11: Deployment on Kubernetes

> #### Novrizal Airsyahputra - 2206081780 - Advance Programming B

---
**1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?**

**ANS:**

From the logs, it's evident that prior to exposing the application as a service, it was accessed directly within the pod. The logs display initial messages (such as "start server HTTP on port 8080") and each incoming request (GET /). Each time the application is accessed within the pod, a log entry is created for that request. After turning the application into a service using minikube service hello-node, the logs continue to show the initial messages and incoming requests as before. However, now the application is accessed through the service, which forwards traffic to the pod. Accessing the application through the service enables external access to the application, while accessing it within the pod remains more internal within the Kubernetes cluster.
![1](assets/images/1.jpeg)

**2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?**

**ANS:** 

The -n option in the kubectl get command is used to specify the namespace from which resources will be displayed. If the -n option is not included, kubectl get will display resources from the default namespace. In subsequent calls, kubectl get is used with the -n kube-system option, instructing it to specifically display resources from the kube-system namespace. This namespace contains system components and infrastructure of Kubernetes itself, such as core system services like DNS, API server, and Kubernetes dashboard.