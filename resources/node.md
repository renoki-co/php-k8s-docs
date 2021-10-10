# 🖥 Node

Default version: `v1`

* [Official Documentation](https://kubernetes.io/docs/concepts/architecture/nodes/)

### Example

```php
$nodes = $this->cluster
    ->node()
    ->all();

foreach ($nodes as $node) {
    $node->getInfo();
    $node->getImages();
    $node->getCapacity();
    $node->getAllocatableInfo();
}
```
