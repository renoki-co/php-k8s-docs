# Resource Metrics

### Resource Metrics

```php
$cpuMetric = K8s::metric()->cpu()->averageUtilization(70);

$memoryMetric = K8s::metric()->memory()->averageValue('512Mi');
```

### Value Types

#### Average Utilization (`Utilization`)

```php
$metric = K8s::metric()->cpu()->averageUtilization(70);
```

#### Average Value (`AverageValue`)

```php
$metric = K8s::metric()->cpu()->averageValue(70);
```

#### Value (`AverageValue`)

```php
$metric = K8s::metric()->cpu()->value(70);
```

### Object Resource

```php
$svcMetric = K8s::object()
    ->setResource($service)
    ->setMetric('packets-per-second')
    ->averageValue('1k');
```
