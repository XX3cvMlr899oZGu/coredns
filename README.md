# CoreDNS Fork

This is a fork of [coredns/coredns](https://github.com/coredns/coredns) — a fast and flexible DNS server.

## Overview

CoreDNS is a DNS server that chains plugins. Each plugin performs a DNS function, such as Kubernetes service discovery, metrics, caching, and more.

## Building

### Prerequisites

- Go 1.21 or later
- Make

### Build from Source

```bash
git clone https://github.com/your-org/coredns.git
cd coredns
make
```

This will produce a `coredns` binary in the current directory.

### Docker

```bash
docker build -t coredns:latest .
```

## Running

```bash
./coredns -conf Corefile
```

### Example Corefile

```
. {
    forward . 8.8.8.8 8.8.4.4
    cache 30
    log
    errors
    health
}
```

## Plugins

This fork includes all standard CoreDNS plugins plus the following additions:

| Plugin | Description |
|--------|-------------|
| `forward` | Proxy DNS requests to upstream resolvers |
| `cache` | Cache DNS responses |
| `log` | Log DNS queries |
| `errors` | Log errors |
| `health` | Health check endpoint |
| `metrics` | Prometheus metrics |
| `kubernetes` | Kubernetes service discovery |

For a full list of plugins, see the [CoreDNS plugin documentation](https://coredns.io/plugins/).

## Configuration

CoreDNS is configured via a `Corefile`. See the [Corefile documentation](https://coredns.io/2017/07/23/corefile-explained/) for details.

## Contributing

Please read [CONTRIBUTING.md](.github/CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](.github/CODE_OF_CONDUCT.md) before submitting pull requests.

## License

Apache License 2.0 — see [LICENSE](LICENSE) for details.

## Upstream

This project tracks upstream [coredns/coredns](https://github.com/coredns/coredns). To sync with upstream:

```bash
git remote add upstream https://github.com/coredns/coredns.git
git fetch upstream
git merge upstream/main
```
