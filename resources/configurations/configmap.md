# ConfigMap

Default version: `v1`

* [Official Documentation](https://kubernetes.io/docs/concepts/configuration/configmap/)

### Example

```php
$cm = $this->cluster
    ->configmap()
    ->setName('certificates')
    ->setLabels(['tier' => 'backend'])
    ->setData([
        'key.pem' => '...',
        'ca.pem' => '...',
    ])
    ->create();
```

### Immutability

Starting with Kubernetes v1.21.0, ConfigMaps support immutability. If you do not specify the `immutable()` method, it will default to false:

```php
$cm = $this->cluster
    ->configmap()
    ...
    ->immutable()
    ->create();

$cm->isImmutable(); // true
```
