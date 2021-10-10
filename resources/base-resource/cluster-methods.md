# Custom Callers

In case some of the methods you want to use does not exist in the docs, you can call `getSomething($default)` or `setSomething($value)`, which will set or get attributes from the object.

This applies to any class from both `RenokiCo\PhpK8s\Kinds\*`  and `RenokiCo\PhpK8s\Instances\*` .

For example, the `K8sPod` instance associated with the Pod resource does not implement any `nodeSelector` function, but you can call it anyway:

```php
$pod->setNodeSelector(['type' => 'spot']);

$pod->getNodeSelector([]); // defaults to [] if not existent
```
