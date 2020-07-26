# Liveness Probes

```
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: myfrontend
      image: nginx
      ports:
        - containerPort: 8080
      volumeMounts:
      - mountPath: "/var/www/html"
        name: mypd
        
+ livenessProbe:
+   httpGet:
+     path: /api/ready
+     port: 8080
      
  volumes:
    - name: mypd
      persistentVolumeClaim:
        claimName: myclaim
        
```
        