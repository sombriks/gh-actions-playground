# My gh-actions playground

Small examples of interesting GitHub actions combinations.

## How to run this playground

Most workflows where intentionally left with `workflow_dispatch` so they don't
run by accident on every commit. Not as if it was a big issue, since they do
_mostly nothing_ by design.

But you can also run them using the [act][0] command line tool, which emulates
the GitHub actions environment in a quite near the real thing way.

So, the three big ways to run a workflow:

- Visit [the actions page][1] and run them by hand
- Use the [GitHub CLI][2]: `gh workflow run .github/workflow/00-hello-world.yml`
- Use act: `act -W .github/workflows/00-hello-world.yml`

## Overview

GitHub Actions is what happens when yaml and bash decide to have a child.

The workflow files are used to common integration routines: run tests, check the
quality of code, perform any chore that can be automatized, scripted.

## Workflow file syntax

Each workflow file must define:

- _name_ (unique across all workflows)
- _on_ (event)
- _jobs_ (actual work)

### Events

What could possibly trigger an workflow

- You hit a button
- A git push or something
- Another workflow

More possibilities [here][3].

### Jobs

- Give cool names to your jobs, not just _build_
- One workflow can house several jobs
- Jobs will run in **parallel** unless you do something about it
  - make jobs `needs` other jobs

More details [here][4].

## 00 - [smallest possible][5]

- [Manual dispatch][6]
- [Echoes 'hello world'][7]

![image-manual-dispatch.png][8]

## 01 - [occurs on every git push or merge][9]

- The 101 of CI
- [Echoes 'hello word from _some branch_'][10]

![image-on-push.png][11]

## 02 - [have two jobs][12]

- Remember, runs in [parallel][13]!
- Pretty much like two distinct workflows, but sharing rent of a workflow file

![two-jobs.png][14]

## 03 - [have two jobs but in sequence][15]

- Make sure the second [needs][16] the first

![job-needs.png][17]

## 04 - [make one job use another workflow][18]

- This is why [workflow_call][19] exists
- Don't misread as [workflow_dispatch][20], it's another thing
- Quite similar to what we do when [consuming actions from marketplace][21]

## 05 - jobs inputs

## 06 - jobs outputs

## 07 - environment variables

## 08 - secrets

## 09 - steps

## 10 - use 3rd actions

## 11 - noteworthy actions

## 12 - writing good CI/CD pipelines

[0]: https://github.com/nektos/act?tab=readme-ov-file#installation-through-package-managers
[1]: https://github.com/sombriks/gh-actions-playground/actions
[2]: https://cli.github.com/
[3]: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows
[4]: https://docs.github.com/en/actions/using-jobs/using-conditions-to-control-job-execution
[5]: .github/workflows/00-hello-world.yml
[6]: https://github.com/sombriks/gh-actions-playground/actions/workflows/00-hello-world.yml
[7]: https://github.com/sombriks/gh-actions-playground/actions/runs/7162121699/job/19498652966#step:2:5
[8]: imgs/manual-dispatch.png
[9]: .github/workflows/01-it-happens-on-push.yml
[10]: https://github.com/sombriks/gh-actions-playground/actions/runs/7162222469/job/19498893130#step:2:5
[11]: imgs/on-push.png
[12]: .github/workflows/02-two-jobs.yml
[13]: https://github.com/sombriks/gh-actions-playground/actions/runs/7175366895/job/19538528783
[14]: imgs/two-jobs.png
[15]: .github/workflows/03-sequence-jobs.yml
[16]: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idneeds
[17]: imgs/job-needs.png
[18]: .github/workflows/04-use-workflow.yml
[19]: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#onworkflow_call
[20]: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#onworkflow_dispatch
[21]: https://github.com/marketplace?type=actions
[22]:
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:
