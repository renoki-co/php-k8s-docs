# 🎭 CRUD Operations

### Retrieving all resources

Getting all resources can be done by calling `->all()`:

```php
$namespaces = $cluster->namespace()->all();

// Or you can use a specific method to call it at once
$namespaces = $cluster->getAllNamespaces();

// For namespaced resources, you may pass the namespace
$stagingServices = $cluster->getAllServices('staging');
```

The result is an `RenokiCo\PhpK8s\ResourcesList` instance. The class is extending `\Illuminate\Support\Collection`, on which you can chain various methods as described here: [https://laravel.com/docs/master/collections](https://laravel.com/docs/master/collections)

### **Retrieving all resources from all namespaces**

Retrieving all resources from all namespaces can also be done using the `allNamespaces()` method:

```php
$allPods = $cluster->pod()->allNamespaces();

// Or you can use the specific method:
$allPods = $cluster->getAllPodsFromAllNamespaces();
```

**For the specific method, the format should be `getAll[Resource]FromAllNamespaces()`**

### Retrieving a specific resource

Getting only one resource is done by calling `->get()`:

```php
$service = $cluster->service()->whereNamespace('staging')->whereName('nginx')->get();

// You can also shorten it like
$service = $cluster->service()->whereNamespace('staging')->getByName('nginx');

// Or you can use a specific method to call it in at once
$service = $cluster->getServiceByName('nginx', 'staging');
```

**Filters can vary, depending if the resources are namespaceable or not. By default, the namespace is `default` and can be missed from the function call.**

### Creating resources

Calling the `->create()` method after building your Kind will create the resource in your cluster. In fact, it will actually sync it to the Cluster as Kubernetes uses the resource names as identifiers.

```php
$ns = $cluster->namespace()->setName('staging')->create();

$ns->isSynced(); // true
```

### Updating resources

While Kubernetes has the ability to PATCH a resource or REPLACE it entirely, PHP K8s relies on REPLACE to update your resource since you have to retrieve it first (thus getting a synced class), edit it, then triggering the update.

```php
$cm = $cluster->getConfigmapByName('env');

$cm->addData('API_KEY', '123')->update();
```

### Deleting resources

You will have to simply call `->delete()` on the resource, after you retrieve it.

```php
$cm = $cluster->getConfigmapByName('settings');

if ($cm->delete()) {
    echo 'Configmap deleted! 🎉';
}
```

Additionally, you can pass query parameters, grace period, and the propagation policy if needed:

```php
public function delete(
    array $query = ['pretty' => 1],
    $gracePeriod = null,
    string $propagationPolicy = 'Foreground'
) {
    //
}
```

### Creating or updating resources

Sometimes, you want to create a resource if it's not existent or update it with the current resource class info. You can do this in one chain call:

```php
$cluster->configmap()
    ->addData('RAND', mt_rand(0, 999))
    ->createOrUpdate();
```

Each time the above code is running, it will create the ConfigMap if it's not existent, or it will update the existent one with a random number between 0 and 999.
