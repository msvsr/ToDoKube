Create a pod called time-check in the dvl1987 namespace. This pod should run a container called time-check that uses the busybox image.

Create a config map called time-config with the data TIME_FREQ=10 in the same namespace.

The time-check container should run the command: _`while true; do date; sleep $TIME_FREQ;done`_ and write the result to the location /opt/time/time-check.log.

The path /opt/time on the pod should mount a volume that lasts the lifetime of this pod.

<pre>
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: time-check
  name: time-check
  namespace: dvl1987
spec:
  volumes:
  - name: log-volume
    emptyDir: {}
  containers:
  - image: busybox
    name: time-check
    env:
    - name: TIME_FREQ
      valueFrom:
        configMapKeyRef:
          name: time-config
          key: TIME_FREQ
    volumeMounts:
    - mountPath: /opt/time
      name: log-volume
    command:
    - "/bin/sh"
    - "-c"
    - "while true; do date; sleep $TIME_FREQ;done > /opt/time/time-check.log"
</pre>