# 🔒 Authentication

For authentication and cluster interaction, a `KubernetesCluster` class is provided. In the showcase, you have been shown how to initialize a Kubernetes Cluster instance when the method is `kubectl proxy`-supported.

```php
use RenokiCo\PhpK8s\KubernetesCluster;

$cluster = new KubernetesCluster('http://127.0.0.1:8080');
```

As an argument, you can pass any Kubernetes endpoint towards your cluster:

```php
use RenokiCo\PhpK8s\KubernetesCluster;

$cluster = new KubernetesCluster(
    'https://cluster-id.api.k8s.fr-par.scw.cloud:6443'
);
```

Further to this page, you will find some ways to authenticate to your cluster.

### Bearer Token

The simplest way is to attach a bearer token to the request:

```php
$cluster->withToken($token);
```

You can also attach a token from a file path:

```php
$cluster->loadTokenFromFile($path);
```

### HTTP authentication header

In case you have a username-password HTTP authentication, the underlying code will make it accessible for you:

```php
$cluster->httpAuthentication($user, $password);
```

### In-Cluster

Kubernetes allows Pods to access [the internal kubeapi within a container](https://kubernetes.io/docs/tasks/run-application/access-api-from-pod/). Each pod that runs in a Cluster has a token and a CA certificate injected at a specific location. The package will recognize the files and will apply the token and the CA accordingly.

Please keep in mind that this works only within pods that run in a Kubernetes cluster.

```php
$cluster->inClusterConfiguration();

foreach ($cluster->getAllServices() as $svc) {
    //
}
```

### Authenticating with kubeconfig file

You may call `fromKubeConfigYamlFile` method to specify the cluster to be authenticated with the given kubeconfig path and use the passed context:

```php
$cluster->fromKubeConfigYamlFile('/.kube/config', 'context-name');
```

### `KUBECONFIG` environment variable

**Available from: 2.12+**

Instead of passing a single kubeconfig file with `fromKubeConfigYamlFile`, you may use the `KUBECONFIG` variabile. This variable [is defined in the specs](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/#set-the-kubeconfig-environment-variable) as holding multiple paths to different kubeconfig files. From all the paths, PHPK8s will merge all kubeconfig files and will use the specified.

```php
$cluster->fromKubeConfigVariable('context-name');
```

### SSL/TLS Support

Besides the authentication, you might want to pass SSL data for the API requests:

```php
$cluster->withCertificate($pathToCert)->withPrivateKey($pathToKey);
```

If you have a CA certificate, you might also want to pass it:

```php
$cluster->withCaCertificate($pathToCA);
```

For testing purposes or local checkups, you can disable SSL checks. This will disable peer verification:

```php
$cluster->withoutSslChecks();
```
