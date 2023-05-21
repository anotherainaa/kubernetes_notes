Usually it's made up of 3 components
- metadata
  - stuff about the component such as the name
- specs
  - specification of the componenet
- status
  - it's how k8s knows whether something is as it should be or not
  - the basis of the self healing feature of k8s.
  - e.g replicas 2, the status of deployment and compare the status and specification
  - the status information comes from etcd. k8s checks whether status and desired state/specification are matching and will react accordingly


Example of a manifest
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  ports: 80
```


