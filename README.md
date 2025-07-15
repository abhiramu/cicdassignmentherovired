# Flask CI/CD Pipeline with Jenkins hero

This project sets up a Jenkins pipeline to build, test, and deploy a Flask web application.

## Prerequisites

- AWS EC2 instance with Jenkins installed
- Python 3 and pip
- Jenkins plugins: Git, Pipeline, Email Extension

## Pipeline Stages

1. **Build**: Installs dependencies using `pip install -r requirements.txt`
2. **Test**: Runs `pytest`
3. **Deploy**: Deploys the app to a staging server (simulated)
4. **Notifications**: Sends email on build success/failure

## Jenkins Setup

- Configured on Ubuntu EC2
- Jenkins runs on port 8080
- GitHub webhook triggers pipeline on push

## Repository

Forked from: [Sample Flask App](https://github.com/heroku/python-getting-started)

## Screenshots

> Include screenshots of:
> - Jenkins Dashboard
> - Pipeline configuration
> - Pipeline execution (build → test → deploy)
> - Email Notification
