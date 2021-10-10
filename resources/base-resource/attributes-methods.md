# Metadata Methods

### Namespace

#### `getNamespace()`

Get the namespace the resource is in. This usually works only for namespaceable resources.

```php
$service->getNamespace();
```

#### `setNamespace($namespace)`

Set the namespace for the resource, if namespaceable. This usually works only for namespaceable resources.

```php
$service->setNamespace('staging');
```

The namespace also accepts a `K8sNamespace` class:

```php
$ns = $cluster->getNamespaceByName('staging');

$service->setNamespace($ns);
```

#### `whereNamespace($namespace)`

Alias for [setNamespace($namespace)](attributes-methods.md#setnamespace-usdnamespace)

It's just a naming convention for better filters on the get methods.

### Names

#### `setName($name)`

Set the name of the resource.

```php
$service->setName('nginx');
```

#### `getName()`

Get the name of a resource.

```php
$namespace->getName();
```

#### `whereName($name)`

Alias for [setName($name)](attributes-methods.md#setname-usdname). It's just a naming convention for better filters on get.

### Labels

#### `setLabels(array $labels)`

Set the labels of the resource.

```php
$service->setLabels(['tier' => 'backend']);
```

#### `getLabels()`

Get the labels of a resource.

```php
$service->getLabels();
```

#### `getLabel($name, $default = null)`

Get the label value by key. Defaults to null.

```php
$service->getLabel('tier'); // "backend"
$service->getLabel('not-a-label'); // null
```

#### `setOrUpdateLabels(array $labels)`

Set or update the labels. The method used will be merge.

```php
$service->setOrUpdateLabels([
    'tier' => 'backend'
    'some-other-label' => 'test',
]);
```

### Annotations

#### `setAnnotations(array $annotations)`

Set the annotations for the resource.

```php
$service->setAnnotations(['kubernetes.io/some-annotation' => 'yes']);
```

#### `getAnnotations()`

Get the annotations of a resource.

```php
$service->getAnnotations();
```

#### `getAnnotation($name, $default = null)`

Get the annotation value by key. Defaults to null.

```php
$service->getAnnotation('kubernetes.io/some-annotation'); // "yes"
$service->getAnnotation('kubernetes.io/non-existing-annotation'); // null
```

#### `setOrUpdateAnnotations(array $annotations)`

Set or update the annotations. The method will be merging existing annotations with the ones passed via the function argument.

```php
$service->setOrUpdateAnnotations([
    'kubernetes.io/some-annotation' => 'yes'
    'kubernetes.io/some-otherannotation' => 'yes',
]);
```

#### `getApiVersion()`

Get the resource API version.

```php
$namespace->getApiVersion();
```

#### `getKind()`

Get the resource's Kind. This method is called statically.

```php
$kind = $namespace::getKind();
```

#### `setDefaultVersion()`

Set at runtime the default version that will be used for the resource.

```php
use RenokiCo\PhpK8s\Kinds\K8sDeployment;

// instead of default apps/v1
K8sDeployment::setDefaultVersion('apps/v2beta1');
```

#### `setDefaultNamespace()`

Set at runtime the default namespace that will be used for the resource.

```php
use RenokiCo\PhpK8s\Kinds\K8sDeployment;

K8sDeployment::setDefaultNamespace('staging'); // instead of "default"
```

To set the default namespace for all resources, you might want to use `K8sResource` instead:

```php
use RenokiCo\PhpK8s\Kinds\K8sResource;

K8sResource::setDefaultNamespace('staging');
```

Now all resources will interact with the `staging` namespace by default.

### Transformers

#### `toArray()`

Get the resource as an array.

```php
$array = $namespace->toArray();
```
