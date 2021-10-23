# Keycloak Helm Chart

```yaml
Author: Mitch Murphy
Date: 2021-10-22
```

## Configuration

Please see the official docs on [Docker Hub](https://hub.docker.com/r/jboss/keycloak) for more details. I have configured the basic settings (only supports embedded H2 database at the moment).

## TLS

This install assumes that the cluster (k3s or K8s) is configured to use the Traefik ingress controller. In order to enable proper TLS certs with Keycloak instance (at host specified in `values.yaml`) you must first procure the cert using the deployed `letsencrypt-prod` `ClusterIssuer`. As this will take some time to complete the ACME challenge, you will need to mount this secret (`.crt` and `.key` files) as a volume. This has been commmented out in `deployment.yaml` as you will need to wait for the secret to be available, and then edit the deployment. 