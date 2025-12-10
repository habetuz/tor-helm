# Tor Bridge Helm Chart

Deploys a Tor bridge node on Kubernetes to help users in censored regions access the Tor network.

> [!NOTE]
> As these charts are primarily build for my own usage,
> they designed for **single node clusters** only.
>
> This might change in the future, but feel free to suggest/implement changes
> for multi node clusters.

## Introduction

This chart deploys a Tor bridge on a Kubernetes cluster using the Helm package manager. Bridges are Tor relays that aren't listed in the main Tor directory, making the ideal for hosting from a home network.

More information can be found on the [Tor website](https://community.torproject.org/relay/types-of-relays/).

## Installing the Chart

```bash
helm install my-bridge tor-helm/tor-bridge
```

## Uninstalling the Chart

```bash
helm uninstall my-bridge
```

## Configuration

The following table lists the configurable parameters of the Tor Bridge chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `thetorproject/tor` |
| `image.tag` | Image tag | `""` (uses appVersion) |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.orPort` | OR port | `9001` |
| `service.extOrPort` | Extended OR port | `6669` |
| `persistence.enabled` | Enable persistence | `true` |
| `persistence.size` | PVC size | `1Gi` |
| `tor.nickname` | Bridge nickname | `TorBridge` |
| `tor.contactInfo` | Contact information | `your@email.com` |
| `tor.bridgeRelay` | Enable bridge mode | `true` |
| `tor.publishServerDescriptor` | Publish descriptor (0=private, 1=public) | `1` |
| `tor.relayBandwidthRate` | Bandwidth rate limit | `100 MBytes` |
| `tor.relayBandwidthBurst` | Bandwidth burst limit | `200 MBytes` |

## Important Notes

- **Contact Info**: You MUST set a valid contact email in `tor.contactInfo`
- **Bridge Distribution**: Set `tor.publishServerDescriptor` to `1` for public bridges distributed by BridgeDB, or `0` for private bridges
- **Bandwidth**: Adjust bandwidth limits based on your available resources
- **Persistence**: Highly recommended to keep bridge identity keys persistent
- **Pluggable Transports**: To add obfs4 or other transports, use `tor.extraConfig` to configure ServerTransportPlugin
