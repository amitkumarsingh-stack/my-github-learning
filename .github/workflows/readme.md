
# Workflow Triggres or Workflow Syntax (my-first-workflow.yml)

To automatically trigger a workflow, use ***on*** to define which events can cause the workflow to run.

1. #### Using a single event
`on: push`

A workflow with the following on value will run when a push is made to any branch in the workflow's repository

2. #### Using multiple events
`on: [push, fork]`

A workflow with the following on value will run when a push is made to any branch in the repository or when someone forks the repository:

3. #### Using activity types
``` yaml
on:
  issues:
    types:
      - opened
      - labeled
```
4. #### Using activity types and filters with multiple events
For example, a workflow with the following on value will run when:

* A label is created
* A push is made to the main branch in the repository
``` yaml
on:
  label:
    types:
      - created
  push:
    branches:
      - main
```
# Parallel Execution vs Sequentially Execution
* By default, jobs in a GitHub Actions workflow run in parallel unless you explicitly define dependencies between them.
* If there are no dependencies between the jobs, they execute in parallel.
* To run jobs sequentially, you can use the ***needs*** keyword to define dependencies between jobs. This ensures that one job waits for another to finish before it starts.

# GitHub Artifacts
#### What are Artifacts?
Artifacts are files or data generated during the execution of a workflow job in GitHub Actions. These files are stored and made available for download after the job completes. Artifacts are especially useful when you want to:

* Share files between jobs in a workflow.
* Persist build outputs, logs, test results, or reports for later use or download.
* Debug issues by storing logs or diagnostic files.

#### Uploading Artifacts
Artifacts are uploaded using the actions/upload-artifact action. You can upload individual files or entire directories as artifacts.

# Job Outputs
#### What are Job Outputs?
Job outputs allow you to pass data (such as strings, version numbers, environment details) between jobs in the same workflow. Outputs are defined in one job and accessed by subsequent jobs. Job outputs are particularly useful when you need to:

* Share results or information between jobs (e.g., a version number generated in a build job and used in a deployment job).
* Control the execution flow of jobs based on previous job results (e.g., conditional deployments).