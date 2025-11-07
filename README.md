# GitHubActionsLab-SushantShouan
# GitHub Actions Lab

This repo has three basic GitHub Actions workflows I made for the lab.  
Each one shows a different feature: job order, env variables/secrets, and multi-platform jobs.

## 1) dependent-jobs.yml
- Trigger -> push to main  
- Shows job order using `needs`  
- Order goes: build -> test -> deploy  
- Just prints messages and uses `sleep` to show the flow

## 2) env-and-secrets.yml
- Trigger -> workflow_dispatch (manual run)  
- Shows env variables at:
  - workflow level  
  - job level  
  - step level  
- Also uses two fake repo secrets:
  - AWS_ACCESS_KEY_ID  
  - AWS_SECRET_ACCESS_KEY  
- GitHub hides secret values in the log automatically

## 3) multi-platform.yml
- Trigger -> pull request into main  
- Runs three jobs at the same time:
  - ubuntu-latest  
  - macos-latest  
  - windows-latest  
- Each prints system info and creates a small text file

### How I ran them
- Workflow 1 -> I pushed to main  
- Workflow 2 -> I went to Actions and clicked “Run workflow”  
- Workflow 3 -> I opened a PR from a new branch into main

### Notes I kept in mind
- Jobs only wait for each other if you use `needs`  
- Without `needs`, jobs run in parallel  
- Env variable levels go:
  workflow -> job -> step  
- Step env overrides the others  
- Secrets show up as `***` in logs

### Screenshots included
- Actions tab showing all workflows  
- Workflow 1 -> dependency graph + logs  
- Workflow 2 -> secrets page (names only) + run output  
- Workflow 3 -> all 3 OS jobs running together + logs
