
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