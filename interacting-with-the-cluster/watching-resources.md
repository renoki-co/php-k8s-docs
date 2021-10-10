# 👀 Watching Resources

### Watch Resource

**The ability to watch the Pods logs is also available and can be seen in the **[**Pod Documentation**](../resources/workloads/pod.md)****

The package comes with a PHP-native way to be able to track the changes via the Kubernetes cluster's Watch API.

You can watch the resource directly from the Resource class, and check & process your logic inside a closure. See more on [Kubernetes Documentation](https://kubernetes.io/docs/reference/using-api/api-concepts/#efficient-detection-of-changes).

### Watching a specific resource

```php
$cluster->pod()->watchByName('mysql', function ($type, $pod) {
    $resourceVersion = $pod->getResourceVersion();

    return true;
});
```

**The watch closures will run indefinitely until you return a `true` or `false` within the closure.**

For additional parameters like `resourceVersion`, continue passing an array of query parameters alongside the closure:

```php
$cluster->pod()->watchByName('mysql', function ($type, $pod) {
    // Waiting for a change.
}, ['resourceVersion' => $pod->getResourceVersion()]);
```

### Watching all resources

To watch all resources instead of just one, you may call `watchAll` . This time, you do not need to call any filter or retrieval, because there is nothing to filter:

```php
$cluster->pod()->watchAll(function ($type, $pod) {
    if ($pod->getName() === 'nginx') {
        // do something
    }
});
```
