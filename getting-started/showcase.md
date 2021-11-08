# 🙌 Showcase

Consider the following YAML configuration for a Service kind:&#x20;

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx
  namespace: frontend
spec:
  selector:
    app: frontend
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

With PHP K8s, you can write it into a more OOP manner:&#x20;

```php
use RenokiCo\PhpK8s\KubernetesCluster;

// Create a new instance of KubernetesCluster.
$cluster = new KubernetesCluster('http://127.0.0.1:8080');

// Create a new NGINX service.
$svc = $cluster->service()
    ->setName('nginx')
    ->setNamespace('frontend')
    ->setSelectors(['app' => 'frontend'])
    ->setPorts([
        ['protocol' => 'TCP', 'port' => 80, 'targetPort' => 80],
    ])
    ->create();
```
