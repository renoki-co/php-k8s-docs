# 💊 Podable Resources

Podable resources are resources that manage pods. You can easily get the pods that are running under the resource and you can control the overall pods inherited by these workload controllers.

For example, Jobs and DaemonSets are some of the kinds that have this behavior.

In PHP K8s, this implementation is a bit tricky and need some configuration on your side:

```php
use RenokiCo\PhpK8s\Contracts\InteractsWithK8sCluster;
use RenokiCo\PhpK8s\Contracts\Podable;
use RenokiCo\PhpK8s\Kinds\K8sResource;
use RenokiCo\PhpK8s\Traits\HasPods;

class GameServerSet extends K8sResource implements InteractsWithK8sCluster, Podable
{
    use HasPods;

    /**
     * Get the selector for the pods that are owned by this resource.
     *
     * @return array
     */
    public function podsSelector(): array
    {
        return [
            'game-server-name' => $this->getName(),
        ];
    }
}
```

```php
$gameServerSet = new GameServerSet($cluster, [
    'metadata' => [
        'name' => 'some-name', // this is metadata.name
    ],
    'spec' => [
        'template' => [
            'metadata' => [
                'labels' => [
                    'game-server-name' => 'some-name', // this must match with metadata.name
                ],
            ],
            ...
        ],
        ...
    ],
    ...
]);
```

```php
foreach ($gameServerSet->getPods() as $pod) {
    //
}
```

As you can see, there is a `podsSelector()` array where you can define a set of labels that a `Pod` managed by this resource needs to have in order to `->getPods()` to work on it.

Alternatively, if you can't control the names and you want to match the labels by each individual resource, you may declare it yourself by calling once a callback that will resolve the label matching for the pod retrieval as explained, for example, in the [StatefulSet definition](../../resources/workloads/statefulset.md#custom-pod-labels).

```php
GameServerSet::selectPods(function (GameServerSet $gss) {
    // $gssis the current GameServerSet

    return [
        'some-label' => 'some-label-value',
        'some-other-label' => "{$gss->getName()}-custom-name",
    ];
});
```
