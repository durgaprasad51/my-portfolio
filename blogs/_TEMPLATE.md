# Your Blog Title Goes Here

<!-- category: Kubernetes -->
<!-- tags: Kubernetes, EKS, AWS, Helm -->

Your opening paragraph goes here. This first paragraph will automatically appear as the excerpt/preview on the blog card. Keep it to 1-2 sentences that summarise what the reader will learn.

## First Section Heading

Your content here. Write naturally — just standard Markdown. You can use **bold**, *italic*, `inline code`, and [links](https://example.com).

## Second Section Heading

More content here. Lists work great:

- First bullet point
- Second bullet point  
- Third bullet point

Or numbered lists:

1. Step one
2. Step two
3. Step three

## Code Example

Use triple backticks with the language name for syntax-highlighted code:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
```

```bash
kubectl apply -f deployment.yaml
kubectl get pods -n production
```

```python
import boto3

ec2 = boto3.client('ec2', region_name='ap-south-1')
response = ec2.describe_instances()
```

## Adding an Image

Put your images in the assets/ folder of this repo, then reference them like this:

![Description of image](../assets/my-image.png)

## Key Takeaways

- Wrap up your main points here
- Keep it concise
- The "By Durga Prasad" signature and date are added automatically
