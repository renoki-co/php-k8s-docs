# Table of contents

* [๐ข Introduction](README.md)
* [๐ Support](support.md)

## Getting Started

* [๐ Installation](getting-started/installation.md)
* [๐ Showcase](getting-started/showcase.md)
* [๐ Authentication](getting-started/authentication.md)
* [๐ Default Versions](getting-started/default-versions.md)

## Cluster Interaction <a href="interacting-with-the-cluster" id="interacting-with-the-cluster"></a>

* [๐งญ Getting Started](interacting-with-the-cluster/getting-started.md)
* [๐ญ CRUD Operations](interacting-with-the-cluster/crud-operations.md)
* [๐ฆ Import from YAML](interacting-with-the-cluster/import-from-yaml.md)
* [๐ Watching Resources](interacting-with-the-cluster/watching-resources.md)

## Resources

* [๐ Base Resource](resources/base-resource/README.md)
  * [Attributes Methods](resources/base-resource/attributes-methods-1.md)
  * [Metadata Methods](resources/base-resource/attributes-methods.md)
  * [Custom Callers](resources/base-resource/cluster-methods.md)
* [๐ง Namespace](resources/namespace.md)
* [๐ฅ Node](resources/node.md)
* [๐ก Event](resources/event.md)
* [๐ฆ Workloads](resources/workloads/README.md)
  * [Pod](resources/workloads/pod.md)
  * [Deployment](resources/workloads/deployment.md)
  * [StatefulSet](resources/workloads/statefulset.md)
  * [DaemonSet](resources/workloads/daemonset.md)
  * [Job](resources/workloads/job.md)
  * [CronJob](resources/workloads/cronjob.md)
* [๐งต Configurations](resources/configurations/README.md)
  * [ConfigMap](resources/configurations/configmap.md)
  * [Secret](resources/configurations/secrets.md)
* [๐ Storage](resources/storage/README.md)
  * [StorageClass](resources/storage/storageclass.md)
  * [PersistentVolume](resources/storage/persistentvolume.md)
  * [PersistentVolumeClaim](resources/storage/persistentvolumeclaim.md)
* [๐ถ Networking](resources/networking/README.md)
  * [Service](resources/networking/service.md)
  * [Ingress](resources/networking/ingress.md)
* [โ Scaling & Availability](resources/scaling-and-availability/README.md)
  * [HorizontalPodAutoscaler](resources/scaling-and-availability/horizontalpodautoscaler.md)
  * [PodDisruptionBudget](resources/scaling-and-availability/poddisruptionbudget.md)
* [๐ RBAC](resources/rbac/README.md)
  * [ClusterRole](resources/rbac/cluster-role.md)
  * [ClusterRoleBinding](resources/rbac/clusterrolebinding.md)
  * [Role](resources/rbac/role.md)
  * [RoleBinding](resources/rbac/rolebinding.md)
  * [ServiceAccount](resources/rbac/service-account.md)

## Instances

* [Affinity](instances/affinity.md)
* [Container](instances/container.md)
* [Container Probes](instances/container-probes.md)
* [Expressions](instances/expressions.md)
* [Resource Metrics](instances/resource-metrics.md)
* [RBAC Rules](instances/rules.md)
* [Volumes](instances/volumes.md)

## Advanced

* [๐ฐ Macros](advanced/macros.md)
* [โจ Create classes for CRDs](advanced/create-classes-for-crds/README.md)
  * [๐ Getting started](advanced/create-classes-for-crds/getting-started.md)
  * [๐ฐ Macros](advanced/create-classes-for-crds/macros.md)
  * [๐ Watchable Resources](advanced/create-classes-for-crds/watchable-resources.md)
  * [โ Scalable Resources](advanced/create-classes-for-crds/scalable-resources.md)
  * [๐ Podable Resources](advanced/create-classes-for-crds/podable-resources.md)
  * [๐ Loggable Resources](advanced/create-classes-for-crds/loggable-resources.md)
  * [๐ Helper Traits](advanced/create-classes-for-crds/helper-traits.md)

## Frameworks

* [Laravel](frameworks/laravel.md)
* [PHP Helm](frameworks/php-helm.md)
