# 🎇 Getting started

Each CRD must extend the `K8sResource` class. This will provide the base PHP API functionalities that you can work with your resource.

Additionally, to be able to interact with the cluster and actually perform operations on it, you should implement the `InteractsWithK8sCluster` interface.

The following example will create an `IngressRoute` CRD-ready class for `traefik.containo.us/v1alpha1`:

```php
use RenokiCo\PhpK8s\Contracts\InteractsWithK8sCluster;
use RenokiCo\PhpK8s\Kinds\K8sResource;

class IngressRoute extends K8sResource implements InteractsWithK8sCluster
{
    /**
     * The resource Kind parameter.
     *
     * @var null|string
     */
    protected static $kind = 'IngressRoute';

    /**
     * The default version for the resource.
     *
     * @var string
     */
    protected static $defaultVersion = 'traefik.containo.us/v1alpha1';

    /**
     * Wether the resource has a namespace.
     *
     * @var bool
     */
    protected static $namespaceable = true;
}
```

```php
$ir = new IngressRoute($cluster, [
    'spec' => [
        'entryPoints' => ...
    ],
]);

$ir->create();
```

**For non-namespaceable resources, you shall set the `$namespaceable` variable to `false`.**
