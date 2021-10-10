# 🧭 Getting Started

Resources are by default interacting with the API. For instance, the idea behind this is to be able to import or create, update, or delete resources, with or without YAML, by using the PHP language.

Each resource extends basic functionality from a single class: `K8sResource`. This should be used to create your own classes for unsupported kinds, like [your CRDs](../advanced/create-classes-for-crds/), for example, as it implements the needed logic to connect to your cluster.

You can perform the CRUD operations from the `KubernetesCluster` instance. Proceed further with the documentation to learn the CRUD operations, how to import existing YAML files and perform watch callbacks on your resources.
