# aws-cloudwatch-metrics

A helm chart for CloudWatch Agent to Collect Cluster Metrics

## Installing the Chart

Add the EKS repository to Helm:

```sh
helm repo add eks https://aws.github.io/eks-charts
```

Install or upgrading aws-cloudwatch-metrics chart with default configuration:

```sh
helm upgrade --install aws-cloudwatch-metrics \
    --namespace amazon-cloudwatch eks/aws-cloudwatch-metrics \
    --set clusterName=my-eks-cluster
```

## Configuration

| Parameter | Description | Default | Required |
| - | - | - | -
| `image.repository` | Image to deploy | `public.ecr.aws/cloudwatch-agent/cloudwatch-agent` | ✔
| `image.tag` | Image tag to deploy | `1.247350.0b251780`
| `image.pullPolicy` | Pull policy for the image | `IfNotPresent` | ✔
| `clusterName` | Name of your cluster | `cluster_name` | ✔
| `serviceAccount.create` | Whether a new service account should be created | `true` | 
| `serviceAccount.name` | Service account to be used | | 
| `hostNetwork` | Allow to use the network namespace and network resources of the node | `false` | 
| `nodeSelector` | Node labels for pod assignment	 | {} | 
| `tolerations` | Optional deployment tolerations	 | {} | 
| `annotations` | Optional pod annotations	 | {} | 
| `deployAsDaemonset` | If `false`, a deployment is created instead of a daemonset | `true` | 
| `replicas` | Number of pod replicas. Effective only if deployAsDaemonset is `false` | `1` | 
| `config` | Configuration for CloudWatch agent	 | See [values.yaml](./values.yaml) | ✔
| `prometheusConfig` | Prometheus configuration for CloudWatch agent	 | {} | 