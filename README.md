# My gh-actions-playground

small examples of interesting github actions combinations

## Overview

GitHub Actions is what happens when yaml and bash decide to have a child.

Each workflow file must define:

- name (unique across all workflows)
- on (event)
- jobs (actual work)

### Events

What could possibly trigger an workflow

- You hit a button
- A git push or something
- Another workflow

More possibilities [here](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows).

### Jobs

- Give cool names to your jobs, not just _build_
- One workflow can hold several jobs
- Jobs will runn in **parallel** unless you do something about it
  - make jobs `needs` other jobs

More details [here](https://docs.github.com/en/actions/using-jobs/using-conditions-to-control-job-execution).

## 00 - [smallest possible](.github/workflows/00-hello-world.yml)

- [manual dispatch](https://github.com/sombriks/gh-actions-playground/actions/workflows/00-hello-world.yml)
- [echoes hello world](https://github.com/sombriks/gh-actions-playground/actions/runs/7162121699/job/19498652966#step:2:5)
- amazingly useless

## 01 - [occurs on every git push or merge](.github/workflows/01-it-happens-on-push.yml)

- [the 101 of CI]()