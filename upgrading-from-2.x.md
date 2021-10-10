# ⏫ Upgrading to 3.x

### Authentication changes

This major update comes with authentication changes thanks to [Kévin Dunglas](https://github.com/renoki-co/php-k8s/pull/117)' initial thoughts on the [Kubeconfig environment variable authentication PR](https://github.com/renoki-co/php-k8s/pull/117) and how it should be changed.

```php
use RenokiCo\PhpK8s\KubernetesCluster;

// 2.x method
$cluster = new KubernetesCluster('http://127.0.0.1:8080');
$cluster = (new KubernetesCluster(...))->fromKubeConfigVariable('context-name');
$cluster = (new KubernetesCluster(...))->fromKubeConfigYamlFile('/.kube/config', 'context-name');
$cluster = (new KubernetesCluster(...))->inClusterConfiguration();

// 3.x method
$cluster = KubernetesCluster::fromUrl('http://127.0.0.1:8080');
$cluster = KubernetesCluster::fromKubeConfigVariable('context-name');
$cluster = KubernetesCluster::fromKubeConfigYamlFile('/.kube/config', 'context-name');
$cluster = KubernetesCluster::inClusterConfiguration();

// Example on using the $cluster method.
foreach ($cluster->getAllPods() as $pod) {
    //
}
```

For the `fromUrl` method, you can still call the `->withToken()` and other authentication options as described in the [authentication section](getting-started/authentication.md).

```php
$cluster = KubernetesCluster::fromUrl('http://127.0.0.1:8080')
    ->withToken('ey...')

$cluster->withToken('ey...')
    ->withCertificate($pathToCert)
    ->withPrivateKey($pathToKey);

$pods = $cluster->getAllPods();
```

### PHP DocBlocks for `KubernetesCluster`

The `RenokiCo\PhpK8s\KubernetesCluster` now has proper annotations for all of the proxied methods, like `getAllPods()` or `getAllConfigmapsFromAllNamespaces()`.

Your IDE should now be able to properly hint you the callable methods while you type them.

### Codebase Cleanup

After a while, the codebase became a bit unorganized, so there were some actions taken:

* The resource-ready traits, like `CanScale` or `HasName` were moved from `RenokiCo\PhpK8s\Traits` to `RenokiCo\PhpK8s\Traits\Resource`
* Multiple classes, especially `K8s` and `KubernetesClient` now implements the code in traits to avoid very long files with mixed functionalities.
