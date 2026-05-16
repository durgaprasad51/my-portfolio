# Mastering Git for DevOps with Simple but Powerful Commands

<!-- category: DevOps -->
<!-- tags: Git, Version Control, DevOps, CI/CD, GitHub -->

Git with powerful real-world DevOps usage. This blog explains concepts clearly with real scenarios and then shows commands used in actual projects.

## First Section Heading

Git is a distributed version control system that helps track changes and manage collaboration.

In DevOps, Git is used not just for code but also for infrastructure, pipelines, and configuration files.

### Scenario

You are working in a team of 5 developers. Everyone is changing code daily. Without Git, files will overwrite each other. With Git, every change is tracked and merged safely.

### Core Concept

Git works with 3 main areas:
- Working Directory → where you edit code  
- Staging Area → where you prepare changes  
- Repository → where history is stored  

### Basic Setup & Starting Work

~~~bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list

git init
git clone https://github.com/user/repo.git
git status
~~~

### Adding and Saving Work

When you complete a small task, you save it using commit.

~~~bash
git add .
git commit -m "Added login feature"
git push origin main
~~~

👉 Always commit small changes instead of big ones.

## Second Section Heading

Branching is the most important concept in DevOps.

### Scenario

You are building a login feature, but the main branch is used for production. If you directly change main, you may break production.

Solution → Use branches.

### Branching Concept

Each feature should be developed in its own branch.

### Create and Work on Branch

~~~bash
git checkout -b feature-login
~~~

Now all your changes are isolated.

### Merge Back to Main

After testing:

~~~bash
git checkout main
git merge feature-login
~~~

### Working with Remote Teams

In real DevOps teams, multiple people push code.

~~~bash
git fetch origin
git pull origin main
~~~

👉 Always pull latest code before starting work.

### Advanced Git (Real Problems)

#### Scenario: You made a wrong commit

~~~bash
git reset --soft HEAD~1
~~~

#### Scenario: You want to completely remove changes

~~~bash
git reset --hard HEAD~1
~~~

#### Scenario: You want clean commit history

~~~bash
git rebase main
~~~

👉 Rebase is used in professional projects for clean history.

### Temporary Work Handling

#### Scenario: You need to switch task but not ready to commit

~~~bash
git stash
git stash pop
~~~

### Release Management

#### Scenario: You are deploying version 1.0

~~~bash
git tag v1.0
git push origin v1.0
~~~

Tags are used in CI/CD pipelines for releases.

### Best Practices

- Never push directly to main branch  
- Always create feature branches  
- Write clear commit messages  
- Pull before push  
- Avoid using `--force` unless necessary  

## Code Block

### Real DevOps Workflow Example

~~~bash
git checkout -b feature-api
git add .
git commit -m "Added API"
git push origin feature-api
~~~

### CI/CD Deployment Trigger

~~~bash
git add .
git commit -m "Deploy update"
git push origin main
~~~

👉 This push can trigger:
- Jenkins pipeline  
- GitHub Actions  
- GitLab CI/CD  

## Adding an Image

![Git Workflow](assets/git-workflow.png)

## Key Takeaways

- Git is the backbone of DevOps  
- Branching prevents breaking production  
- Rebase helps maintain clean history  
- Stash helps manage unfinished work  
- Git integrates directly with CI/CD pipelines  
