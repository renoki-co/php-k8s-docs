# 📦 Import from YAML

 **For the imports to work, you will need the `ext-yaml` extension.**

If you already have YAML files or YAML as a string, you can import them into PHP K8s resource classes:

```php
$cluster->fromYaml($yamlAsString); // import using YAML as string

$cluster->fromYamlFile($yamlPath); // import using a path to the YAML file
```

The result would be a `\RenokiCo\PhpK8s\Kinds\K8sResource` instance you can call methods on.

If there are more resources in the same YAML file, like the ones separated by dashes, you will be given an array of them, representing each of their kind, in order.

**Keep in mind, the resources are not synced, since it's not known if they exist already or not. So everything you have to do is to loop through them and make sure to call `->create()` if it's needed or sync them using `->createOrUpdate()`**:

```php
$storageClasses = $cluster->fromYaml($awsStorageClassesYamlPath);

foreach ($storageClasses as $sc) {
    $sc->createOrUpdate();

    echo "{$sc->getName()} storage class got synced!";
}
```

### Import templated YAMLs

This can be really useful if you decide to use the YAML import feature with local files to fill data that is being added dynamically. You would want to define your YAMLs and use curly brackets `{}` to define variables.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: settings
data:
  key1: "{value1}"
  key2: "{value2}"
```

In your code, you would use the `fromTemplatedYamlFile` and inject the values dynamically:

```php
$cm = $cluster->fromTemplatedYamlFile('file.yaml', [
    'value1' => 'some-value-for-key-1',
    'value2' => 'some-value-for-key-2',
]);
```
