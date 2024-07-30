| Workload Resource                | Description                                                              | Use Case                                        |
|----------------------------------|--------------------------------------------------------------------------|-------------------------------------------------|
| Pod                              | Smallest, simplest Kubernetes object                                     | Running a single/multiple tightly coupled containers |
| ReplicaSet                       | Ensures specified number of identical pods                               | Maintaining stable set of replicas              |
| Deployment                       | Manages ReplicaSets, provides declarative updates                        | Stateless apps, microservices, updates          |
| StatefulSet                      | Manages stateful applications, ordered, unique pods                      | Databases, distributed stateful apps            |
| DaemonSet                        | Ensures a copy of a pod runs on all/some nodes                           | Node-specific daemons, log collection, monitoring |
| Job                              | Creates pods to ensure completion                                        | Batch processing, data processing, one-time tasks |
| CronJob                          | Manages time-based jobs                                                  | Periodic tasks like backups, report generation  |
| ReplicationController            | Ensures specified number of pod replicas                                 | Similar to ReplicaSet, but less commonly used   |
| Horizontal Pod Autoscaler (HPA)  | Scales pods based on resource usage metrics                              | Dynamically adjust pod count                    |
| Vertical Pod Autoscaler (VPA)    | Adjusts resource limits/requests based on usage                          | Ensuring proper CPU/memory resources            |