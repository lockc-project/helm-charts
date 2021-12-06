lockc is open source software for providing MAC (Mandatory Access Control) type of security audit for container workloads.

For more information refer to the [official lockc website](https://rancher-sandbox.github.io/lockc/).

## Installing the charts


For example:
```console
$ helm repo add lockc https://rancher-sandbox.github.io/lockc-helm-charts/
$ helm install --create-namespace -n lockc lockc lockc
```

This will install lockc on the Kubernetes cluster in the default configuration.

The default configuration values should be good enough for the majority of
deployments. All the options are documented in the configuration section.

## Upgrading the charts

Please refer to the release notes of each version of the helm charts.
These can be found [here](https://github.com/rancher-sandbox/lockc-helm-charts/releases).

## Uninstalling the charts

To uninstall/delete lockc use the following
command:

```console
$ helm uninstall -n lockc lockc
```

The commands remove all the Kubernetes components associated with the chart, all
policy servers and their policies, and deletes the release along with the release
history.

If you want to keep the history use `--keep-history` flag.

## Configuration

The following tables list the configurable parameters of the lockc
chart and their default values.

| Parameter                        | Description                                                                                                              | Default             |
| ---------------------------------| ------------------------------------------------------------------------------------------------------------------------ | ------------------- |
| `nameOverride`                   | Replaces the name of the chart in the `Chart.yaml` file when this is is used to construct Kubernetes object names         | ``                  |
| `fullnameOverride`               | Completely replaces the generated name                                                                                   | ``                  |
| `imagePullSecrets`               | Secrets to be used to pull container images from a Private Registry. Refer to [official Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/) | `[]` |
| `image.repository`               | The `lockc` container image to be used                                                                      | `ghcr.io/rancher-sandbox/lockc` |
| `image.tag`                      | The tag of the `lockc` container image to be used. When left empty chart's `AppVersion` is going to be used | ``                  |
| `podAnnotations`                 | Extra annotations to add to the `lockc` deployment                                                          | `{}`                |
| `nodeSelector`                   | `nodeSelector` for the `lockc` deployment                                                                   | `{}`                |
| `tolerations`                    | `tolerations` for the `lockc` deployment                                                                    | `{}`                |
| `affinity`                       | `affinity` rules for the `lockc` deployment                                                                 | `{}`                |
| `policyServer.replicaCount`      | Replica size for the `policy-server` deployment                                                                          | `1`                 |
| `policyServer.image.repository`  | The `policy-server` container image to be used                                                                           | `ghcr.io/rancher-sandbox/lockc` |
| `policyServer.image.tag`         | The tag of the `policy-server` container image to be used                                                                | ``                  |
