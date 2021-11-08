# 🏰 Macros

[Macros](../macros.md) come in help to fix issues with the initialization of your own CRDs.

For example, instead of calling `new GameServer()` and passing the cluster for each new instance, you may create a custom caller for your resource that will automatically get the `KubernetesCluster` object injected via the `RenokiCo\PhpK8s\K8s` class:

```php
use RenokiCo\PhpK8s\K8s;

K8s::macro('gameServer', function ($cluster = null, array $attributes = []) {
    return new Kinds\GameServer($cluster, $attributes);
});
```

```php
foreach ($cluster->gameServer()->all() as $gs) {
    //
}
```
