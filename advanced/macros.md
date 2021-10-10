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
