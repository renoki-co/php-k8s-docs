---
description: PHP Helm Processor is a process wrapper for Kubernetes' Helm v3 CLI. You can run programmatically Helm v3 commands, directly from PHP, with a simple syntax.
---
# PHP Helm

[![CI](https://github.com/renoki-co/php-helm/workflows/CI/badge.svg?branch=master)](https://github.com/renoki-co/php-helm/workflows/CI/badge.svg?branch=master) [![codecov](https://camo.githubusercontent.com/06693bbedce2fbc543fa4e8a4c194e021410aa6bb016f412639c44d1bfb8f7c2/68747470733a2f2f636f6465636f762e696f2f67682f72656e6f6b692d636f2f7068702d68656c6d2f6272616e63682f6d61737465722f67726170682f62616467652e737667)](https://codecov.io/gh/renoki-co/php-helm/branch/master) [![StyleCI](https://camo.githubusercontent.com/a0b7d9ef3dcc12bd4878267aace668269f129e7aa9e344f0b90f75548a1c40a6/68747470733a2f2f6769746875622e7374796c6563692e696f2f7265706f732f3332333434353235302f736869656c643f6272616e63683d6d6173746572)](https://github.styleci.io/repos/323445250) [![Latest Stable Version](https://camo.githubusercontent.com/60aca0864db127db5f670af7a3b4e0adfc7a72a8769c092afc3a5e4c9fcef8d5/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d68656c6d2f762f737461626c65)](https://packagist.org/packages/renoki-co/php-helm) [![Total Downloads](https://camo.githubusercontent.com/7601ec723837f0cb95543457984963024182abaa586930f31825053b8428e5ba/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d68656c6d2f646f776e6c6f616473)](https://packagist.org/packages/renoki-co/php-helm) [![Monthly Downloads](https://camo.githubusercontent.com/d85b4142d404584d04dda005a63dd25e92cf758805a3abcba48289ec16671731/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d68656c6d2f642f6d6f6e74686c79)](https://packagist.org/packages/renoki-co/php-helm) [![License](https://camo.githubusercontent.com/18d749426f702eb315e4d8cccb87f25f6ea2673389a7bd19c69f1ab1c6307bd7/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d68656c6d2f6c6963656e7365)](https://packagist.org/packages/renoki-co/php-helm)

PHP Helm Processor is a process wrapper for Kubernetes' Helm v3 CLI. You can run programmatically Helm v3 commands, directly from PHP, with a simple syntax.

### 🚀 Installation

You can install the package via composer:

```
composer require renoki-co/php-helm
```

For Laravel, you may Publish the config:

```bash
php artisan vendor:publish --provider="RenokiCo\PhpHelm\PhpHelmServiceProvider" --tag="config"
```

### 🙌 Usage

```php
use RenokiCo\PhpHelm\Helm;

$helm = Helm::repoAdd(
    'add',
    'stable',
    'https://charts.helm.sh/stable'
);

$helm->run();

// The process is based on symfony/process
echo $helm->getOutput();
```

### Flags & Environment Variables

You might want to pass flags to the commands:

```php
use RenokiCo\PhpHelm\Helm;

$helm = Helm::repoAdd(
    'stable',
    'https://charts.helm.sh/stable',
    ['--no-update' => true]
);

$helm->run();
```

A third parameter is used for envs:

```php
use RenokiCo\PhpHelm\Helm;

$helm = Helm::repoAdd(
    'stable',
    'https://charts.helm.sh/stable',
    ['--no-update' => true],
    ['SOME_ENV' => '1234']
);

$helm->run();
```

### Add Repo

```php
use RenokiCo\PhpHelm\Helm;

$helm = Helm::addRepo('stable', 'https://charts.helm.sh/stable', [
    '--no-update' => true,
    '--debug' => true,
]);

$helm->run();
```

### Install/Upgrade Release

```php
use RenokiCo\PhpHelm\Helm;

$helm = Helm::install('my-release', 'stable/postgres');

$helm->run();
```

```php
use RenokiCo\PhpHelm\Helm;

$helm = Helm::upgrade('my-release', 'stable/postgres');

$helm->run();
```

### Specifying Binary Path

You can call it once to set the path to the binary to the `helm` cli:

```php
use RenokiCo\PhpHelm\Helm;

Helm::setHelmPath('/usr/bin/my-path/helm');
```

For Laravel, you might simply publish the config and set the `HELM_PATH` env variable:

```
HELM_PATH=/usr/bin/my-path/helm
```
