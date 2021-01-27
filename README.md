# ECS TaskRun Buildkite Plugin

A [Buildkite plugin](https://buildkite.com/docs/agent/v3/plugins) wrapper for [ecs-run-task](https://github.com/buildkite/ecs-run-task).

## Example

This will run a Fargate task based on the existing `my-task-family` task definition

```yml
steps:
  - plugins:
      - marketplacer/ecs-run-task:
         download_url: https://github.com/buildkite/ecs-run-task/releases/download/v1.3.0/ecs-run-task-linux-amd64
         name: ecs-run-task
         task: my-task-family
         subnet: subnet-0fad071eb3f4fd69a
         security_group: sg-0350ec4a72ec27c38
         fargate: true
         deregister: true
```

## Configuration

### Required (one of)

### `file` (string)

Task definition file in JSON or YAML

### `task` (string)

An existing task definition. Either full Arn, family or family:revision

### Optional

### `download_url` (string)

Download URL for ecs-run-task binary. If not set, `ecs-run-task` is executed and has to be in the run path

### `cluster` (string)

ECS cluster name

Default: `"default"`

### `name` (string)

Task name

Default: `"buildkite-ecs-run-task"`

### `image` (string)

Container image name to replace

### `service` (string)

service to replace cmd for

### `platform_version` (string)

The platform version the task should run (only for FARGATE)

### `count` (integer)

Number of tasks to run

Default: `1`

### `cpu` (integer)

Number of cpu units reserved for the container

### `memory` (integer)

Hard limit (in MiB) of memory available to the container

### `fargate` (boolean)

Specified if task is to be run under FARGATE as opposed to EC2

Default: `false`

### `deregister` (boolean)

Deregister task definition once done

Default: `false`

### `region` (string)

AWS Region

### `log_group` (string)

Cloudwatch Log Group Name to write logs to

Default: `"ecs-task-runner"`

### `environment` (string or array of strings)

An environment variable to add in the form KEY=value

### `subnet` (string or array of strings)

Subnet to launch task in (required for FARGATE)

### `security_group` (string or array of strings)

Security groups to launch task in (required for FARGATE)

## License

MIT (see [LICENSE](LICENSE))
