---
description: >-
  Control your Kubernetes clusters with this PHP-based Kubernetes client. It
  supports any form of authentication, the exec API, and it has an easy
  implementation for CRDs.
---

# 🚢 Introduction

![](.gitbook/assets/php\_k8s\_25.png)

Control your Kubernetes clusters with this PHP-based Kubernetes client. It supports any form of authentication, the exec API, and it has an easy implementation for CRDs.

For Laravel projects, you might want to use the [Laravel wrapper](frameworks/laravel.md) which eases the access for this particular case.

[![CI](https://github.com/renoki-co/php-k8s/workflows/CI/badge.svg?branch=master)](https://github.com/renoki-co/php-k8s/workflows/CI/badge.svg?branch=master) [![codecov](https://camo.githubusercontent.com/3f0b848659de3423ee1a49dfe7ec4bbf7d74f6681041edd4aa2c1f8b854cd576/68747470733a2f2f636f6465636f762e696f2f67682f72656e6f6b692d636f2f7068702d6b38732f6272616e63682f6d61737465722f67726170682f62616467652e737667)](https://codecov.io/gh/renoki-co/php-k8s/branch/master) [![StyleCI](https://camo.githubusercontent.com/908797a2f7c69f5ddde9a768d2731c8389be5c4c9385f7b033a969d7ddd3a7b0/68747470733a2f2f6769746875622e7374796c6563692e696f2f7265706f732f3235393939323532352f736869656c643f6272616e63683d6d6173746572)](https://github.styleci.io/repos/259992525) [![Latest Stable Version](https://camo.githubusercontent.com/88d3cbabd37b070b7a0560ff265151d83f5ee9d8900db78ee11016b7df06df0d/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d6b38732f762f737461626c65)](https://packagist.org/packages/renoki-co/php-k8s) [![Total Downloads](https://camo.githubusercontent.com/c9148b43923f5ad0b340edff299879dbd2f276e0c5ac8ade16439d8af110ec12/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d6b38732f646f776e6c6f616473)](https://packagist.org/packages/renoki-co/php-k8s) [![Monthly Downloads](https://camo.githubusercontent.com/fa89b52f9382a6176e7317ef14445e650f9b63376e65ca0a630d3091449feace/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d6b38732f642f6d6f6e74686c79)](https://packagist.org/packages/renoki-co/php-k8s) [![License](https://camo.githubusercontent.com/624d6036c414f936daef41789e2d365a322ff4946702b1ed32f8302ec32bd745/68747470733a2f2f706f7365722e707567782e6f72672f72656e6f6b692d636f2f7068702d6b38732f6c6963656e7365)](https://packagist.org/packages/renoki-co/php-k8s) &#x20;

[![Client Capabilities](https://camo.githubusercontent.com/ec1e14f6de963dfe599b429ad473a02bf8ce470eec9c3509f651cf17aed9d0b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4b756265726e65746573253230436c69656e742d53696c7665722d626c75652e7376673f636f6c6f72423d43304330433026636f6c6f72413d333036434538)](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/api-machinery/csi-new-client-library-procedure.md#client-capabilities) [![Client Support Level](https://camo.githubusercontent.com/8296f95e8642ef21ec0b2c17c5b35450353b6919d370ef0bb7fffbe1807104ea/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4b756265726e65746573253230436c69656e742d626574612d677265656e2e7376673f636f6c6f72413d333036434538)](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/api-machinery/csi-new-client-library-procedure.md#client-support-level)
