# Your Blog Title Goes Here

<!-- category: Kubernetes -->
<!-- tags: Kubernetes, EKS, AWS, Helm -->

Your opening paragraph goes here. This becomes the card preview on the portfolio automatically. Keep it to 1-2 clear sentences summarising what the reader will learn.

## First Section Heading

Write your content here using standard Markdown. You can use **bold**, *italic*, `inline code`, and [links](https://example.com).

## Second Section Heading

More content. Lists work great:

- First bullet point
- Second bullet point
- Third bullet point

Or numbered steps:

1. Step one
2. Step two
3. Step three

## Code Block

Use triple backticks with the language for syntax highlighting:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
```

```bash
kubectl apply -f deployment.yaml
kubectl get pods -n production
```

```python
import boto3
ec2 = boto3.client('ec2', region_name='ap-south-1')
```

## Adding an Image

Put your image in the assets/ folder of this repo, then reference it like this:

![Description of image](assets/my-image.png)

## Key Takeaways

- Summarise your main points here
- Keep it concise
- The date, read time, and "By Durga Prasad" signature are added automatically
