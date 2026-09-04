# Mongoku service for Kubernetes on Wodby

Run [Mongoku](https://github.com/huggingface/Mongoku), a browser-based MongoDB
client, as a service in Wodby applications.

This repository defines the Wodby service manifest for Mongoku. The service
uses the upstream `huggingface/mongoku` image and the generic Wodby stateless
Helm chart.

- [Mongoku service on Wodby](https://wodby.com/services/mongoku)
- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Configuration

The service requires a link to a MongoDB database and uses that database's
credential-bearing connection URL as its default host.

The web interface is protected by HTTP Basic authentication. The username is
`admin`; Wodby generates the password as the `admin_password` service token.
Read-only mode can be enabled through the service settings.

## Maintain a custom version

1. Fork this repository.
2. Edit `service.yml`.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).

When changing the container image, keep the service option tag and image
architecture support aligned. When changing the Helm chart, verify workload
selectors, container names, ports, probes, environment mappings, and replica
behavior against the rendered resources.

Validate the manifest with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/)
and the [managed services index](https://github.com/wodby/services).
