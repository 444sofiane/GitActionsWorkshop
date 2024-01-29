# GitActionsWorkshop
Unlock the power of Git with automation : Build, test and deploy your projects using the Gitaction service

# GitHub Actions Fundamentals



## 1. Setting Up Basic Workflow

### Create a new github repo

### Create a `.github/workflows` Directory

```bash
mkdir .github/workflows
```

### Create a `basic_workflow.yml` file

This workflow will include one job: hello-world prints a simple message.

Ensure the workflow is triggered on each push to the master branch

Test the workflow by pushing a random file

Hints :
First, the workflow will checkout the repo using the action: [Checkout repo](https://github.com/actions/checkout/tree/v2.5.0/)

## 2.Test running Workflow

### Create a `run_unit_tests.yml` file

This workflow will include one job: run criterion unit test on a .c file

Ensure the workflow is triggered on each push to the master branch

Hint:
Install libcriterion using sudo apt-get install -y libcriterion-dev if your workflow runs on ubuntu-latest

### Create a `node_action.yml` file

This workflow will include one job: run test on a .js file and notify on a discord channel if the tests fails

Ensure the workflow is triggered on each push to the master branch

Hints:
First, like before, the workflow will checkout the repo using the same action
Second, the workflow will setup node.js: [Node](https://github.com/actions/setup-node/tree/v3/)

Then it will install the necessary dependencies for your js project using npm install
To notify the user if the test fails use : [Discord](https://github.com/Ilshidur/action-discord)

## 3. Deployment 

### Create a `push_to_docker.yml` file

This workflow will include one job: containerize your js project in a docker image

Ensure the workflow is triggered on each push to the master branch

Hints:
Setup docker using: [Docker](https://github.com/docker/setup-buildx-action/tree/v1/)

### Create a `push_to_s3.yml` file

This workflow will include one job: push your js project to a s3 bucket

Ensure the workflow is triggered on each push to the master branch

Hints:
Setup aws using : [Amazon](https://github.com/aws-actions/configure-aws-credentials/tree/v1/)