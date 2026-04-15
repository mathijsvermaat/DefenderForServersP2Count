# Defender for Servers P2 - Resource Count

This Azure Resource Graph (ARG) query replicates the **virtualMachinesResourcesCount** shown in the Defender for Cloud Environment Settings blade (`PolicyPricingWithBundlesBlade`). It counts the number of resources covered by the **Defender for Servers P2** plan.

## What it counts

| Column | Description |
|---|---|
| `virtualMachinesResourcesCount` | Azure VMs, Classic VMs, and Azure Arc machines |
| `vmssServicesResourcesCount` | VM Scale Set instances (based on `sku.capacity`) |
| `totalServersCount` | Sum of both |

## Resource types included

- `microsoft.compute/virtualmachines`
- `microsoft.classiccompute/virtualmachines`
- `microsoft.hybridcompute/machines`
- `microsoft.compute/virtualmachinescalesets`

## How to run

1. Open the [Azure Resource Graph Explorer](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade)
2. Paste the contents of `DefenderForServersP2Count.kql`
3. Select the target subscriptions and click **Run query**

## Sample output

| subscriptionId | subscriptionName | virtualMachinesResourcesCount | vmssServicesResourcesCount | totalServersCount |
|---|---|---|---|---|
| 5acda791-... | My Subscription | 10 | 0 | 10 |
