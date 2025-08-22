# Grafana Deployment

This directory contains the Kubernetes manifests for deploying Grafana in the homelab cluster.

## Components

- **deployment.yaml**: Main Grafana deployment with proper security context and resource limits
- **service.yaml**: LoadBalancer service with MetalLB IP 10.0.3.24
- **claim.yaml**: Persistent volume claim using Longhorn storage
- **configmap.yaml**: Grafana configuration (grafana.ini)
- **datasources.yaml**: Pre-configured datasources for Prometheus, Grafana Alloy, and Node Exporter
- **rbac.yaml**: Service account and cluster role for proper permissions

## Access

- **LoadBalancer**: http://10.0.3.24:3000
- **Authentication**: Disabled (anonymous access enabled for local development)

## Datasources

The following datasources are automatically configured:

1. **Prometheus** (Default): http://prometheus:9090
2. **Grafana Alloy**: http://grafana-alloy:12345
3. **Node Exporter**: http://node-exporter:9100

## Security Notes

- **Authentication disabled** for local development (anonymous access enabled)
- Service account has minimal required permissions
- Persistent storage ensures data survives pod restarts
- Health checks ensure proper monitoring
- **Note**: This configuration is for local development only - enable authentication for production

## Next Steps

1. Deploy the application via ArgoCD
2. Access Grafana directly at http://10.0.3.24:3000 (no authentication required)
3. Import additional dashboards for Kubernetes monitoring
4. Configure alerting rules
5. Set up additional datasources as needed

## Local Development Notes

- **No authentication required** - Grafana is accessible without login
- **Anonymous users** have Viewer role by default
- **Perfect for local development** and testing
- **Remember to enable authentication** when deploying to production
