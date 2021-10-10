# 📄 Loggable Resources

Loggable resources are resources that expose the `/log` endpoint and can easily get logs, both statically and in a polling request manner.

Check the [documentation on how to watch or get logs](../../resources/workloads/pod.md#pod-logs) for Pods.

```php
use RenokiCo\PhpK8s\Contracts\Loggable;
use RenokiCo\PhpK8s\Kinds\K8sResource;

class GameServerSet extends K8sResource implements InteractsWithK8sCluster, Loggable
{
    //
}
```

```php
$logs = $gs->logs();
```
