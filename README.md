# Tor Helm Charts

A collection of Helm charts for deploying various Tor services on Kubernetes.

## Available Charts

- **tor-relay**: Deploy a Tor relay node
- **tor-bridge**: Deploy a Tor bridge node
- **tor-snowflake**: Deploy a Snowflake proxy

## Installation

Add this Helm repository:

```bash
helm repo add tor-helm https://habetuz.github.io/tor-helm/
helm repo update
```

## Usage

### Installing a Chart

> [!NOTE]
> As these charts are primarily build for my own usage,
> they designed for **single node clusters** only.
>
> This might change in the future, but feel free to suggest/implement changes
> for multi node clusters.

```bash
# Install Tor Relay
helm install my-relay tor-helm/tor-relay

# Install Tor Bridge
helm install my-bridge tor-helm/tor-bridge

# Install Tor Snowflake
helm install my-snowflake tor-helm/tor-snowflake
```

More information in the `README.md` of each chart.

- [Relay](./charts/tor-relay/README.md)
- [Bridge](./charts/tor-bridge/README.md)
- [Snowflake](./charts/tor-snowflake/README.md)

## Development

### Building Charts

```bash
# Package all charts
helm package charts/tor-relay
helm package charts/tor-bridge
helm package charts/tor-snowflake

# Generate index
helm repo index .
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

See [LICENSE](LICENSE) file for details.
