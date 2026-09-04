# Defender for Servers P2 - Resource Count

> [!NOTE]
> **Part of the [Sentinel Maturity Model](https://github.com/mathijsvermaat/Sentinel-Maturity)** — tiered guidance for Microsoft Sentinel data-connector onboarding, retention and detection coverage. The count this query returns is the P2 licence figure used by [Budget and Cost Planning](https://github.com/mathijsvermaat/Sentinel-Maturity/blob/main/guidance/budget-and-cost-planning.md) and by the ingestion-benefit calculation in the [assessment checklist](https://mathijsvermaat.github.io/sentinel-maturity-assessment.html).

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

## Sample output

| subscriptionId | subscriptionName | virtualMachinesResourcesCount | vmssServicesResourcesCount | totalServersCount |
|---|---|---|---|---|
| 5acda791-... | My Subscription A | 10 | 0 | 10 |
| 8bef3c72-... | My Subscription B | 5 | 3 | 8 |
| --- | \*\* Total (all subscriptions) \*\* | 15 | 3 | 18 |

## Related

- **[Sentinel Maturity Model](https://github.com/mathijsvermaat/Sentinel-Maturity)** — the tiered connector guidance model this query belongs to.
- **[Budget and Cost Planning](https://github.com/mathijsvermaat/Sentinel-Maturity/blob/main/guidance/budget-and-cost-planning.md)** — how the P2 count feeds Sentinel cost planning and the pooled ingestion allowance.
- **[Windows Security Events connector guidance](https://github.com/mathijsvermaat/Sentinel-Maturity/blob/main/connectors/windows-security-events.md)** — the connector whose `SecurityEvent` ingestion the P2 benefit offsets.
- **[Assessment checklist](https://mathijsvermaat.github.io/sentinel-maturity-assessment.html)** — enter the count in *Number of Defender for Servers P2 Licenses* to calculate the ingestion benefit.
