Create a **Persistent Volume** called log-volume. It should make use of a storage class name manual.
It should use RWX as the access mode and have a size of 1Gi. The volume should use the hostPath
 /opt/volume/nginx

Next, create a **PVC** called log-claim requesting a minimum of 200Mi of storage.
 This PVC should bind to log-volume.

Mount this in a **pod** called logger at the location /var/www/nginx.
 This pod should use the image nginx:alpine.
 
### PersistentVolume with hostPath 
<pre>
apiVersion: v1
kind: PersistentVolume
metadata:
  name: log-volume
spec:
  capacity:
    storage: 1Gi
  accessModes:
  - ReadWriteMany
  storageClassName: manual
  hostPath:
    path: /opt/volume/nginx
</pre>

### PersistentVolumeClaim
<pre>
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: log-claim
spec:
  accessModes:
    - ReadWriteMany
  resources:
    requests:
      storage: 200Mi
  storageClassName: manual
</pre>

### Pod
<pre>
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: logger
  name: logger
spec:
  volumes:
    - name: log-claim
      persistentVolumeClaim:
        claimName: log-claim
  containers:
  - image: nginx:alpine
    name: logger
    volumeMounts:
      - name: log-claim
        mountPath: /var/www/nginx
</pre>
