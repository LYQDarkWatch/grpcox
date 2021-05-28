# gRPCox

[![Go Report Card](https://goreportcard.com/badge/github.com/gusaul/grpcox)](https://goreportcard.com/report/github.com/gusaul/grpcox)

turn [gRPCurl](https://github.com/fullstorydev/grpcurl) into web based UI, extremely easy to use

## Features

- Recognize and provide list of services and methods inside it as an options.
- Automatically recognize schema input and compose it into JSON based. (ensure your gRPC server supports [server reflection](https://github.com/grpc/grpc/blob/master/src/proto/grpc/reflection/v1alpha/reflection.proto)). Examples for how to set up server reflection can be found [here](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md#known-implementations).
- Save established connection, and reuse it for next invoke/request (also can close/restart connection)

## Installation

### Docker

```shell
docker pull gusaul/grpcox:latest
```

then run

```shell
docker run -p 6969:6969 -v {ABSOLUTE_PATH_TO_LOG}/log:/log -d gusaul/grpcox
```

### Docker Compose

from terminal, move to grpcox directory, then run command

```shell
docker-compose up
```

if you're using docker and want to connect gRPC on your local machine, then use
<br/>`host.docker.internal:<your gRPC port>` instead of `localhost`

### Golang

if you have golang installed on your local machine, just run command

```shell
make start
```

from grpcox directory

configure app preferences by editing `config.env` file

| var             | usage                                       | type   | unit   |
| --------------- | ------------------------------------------- | ------ | ------ |
| MAX_LIFE_CONN   | maximum idle time connection before closed  | number | minute |
| TICK_CLOSE_CONN | ticker interval to sweep expired connection | number | second |

set value `0 (zero)` to disable auto close idle connection.

## Demo

![gRPCox Demo](https://raw.githubusercontent.com/gusaul/grpcox/master/index/img/demogrpcox.gif)

导出

渠道名

607f73f62650fb00f04f5ee6

# Felix Liu

## 知识

### MongoDB Aggregate 注意事项

`$limit` 和 `$skip` 位置会影响最终结果：

- 如果 `$limit` 在前 `$skip` 在后，表示先取 `limit` 条记录，然后跳过前 `skip` 条数记录。
- 如果 `$skip` 在前 `$limit` 在后，表示先跳过 `skip` 条记录，然后取 `limit` 条数记录。
