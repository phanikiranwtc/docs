---
title: Parallel vs. Sequential Tasks in Kestra
icon: /docs/icons/tutorial.svg
---

When to use parallel tasks and when to use sequential tasks in Kestra.

## Parallel Tasks

The following flow has 6 tasks wrapped in the `Parallel` task. Since the `concurrent` property is set to 3, Kestra will run 3 tasks in parallel. As soon as any of the three tasks completes, the next task will start.

The addition of the Parallel task with the `concurrent` property set to 3 ensures that Kestra will run up to 3 tasks concurrently. The `last` task will run after all the tasks in the `Parallel` task group have completed.

```yaml
id: parallel
namespace: example

tasks:
  - id: parent
    type: io.kestra.core.tasks.flows.Parallel
    concurrent: 3
    tasks:
      - id: t1
        type: io.kestra.plugin.scripts.shell.Commands
        runner: PROCESS
        commands:
          - 'echo "running {{task.id}}"'
          - 'sleep 1'
      - id: t2
        type: io.kestra.plugin.scripts.shell.Commands
        runner: PROCESS
        commands:
          - 'echo "running {{task.id}}"'
          - 'sleep 1'
      - id: t3
        type: io.kestra.plugin.scripts.shell.Commands
        runner: PROCESS
        commands:
          - 'echo "running {{task.id}}"'
          - 'sleep 1'
      - id: t4
        type: io.kestra.plugin.scripts.shell.Commands
        runner: PROCESS
        commands:
          - 'echo "running {{task.id}}"'
          - 'sleep 1'
      - id: t5
        type: io.kestra.plugin.scripts.shell.Commands
        runner: PROCESS
        commands:
          - 'echo "running {{task.id}}"'
          - 'sleep 1'
      - id: t6
        type: io.kestra.plugin.scripts.shell.Commands
        runner: PROCESS
        commands:
          - 'echo "running {{task.id}}"'
          - 'sleep 1'
  - id: last
    type: io.kestra.core.tasks.debugs.Return
    format: "{{task.id}} > {{taskrun.startDate}}"

```

## Sequential Tasks

This flow will start two sequential task groups in parallel. The addition of the `Sequential` task ensures that the tasks within each group will run one after the other. The `last` task will run after all the tasks in the `Sequential` task group have completed

```yaml
id: sequential
namespace: example

description: |
  This flow will start the 2 sequential tasks in parallel and those will launch tasks one after the other.

tasks:
  - id: parent
    type: io.kestra.core.tasks.flows.Parallel
    tasks:
      - id: seq1
        type: io.kestra.core.tasks.flows.Sequential
        tasks:
          - id: t1
            type: io.kestra.plugin.scripts.shell.Commands
            runner: PROCESS
            commands:
              - 'echo "running {{task.id}}"'
              - 'sleep 1'
          - id: t2
            type: io.kestra.plugin.scripts.shell.Commands
            runner: PROCESS
            commands:
              - 'echo "running {{task.id}}"'
              - 'sleep 1'
          - id: t3
            type: io.kestra.plugin.scripts.shell.Commands
            runner: PROCESS
            commands:
              - 'echo "running {{task.id}}"'
              - 'sleep 1'
      - id: seq2
        type: io.kestra.core.tasks.flows.Sequential
        tasks:
          - id: t4
            type: io.kestra.plugin.scripts.shell.Commands
            runner: PROCESS
            commands:
              - 'echo "running {{task.id}}"'
              - 'sleep 1'
          - id: t5
            type: io.kestra.plugin.scripts.shell.Commands
            runner: PROCESS
            commands:
              - 'echo "running {{task.id}}"'
              - 'sleep 1'
          - id: t6
            type: io.kestra.plugin.scripts.shell.Commands
            runner: PROCESS
            commands:
              - 'echo "running {{task.id}}"'
              - 'sleep 1'
  - id: last
    type: io.kestra.core.tasks.debugs.Return
    format: "{{task.id}} > {{taskrun.startDate}}"
```



