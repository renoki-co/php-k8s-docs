# Service

Default version: `v1`

* [Official Documentation](https://kubernetes.io/docs/concepts/services-networking/service/)

### Example

```php
$svc = $this->cluster
    ->service()
    ->setName('nginx')
    ->setLabels(['tier' => 'backend'])
    ->setSelectors(['app' => 'frontend'])
    ->setPorts([
        ['protocol' => 'TCP', 'port' => 80, 'targetPort' => 80],
    ])
    ->create();
```

