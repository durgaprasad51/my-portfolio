# portfolio-blogs

> Drop a `.md` file here → it appears on your portfolio automatically.

---

## How it works

```
You write a .md file  →  push to this repo  →  portfolio picks it up

Auto-detected from the file:
  ✅ Title      →  first # heading
  ✅ Date stamp →  last Git commit date (auto-updates on every edit)
  ✅ Read time  →  calculated from word count
  ✅ Excerpt    →  first paragraph
  ✅ Category   →  <!-- category: Kubernetes --> comment
  ✅ Tags       →  <!-- tags: K8s, AWS --> comment
  ✅ Signature  →  "By Durga Prasad" added automatically
  ✅ Images     →  put in assets/, reference in markdown
```

No JSON index. No rebuild. No deployment. Just write and push.

---

## Repo Structure

```
portfolio-blogs/
├── blogs/
│   ├── _TEMPLATE.md          ← copy this to start every new post
│   ├── eks-zero-downtime.md  ← example post
│   └── your-new-post.md      ← add yours here
├── assets/
│   └── my-image.png          ← images for your posts
├── .github/workflows/
│   └── validate-blogs.yml    ← auto-validates every push
└── README.md
```

---

## Writing a Blog Post (3 steps only)

### Step 1 — Copy the template

```bash
cp blogs/_TEMPLATE.md blogs/my-new-post.md
```

### Step 2 — Write your content

```markdown
# Your Blog Title Here

<!-- category: Terraform -->
<!-- tags: Terraform, AWS, IaC, S3 -->

Your opening paragraph. This becomes the card preview automatically.

## Section Heading

Your content here — standard Markdown, nothing special.

```yaml
key: value   ← code blocks with language for syntax highlighting
```

## Another Section

- Bullet points
- Work fine

## Conclusion

Wrap up here. Signature is added automatically.
```

**That is the complete format.** Clean markdown, nothing else.

### Step 3 — Push

```bash
git add blogs/my-new-post.md
git commit -m "Add blog: Your Title"
git push
```

Portfolio updates within seconds. No other steps.

---

## Markdown Reference

| Element | Syntax |
|---------|--------|
| Title (required) | `# My Title` as first line |
| Category badge | `<!-- category: Kubernetes -->` |
| Tags | `<!-- tags: K8s, EKS, Helm -->` |
| Excerpt | First paragraph (auto) |
| Bold | `**text**` |
| Italic | `*text*` |
| Inline code | `` `code` `` |
| Code block | ` ```yaml ... ``` ` |
| Image | `![alt](../assets/file.png)` |
| Link | `[text](https://url.com)` |
| Heading 2 | `## Section` |
| Heading 3 | `### Sub-section` |
| Bullet list | `- item` |
| Numbered list | `1. item` |
| Table | `\| Col \| Col \|` |

**Category examples:** `Kubernetes` `Terraform` `Docker` `CI/CD` `AWS` `Security` `GitOps` `Ansible` `Python` `Observability` — any word works.

---

## Images

1. Put your image in `assets/`
2. Reference it in markdown:

```markdown
![Architecture diagram](../assets/my-diagram.png)
```

---

## Date Stamping

- Date shown = **last Git commit date** for that file
- Edit a post → push → date updates automatically
- No manual date entry ever needed

---

## First-Time Deployment (One Time Only)

### 1. Create the GitHub repo

- Go to **github.com/new**
- Name: `portfolio-blogs` (must match `BLOGS_REPO` in your `index.html`)
- Visibility: **Public** ← Required for free GitHub Pages
- Do NOT tick "Add README" — you'll push your own files
- Click **Create repository**

### 2. Push this folder

```bash
cd portfolio-blogs
git init
git add .
git commit -m "Initial blog setup"
git branch -M main
git remote add origin https://github.com/durgaprasad51/portfolio-blogs.git
git push -u origin main
```

### 3. Verify

Open your portfolio → Blogs section → the cards should populate with your real posts.
Click a card → the full article should open.

Done. Every future blog = write `.md` → `git push`.

---

## GitHub Actions Validation

Every push to `blogs/*.md` triggers automatic checks:
- ✅ Every post has a `# Title`
- ✅ Category and title reported for each file
- ⚠️ Warns if `<!-- category: -->` is missing (doesn't fail the build)

Check results: **GitHub → Actions tab**

---

## Protecting Your Portfolio Repo

Steps to lock down your `index.html` repo so only you can change it.

### A. Protect the main branch (prevent accidental overwrites)

1. Your portfolio repo → **Settings** → **Branches** (left sidebar)
2. Click **Add branch ruleset**
3. Ruleset name: `Protect main`
4. Target: Add `main`
5. Enable:
   - ✅ **Restrict deletions**
   - ✅ **Block force pushes**
6. Click **Create**

### B. Remove unwanted collaborators

1. Repo → **Settings** → **Collaborators and teams**
2. Under **Manage access** — confirm only you are listed
3. Remove anyone who shouldn't be there

### C. Disable forking (public repos)

1. Repo → **Settings** → **General**
2. Scroll to **Features** → uncheck **Allow forking** (if available)

### D. Make the repo private (if not on GitHub Pages free tier)

If you host on Netlify, Vercel, or your own server — you can make it private:
- Repo → **Settings** → scroll to **Danger Zone**
- **Change repository visibility** → **Make private**

### E. Prevent ZIP downloads (legal protection)

GitHub can't fully block ZIP downloads on public repos. Use these instead:
- Add `<!-- © Durga Prasad — All Rights Reserved -->` at top of `index.html`
- Add a `LICENSE` file with "All Rights Reserved" (legally prevents reuse)

### F. Enable Two-Factor Authentication (CRITICAL)

This is the single most important protection for your account:

1. GitHub → your avatar (top right) → **Settings**
2. **Password and authentication** (left sidebar)
3. Under **Two-factor authentication** → **Enable**
4. Choose **Authenticator app** (Google Authenticator / Authy)
5. Scan the QR code with your phone app
6. Enter the 6-digit code to confirm
7. **Save your recovery codes** somewhere safe offline

### G. Review sessions and tokens

1. **Settings** → **Sessions** → revoke anything you don't recognise
2. **Settings** → **Developer settings** → **Personal access tokens** → revoke old tokens

---

## Quick Reference

| Task | What to do |
|------|-----------|
| New blog post | `cp blogs/_TEMPLATE.md blogs/my-post.md` → write → push |
| Edit a post | Edit the `.md` file → push (date auto-updates) |
| Add an image | Put in `assets/` → `![alt](../assets/file.png)` in markdown |
| Check validation | GitHub → Actions tab |
| Change portfolio username | Edit `GITHUB_USER` in `index.html` script section |

---

*© Durga Prasad — All Rights Reserved*
