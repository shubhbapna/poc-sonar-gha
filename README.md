# PoC-sonar-gha  

This PoC is to demonstrate how we can access secrets on PRs from forked repository.

The `PR check` workflow will run on every PR and its purpose is to perform tests and upload the results as an artifact.  
This workflow cannot access secrets when PRs are created from forked repository. To demonstrate this, the workflow will upload a file as artifact which contains the token. The file will be empty for PRs created from a fork.  
  
  
The `sonar` workflow is triggered whenever a `PR check` workflow runs successfully. Since `sonar` worflow has access to the secrets, this workflow can download the artifact from the `PR check` job that triggered it and successfully upload then to sonarcloud.

To try it out, fork the repository and open a PR to increment the counter below

counter = 2
