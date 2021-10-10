# Attributes Methods

### `getAttribute($name, $default)`

Get an attribute. If it does not exist, return a `$default`. Supports dot notation for nested fields.

```php
$configmap->getAttribute('data', []);
```

```php
$configmap->getAttribute('data.key', '');
```

### `setAttribute($name, $value)`

Sets an attribute to the configuration. Supports dot notation for nested fields.

```php
$configmap->setAttribute('data', ['key' => 'value']);
```

```php
$volume->setAttribute('spec.mountingOptions', ['debug']);
```

For the `spec.*` paths, please consider using `->setSpec()` and `->getSpec()`:

```php
$volume->setSpec('mountingOptions', ['debug']);
```

### `removeAttribute($name)`

Remove an attribute from the configuration. Supports dot notation for nested fields.

```php
$configmap->removeAttribute('data');
```

```php
$storageClass->removeAttribute('parameters.iopsPerGB');
```

### `addToAttribute($name, $element)`

Append an `$element` to the `$name` attribute in an instance. For example, it might be an array of `rules` like the RBAC Rules instance has:

```php
$rule->addToAttribute('rules', 'some-rule')
    ->addToAttribute('rules', 'another-rule');

// rules: ['some-rule', 'another-rule']
```
