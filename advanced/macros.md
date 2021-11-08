# 🏰 Macros

Besides the custom callers to call for custom attributes, you may also define your own custom functions, without extending or overwriting classes, using [Macros](https://tighten.co/blog/the-magic-of-laravel-macros/).

In case you are not familiar with Macros, you can see the following example on defining a custom function for the `K8sPod` instance.

```php
use RenokiCo\PhpK8s\Kinds\K8sPod;

// changeDnsPolicy() does not exist in the code

K8sPod::macro('changeDnsPolicy', function ($policy = 'None') {
    return $this->setSpec('dnsPolicy', $policy);
});

$pod->changeDnsPolicy('ClusterFirst');
```

**`$this` keyword used within the closure is going to reference the current K8sPod object in this example. You might as well define how many macros you want. The closure can also contain parameters or no parameters at all, based on your needs.**

Macros also work with custom callers:

```php
use RenokiCo\PhpK8s\Kinds\K8sPod;

K8sPod::macro('changeMetadata', function (array $metadata) {
    return $this->setMetadata($metadata);
});

$pod->changeMetadata(['name' => 'mysql']);
```

To initialize the resources from within the cluster, define a macro for `K8s` class.

If you have new resources to initialize, you should define a macro for the `K8s` class, so that whenever you call it from a cluster object, you will be able to interact with it within the cluster.

For example, for an [Agones Fleet](https://agones.dev/site/docs/reference/fleet), that is a custom third-party CRD and is not supported by this package, but can be initialized from the cluster object:

```php
use RenokiCo\PhpK8s\K8s;

K8s::macro('agonesFleet', function ($cluster = null, array $attributes = []) {
    return new Kinds\MyAgonesFleet($cluster, $attributes);
});

foreach ($cluster->agonesFleet()->all() as $fleet) {
    //
}
```
