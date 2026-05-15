# Zero-Downtime Deployments on EKS: Rolling Updates vs Blue/Green vs Canary

<!-- category: Kubernetes -->
<!-- tags: Kubernetes, EKS, ArgoCD, Helm, AWS -->

Downtime is expensive. For production workloads on AWS EKS, choosing the right deployment strategy can mean the difference between a seamless release and a 2am incident call.

## Rolling Updates — The Default

Kubernetes' built-in rolling update replaces pods incrementally. You control the blast radius with `maxUnavailable` and `maxSurge`:

```yaml
strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 1
    maxSurge: 2
```

**Best for:** Stateless services with a stable API contract.

**Risk:** Both versions run simultaneously — ensure your DB migrations are backward-compatible.

## Blue/Green — Full Swap, Zero Overlap

Spin up the new environment in full, then switch traffic at the Ingress level. ArgoCD's `BlueGreenStrategy` handles this natively:

```yaml
blueGreen:
  activeService: my-app-active
  previewService: my-app-preview
  autoPromotionEnabled: false
```

**Best for:** Releases requiring instant rollback or database schema changes.

**Cost:** Doubles resource consumption during the swap window.

## Canary — Progressive Traffic Shifting

Route a small percentage of real traffic to the new version first:

```yaml
canary:
  steps:
  - setWeight: 10
  - pause: {duration: 5m}
  - setWeight: 50
  - pause: {duration: 10m}
  - setWeight: 100
```

**Best for:** High-traffic services where you want real-world validation. Pair with Prometheus and `analysisRun` for fully automated promotion or rollback.

## Which One to Choose?

- **Need instant rollback?** → Blue/Green
- **Resource-constrained?** → Rolling Update
- **Want real traffic validation first?** → Canary

In practice: Rolling Updates for internal services, Blue/Green for customer-facing APIs, and Canary for anything touching payments or auth.
