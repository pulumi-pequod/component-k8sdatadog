# component-k8sdatadog
Pulumi Component to deploy datadog monitor in K8s cluster using the [Datadog helm chart](https://artifacthub.io/packages/helm/datadog/datadog).

# Inputs

* datadogApiKey: API key to interface with Datadog.
* datadogHelmChartVersion (Optional): Version of the [Datadog Helmchart](https://artifacthub.io/packages/helm/datadog/datadog) to use. If not specified, a default version is used.

# Outputs

* datadogNamespace: The Datadog namespace that contains the monitoring output.

# Usage
## Specify Package in `Pulumi.yaml`

Add the following to your `Pulumi.yaml` file:
Note: If no version is specified, the latest version will be used.

```
packages:
  k8sdatadog: https://github.com/pulumi-pequod/component-k8sdatadog[@vX.Y.Z]
``` 

## Use SDK in Program

### Python
```
from pulumi_pequod_k8sdatadog import K8sMonitor, K8sMonitorArgs 

datadog_monitor = K8sMonitor("my-k8smonitor", 
                        datadog_api_key=config.datadogApiKey,
                        datadog_helm_chart_version=config.datdogMonitorHelmChart)
```

### Typescript
```
import { K8sMonitor } from "@pulumi-pequod/k8sdatadog";

const datadogMonitor = new K8sMonitor(baseName, {datadogApiKey: config.get("datadogApiKey")})
```

### Dotnet
```
using PulumiPequod.K8sDatadog;

var datadogMonitor = new K8sMonitor("stack-settings", {DatadogApiKey=datadogApiKey});
```

### YAML
```
  datadogMonitor:
    type: k8sdatadog:K8sMonitor
    properties:
      datadogApiKey: datadogApiKey 
```




