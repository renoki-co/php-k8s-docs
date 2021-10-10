---
description: Just a simple port of renoki-co/php-k8s for easier access in Laravel.
---
# Laravel

[![CI](https://github.com/renoki-co/laravel-php-k8s/workflows/CI/badge.svg?branch=master)](https://github.com/renoki-co/laravel-php-k8s/workflows/CI/badge.svg?branch=master) [![codecov](https://camo.githubusercontent.com/55dab7191c468d5832aa75143d92d02cd0d46a92e5849a961b2e89315b506ae9/68747470733a2f2f636f6465636f762e696f2f67682f72656e6f6b692d636f2f6c61726176656c2d7068702d6b38732f6272616e63682f6d61737465722f67726170682f62616467652e737667)](https://codecov.io/gh/renoki-co/laravel-php-k8s/branch/master) [![StyleCI](https://camo.githubusercontent.com/199bf5b58d59e7ecdd86a73d81a15351abbe0cb416ae77ac7c929d1fbe447130/68747470733a2f2f6769746875622e7374796c6563692e696f2f7265706f732f3330373639363837382f736869656c643f6272616e63683d6d6173746572)](https://github.styleci.io/repos/307696878) [![Latest Stable Version](https://camo.githubusercontent.com/f180b19a74da8d9d14ed4e10e896a3deb939ae4d3dbd052963e62b513c06fcc2/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f6c61726176656c2d7068702d6b38732f762f737461626c65)](https://packagist.org/packages/renoki-co/laravel-php-k8s) [![Total Downloads](https://camo.githubusercontent.com/e07ac5d59d264269bd89242a27dc8d5e1d0b8fc248278a79a63e1cb6c46a314a/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f6c61726176656c2d7068702d6b38732f646f776e6c6f616473)](https://packagist.org/packages/renoki-co/laravel-php-k8s) [![Monthly Downloads](https://camo.githubusercontent.com/551bfbfacf175a2447ef70fcab2c1a10a3964f24b98aa014db844bd0c04dd908/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f6c61726176656c2d7068702d6b38732f642f6d6f6e74686c79)](https://packagist.org/packages/renoki-co/laravel-php-k8s) [![License](https://camo.githubusercontent.com/ee06244d0939ca475b81b5b69b3bbef7bd6340e735fa2e8b27de101c7b8200d1/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f6c61726176656c2d7068702d6b38732f6c6963656e7365)](https://packagist.org/packages/renoki-co/laravel-php-k8s)

### 🚀 Installation

You can install the package via composer:

```bash
composer require renoki-co/laravel-php-k8s
```

Publish the config:

```bash
php artisan vendor:publish --provider="RenokiCo\LaravelK8s\LaravelK8sServiceProvider" --tag="config"
```

### 🙌 Usage

The cluster configuration can be found in the `config/k8s.php` file. You can get started directly with the `/.kube/config` file you already have.

```php
use RenokiCo\LaravelK8s\LaravelK8sFacade as K8s;

foreach (K8s::getAllConfigMaps() as $cm) {
    // $cm->getName();
}
```

For further documentation, check [renoki-co/php-k8s](https://github.com/renoki-co/php-k8s).

### Multiple connections

The package supports multiple connections configurations. If you wish to select a specific one (not the default one), call `connection` before getting the cluster.

```php
use RenokiCo\LaravelK8s\LaravelK8sFacade as K8s;

$cluster = K8s::connection('http')->getCluster();
```

### Getting the cluster instance

You can also call `getCluster()` to get the instance of `\RenokiCo\PhpK8s\KubernetesCluster`:

```php
$cluster = K8s::getCluster();
```
