# Summarized Status

Summarize Status multiple CIs (like Github Actions workflow).
Useful when you want to use `Require status checks to pass before merging` with monorepo (paths).

This is inspired action by [Merge Gatekeeper](https://github.com/marketplace/actions/merge-gatekeeper).
But, it has been improved in several points (especially execution time).

Original Merge Gatekeeper runs side-by-side with target workflows.
If a target workflow fails early, Gatekeeper quit too.
But if all target workflows succeed, Gatekeeper will run until last workflow finishes.
Its cost is high. If you have only one target workflow, Github Actions running cost becomes double.

Another improvement is image build.
Original is [Docker Action](https://docs.github.com/en/actions/creating-actions/about-custom-actions). Therefore, docker image build needed before execution.
This action is Composite Action. Then no need to build anything.

## Summarized Status vs Merge Gatekeeper

Summarized Status Pros:

- less running time (= less cost)
- Re-evaluate status automatically when you re-run failed job

Merge Gatekeeper Pros:

- Simple workflow definition
- No need to edit every time you add a workflow
- Gatekeeper workflow and subjest workflows are more isolated

# Designer's memo

If github changes check_run / check_suite event behaviors, this actions can be writtern more simply.
