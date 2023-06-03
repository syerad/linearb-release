# LinearB Release Detection Action

The LinearB release detection action is a GitHub Action that allows you to send an HTTP request to the LinearB API in order to detect the release of a new version of your application. This action can be used as part of your CI/CD pipeline to automate the detection and tracking of releases.

## Usage

To use this GitHub Action in your own projects, follow the steps below:

### Step 1: Add the Action to Your Workflow

In your project's repository, create or navigate to the `.github/workflows` directory. Create a new workflow file (e.g., `release_detection.yml`) and add the following code:

```yaml
name: Release Detection

on:
  push:
    branches:
      - main

jobs:
  release_detection:
    name: LinearB Release Detection
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      - name: Run LinearB Release Detection
        uses: <your-github-username>/<your-repo-name>@<release-tag>
        with:
          linearb_api_token: ${{ secrets.LINEARB_API_TOKEN }}
          release_commit_sha: ${{ github.sha }}
          repository_name: ${{ github.repository }}
```

Replace `<your-github-username>` and `<your-repo-name>` with your GitHub username and repository name, respectively. Also, replace `<release-tag>` with the specific release tag of the action you want to use (e.g., `v1.0.0`).

### Step 2: Obtain LinearB API Token

To use this action, you need to obtain an API token from LinearB. Follow the LinearB documentation or contact your organization's administrator to obtain the API token. Once you have the token, store it as a secret in your GitHub repository. Go to your repository's "Settings" > "Secrets" and add a new secret named `LINEARB_API_TOKEN` with the API token value.

### Step 3: Configure the Action Inputs

The LinearB release detection action requires three inputs:

- `linearb_api_token`: The API token for LinearB (required).
- `release_commit_sha`: The SHA of the commit to detect the release of (required).
- `repository_name`: The name of the repository (required).

Ensure that you provide the correct values for these inputs in the workflow file.

### Step 4: Run the Workflow

Commit and push the workflow file (`release_detection.yml`) to your repository. The workflow will automatically trigger whenever a push event occurs on the `main` branch. The action will send an HTTP request to the LinearB API to detect the release of a new version of your application.

You can view the workflow runs and check the logs to monitor the execution of the action.

That's it! You have successfully integrated the LinearB release detection action into your project's workflow.

## Action Inputs

The following inputs are available for configuring the LinearB release detection action:

- `linearb_api_token` (required): The API token for LinearB. You can obtain this token from LinearB and store it as a secret in your repository.
- `release_commit_sha` (required): The SHA of the commit to detect the release of. This should be the commit that triggers the release.
- `repository_name` (required): The name of the repository. This should match the name of your GitHub repository.

## Action Outputs

This action does not provide any outputs.

## Example

Here's an example of how the LinearB release detection action can be used in a workflow:

```yaml
name: Release Detection

on:
  push:
    branches:
      - main

jobs:
  release_detection:
    name:# linearb-release
