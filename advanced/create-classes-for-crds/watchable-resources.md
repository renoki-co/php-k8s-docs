# 👀 Watchable Resources

Watchable Resources are resources that can access the `/watch` endpoint in order to poll the changes over one or more resources. Typically, this can happen on any resource on which you can run `kubectl get some-crd --watch` upon.

For example, on basic resources (the default K8s ones), many resources like Service or Secret come with a watchable implementation.

You can read more about [how to watch a resource](../../interacting-with-the-cluster/watching-resources.md).

```php
use RenokiCo\PhpK8s\Contracts\InteractsWithK8sCluster;
use RenokiCo\PhpK8s\Contracts\Watchable;
use RenokiCo\PhpK8s\Kinds\K8sResource;

class IngressRoute extends K8sResource implements InteractsWithK8sCluster, Watchable
{
    //
}
```

Calling watch from the ingress route can be done so:

```php
(new IngressRoute($cluster))->whereName('foo')->watch(function ($type, $ir) {
    //
});
```

Or in case you created a `ingressRoute` macro:

```php
$cluster->ingressRoute()->whereName('foo')->watch(function ($type, $ir) {
    //
});
```
