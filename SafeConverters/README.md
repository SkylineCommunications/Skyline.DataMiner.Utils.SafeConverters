# Skyline.DataMiner.Utils.SafeConverters

## About

Skyline.DataMiner.Utils.SafeConverters is a NuGet package in the public [nuget store](https://www.nuget.org/) that contain assemblies that assist in the safe convertion of one type to another.

Specifically they handle arithmetic overflow issues when going from a double to a uint or ulong value. This is particularly useful for Rate Calculations.

> Documentation: [Rate Calculations](https://community.dataminer.services/the-many-pitfalls-of-rate-calculations-and-how-you-can-avoid-them/?hilite=rate)

This safe converter will first check if the value is bigger than, in this example, the maximum value of UInt64 and in that case, return this maximum value. Again, you should not be afraid of this inaccuracy here as it will be very negligible and will only return a value closer to reality, since it all started from a counter that almost reached the maximum value of the counter type (in no case bigger).

## Requirements

The "DataMiner Integration Studio" Visual Studio extension is required for development of connectors and Automation scripts using NuGets.

See [Installing DataMiner Integration Studio](https://aka.dataminer.services/DisInstallation)

> [!IMPORTANT]
> NuGets are mandatory to be installed with PackageReferences. DIS was redesigned to work with PackageReferences and be future-proof.
>
> For more information on how to migrate from packages.config to PackageReferences, see [docs.microsoft.com](https://docs.microsoft.com/en-us/nuget/consume-packages/migrate-packages-config-to-package-reference).

## Getting started

```cs
    double counterAsDouble = Convert.ToDouble(protocol.GetParameter(Parameter.counter));
    ulong counter = SafeConvert.ToUInt64(counterAsDouble)
```
