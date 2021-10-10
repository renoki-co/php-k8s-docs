# 🚒 Helper Traits

Helper Traits are just PHP traits that make the boring nested variables be easier to set them, in a more friendly way.

You can find some in the [Traits folder](https://github.com/renoki-co/php-k8s/blob/master/src/Traits). By default, the `K8sResource` already uses the `HasAttributes` trait.

```php
use RenokiCo\PhpK8s\Kinds\K8sResource;
use RenokiCo\PhpK8s\Traits\HasStatus;

class GameServerSet extends K8sResource implements InteractsWithK8sCluster
{
    use HasStatus;
}
```

```php
$gameServerSet->getStatus('some.path');
```
