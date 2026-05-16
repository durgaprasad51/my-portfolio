# A perfect CI/CD for Portfolio Deployments

<!-- category: GitHub Action-->
<!-- tags: Git, GitHub Action, HTML, CSS, JS -->

GItHub Action solves the most demanding component of DevOps called CI/CD. Which makes things continuously `Integrated` and `Delivered / Deployed`.

## CI / CD

`Continuously Integration` - Devepoler Writes code on his system and pushes it to the `GIT` , Where the code will go through the variuos phases like `code build` `code test` then it will be integrated with rest of the code or with other developers code. 

`Delivered / Deployed` - Once the code is fully tested, it will be push to Main or Master branch. If this process needs a manual approval to get pushed to Main/Master branch it's called Delivery. And if all that is happing in a pipeline (Auto approved) then it is called Deployed or Deployment.

```
git   init
git add (file name)
git commit -m "First commit"
git push origin main/master

```

**Best for:** CICD Pipeline.

**Risk:** .

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
