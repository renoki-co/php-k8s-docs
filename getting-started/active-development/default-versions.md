# 📗 Default Versions

Since the package supports multiple K8s Cluster versions, some versions do promote certain resources to GA. Since each resource needs a default version, the package will set **the default versions for the oldest Kubernetes version supported**.

The minimum Kubernetes version that is supported by a given package version can be found [in the project readme file, at the very top](https://github.com/renoki-co/php-k8s).  Maintainers try as hard as possible to update the Kubernetes versions that are put into test to the latest patch as often as possible.

{% hint style="warning" %}
If the package supports `v1.18+`, then the package will make sure the versions are defaults for `v1.18`. In some cases, like Ingress in `v1.19` that switched from Beta to GA, the `v1beta1` is no longer a default and instead, the `v1` is now a default. If `v1.17` is the oldest supported version, then it will stay to `v1beta`.
{% endhint %}
