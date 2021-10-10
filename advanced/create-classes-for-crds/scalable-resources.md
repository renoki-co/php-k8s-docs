# ↔ Scalable Resources

Scalable resources need a custom API on which you can call scale operations. Usually, this is done for resources that open a `/scale` endpoint to the API.

On the default resources, this is applied to StatefulSets and [Deployments](../../resources/workloads/deployment.md#scaling).

```php
use RenokiCo\PhpK8s\Contracts\InteractsWithK8sCluster;
use RenokiCo\PhpK8s\Contracts\Scalable;
use RenokiCo\PhpK8s\Kinds\K8sResource;
use RenokiCo\PhpK8s\Traits\CanScale;

class GameServerSet extends K8sResource implements InteractsWithK8sCluster, Scalable
{
    use CanScale;
}
```

```php
$gameServerSet->scale(3);
```
