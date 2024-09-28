Kubernetes provides several built-in CLI tools that are essential for monitoring and managing applications running in your cluster. These tools help you inspect the state of your resources, debug issues, and ensure the health and performance of your applications. Here are some of the most commonly used Kubernetes CLI commands for monitoring:

### 1. `kubectl get`

The `kubectl get` command lists resources in the cluster. It’s useful for getting a quick overview of the state of various resources.

- **Pods**:
  ```sh
  kubectl get pods
  ```

- **Deployments**:
  ```sh
  kubectl get deployments
  ```

- **Services**:
  ```sh
  kubectl get services
  ```

- **All resources in a namespace**:
  ```sh
  kubectl get all -n <namespace>
  ```

### 2. `kubectl describe`

The `kubectl describe` command provides detailed information about a specific resource. It’s useful for debugging issues.

- **Pod**:
  ```sh
  kubectl describe pod <pod-name>
  ```

- **Deployment**:
  ```sh
  kubectl describe deployment <deployment-name>
  ```

- **Node**:
  ```sh
  kubectl describe node <node-name>
  ```

### 3. `kubectl logs`

The `kubectl logs` command retrieves logs from a container in a pod. It’s essential for debugging and monitoring the application’s output.

- **Logs from a single container pod**:
  ```sh
  kubectl logs <pod-name>
  ```

- **Logs from a specific container in a multi-container pod**:
  ```sh
  kubectl logs <pod-name> -c <container-name>
  ```

- **Follow logs (streaming logs)**:
  ```sh
  kubectl logs -f <pod-name>
  ```

### 4. `kubectl top`

The `kubectl top` command provides metrics about resource usage for nodes or pods. It requires the Metrics Server to be installed in the cluster.

- **Resource usage of nodes**:
  ```sh
  kubectl top nodes
  ```

- **Resource usage of pods**:
  ```sh
  kubectl top pods
  ```

### 5. `kubectl exec`

The `kubectl exec` command executes a command in a container. It’s useful for debugging and interacting with the application directly.

- **Run a command in a container**:
  ```sh
  kubectl exec -it <pod-name> -- <command>
  ```

- **Open a shell in a container**:
  ```sh
  kubectl exec -it <pod-name> -- /bin/bash
  ```

### 6. `kubectl port-forward`

The `kubectl port-forward` command forwards one or more local ports to a pod. It’s useful for accessing applications in the cluster without exposing them via a service.

- **Forward a local port to a pod**:
  ```sh
  kubectl port-forward <pod-name> <local-port>:<pod-port>
  ```

### 7. `kubectl get events`

The `kubectl get events` command lists events in the cluster, which can provide insights into what is happening, especially during troubleshooting.

- **List all events**:
  ```sh
  kubectl get events
  ```

### 8. `kubectl get endpoints`

The `kubectl get endpoints` command displays the endpoints for services, showing which pods are exposed by a service.

- **Get endpoints for a service**:
  ```sh
  kubectl get endpoints <service-name>
  ```

### Example Workflow

Here’s an example workflow for monitoring and troubleshooting a Kubernetes application:

1. **Check the status of pods**:
   ```sh
   kubectl get pods
   ```

2. **Describe a problematic pod**:
   ```sh
   kubectl describe pod <pod-name>
   ```

3. **View logs from the pod**:
   ```sh
   kubectl logs <pod-name>
   ```

4. **Check resource usage of pods**:
   ```sh
   kubectl top pods
   ```

5. **Run a command inside the pod for further debugging**:
   ```sh
   kubectl exec -it <pod-name> -- /bin/bash
   ```

6. **Forward a local port to access the application**:
   ```sh
   kubectl port-forward <pod-name> 8080:80
   ```

7. **Check cluster events for additional information**:
   ```sh
   kubectl get events
   ```

Using these built-in CLI tools, you can effectively monitor and manage your Kubernetes applications, ensuring they run smoothly and efficiently.