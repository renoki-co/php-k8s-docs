# 🏰 Macros

[Macros](../macros.md) come in help to fix issues with the initialization of your own CRDs.

For example, instead of calling `new GameServer()` and passing the cluster for each new instance, you may create a custom caller for your resource that will automatically get the `KubernetesCluster` object injected via the `RenokiCo\PhpK8s\K8s` class:

**Starting with PHP K8s 3.1.1+ you can now define CRDs by using `register`:**

```php
use RenokiCo\PhpK8s\K8s;

Kinds\GameServer::register();

foreach ($cluster->gameServer()->all() as $gs) {
    //
}
```

As you already saw, by default, the method to call is the `camelCase` format of the class name. You may pass an argument to define the name to call by if you wish something different:

```php
use RenokiCo\PhpK8s\K8s;

Kinds\GameServer::register('gs');

foreach ($cluster->gs()->all() as $gs) {
    //
}
```
