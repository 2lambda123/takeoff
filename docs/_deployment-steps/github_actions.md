name: My Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Build project
        run: |
          npm install
          npm run build

      - name: Run tests
        run: npm test
```

In this example, the workflow is triggered on every push to the `main` branch. The `build` job runs on an Ubuntu environment and consists of three steps: checking out the code, building the project, and running tests.

## Environment variables

You can define and use environment variables in your GitHub Actions workflows. Environment variables allow you to store sensitive information or configuration values that can be accessed by your workflow steps.

To define an environment variable, you can use the `env` keyword in your workflow file. Here's an example:

```yaml
name: My Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    env:
      MY_VARIABLE: my-value

    steps:
      - name: Print environment variable
        run: echo $MY_VARIABLE
