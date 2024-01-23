# GitActionsWorkshop
Unlock the power of Git with our intermediate-level workshop, GitAction Mastery: Streamlining Collaboration and Automation. Dive into advanced branching strategies, GitHub Actions workflows, and automation techniques to elevate your version control skills to new heights.

# GitHub Actions Fundamentals



## 1. Setting Up Basic Workflow

### Create a new github repo

### Create a `.github/workflows` Directory

```bash
mkdir -p .github/workflows
```

### Create a `github_action.yml` file

Put in the file the following content : 

```yml
name: Advanced Workflow

on:
  push:
    branches:
      - master

jobs:
  hello-world:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2.5.0
        with:
          fetch-depth: 0

      - name: Print Hello World
        run: echo "Hello, World!"

  setup-node:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2.5.0
        with:
          fetch-depth: 0

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: npm test

```
This workflow includes two jobs: hello-world prints a simple message, and setup-node checks out the repository, sets up Node.js, installs dependencies, and runs tests.

Ensure the workflow is triggered on each push to the master branch

```bash
git add .github/workflows/basic_workflow.yml
git commit -m "Add basic GitHub Actions workflow"
git push origin master
```

Now, the workflow will run on each push to the master branch, performing the specified tasks.


## 2. Advanced Workflow - Additional Job Ideas

Here are some ideas for additional jobs that you can add to your GitHub Actions workflow for more advanced functionality:

### Job for Code Quality Checks

Deploy to s3 bucket

```yml
additional_job_deploy_to_s3:
  runs-on: ubuntu-latest

  steps:
    - name: Checkout Repository
      uses: actions/checkout@v2.5.0
      with:
        fetch-depth: 0

    - name: Set up AWS CLI
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: 'us-east-1'

    - name: Check Dist Directory
      run: |
        if [ ! -d "dist" ]; then
          echo "Error: The 'dist' directory does not exist."
          exit 1
        fi

    - name: Deploy to AWS S3
      run: aws s3 sync ./dist s3://your-s3-bucket
```





