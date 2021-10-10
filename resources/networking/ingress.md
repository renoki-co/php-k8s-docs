# Ingress

Default version: `networking.k8s.io/v1`‌

* [Official Documentation](https://kubernetes.io/docs/concepts/services-networking/ingress/)

### Example

```php
$ingress = $this->cluster
    ->ingress()
    ->setName('nginx')
    ->setLabels(['tier' => 'backend'])
    ->setSelectors(['matchLabels' => ['app' => 'frontend']])
    ->setTls([[
        'hosts' => [
            'test.com',
        ],
        'secretName' => 'verySecretName',
    ]])
    ->setRules([[
        'host' => 'nginx.test.com',
        'http' => [
            'paths' => [[
                'path' => '/',
                'backend' => [
                    'serviceName' => 'nginx',
                    'servicePort' => 80,
                ],
            ]],
        ],
    ]])
    ->create();
```
