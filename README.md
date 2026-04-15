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

The query includes a **total row** that sums all counts across every subscription, displayed as `** Total (all subscriptions) **`. Results are sorted by subscription name.

## How to run

1. Open the [Azure Resource Graph Explorer](https://portal.azure.com/#view/HubsExtension/ArgQueryBlade)
2. Paste the contents of `DefenderForServersP2Count.kql`
3. Select the target subscriptions and click **Run query**

## Sample output

| subscriptionId | subscriptionName | virtualMachinesResourcesCount | vmssServicesResourcesCount | totalServersCount |
|---|---|---|---|---|
| 5acda791-... | My Subscription A | 10 | 0 | 10 |
| 8bef3c72-... | My Subscription B | 5 | 3 | 8 |
| --- | \*\* Total (all subscriptions) \*\* | 15 | 3 | 18 |
