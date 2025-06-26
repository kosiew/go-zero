
# Gemini Code Assistant Project Context

This document provides context for the Gemini Code Assistant to understand the go-zero project.

## Project Description

go-zero is a web and rpc framework with lots of builtin engineering practices. It’s born to ensure the stability of the busy services with resilience design and has been serving sites with tens of millions of users for years.

go-zero contains simple API description syntax and code generation tool called `goctl`. You can generate Go, iOS, Android, Kotlin, Dart, TypeScript, JavaScript from .api files with `goctl`.

## Project Language

The primary language of this project is Go.

## Key Tools and Technologies

- **goctl**: A command-line tool for code generation.
- **gRPC**: The project uses gRPC for remote procedure calls.
- **Docker**: The project uses Docker for containerization.

## Development Conventions

- API definitions are written in `.api` files.
- The `goctl` tool is used to generate server-side and client-side code from the `.api` files.
- Business logic is implemented in the `internal/logic` directory.
- Service context, such as database connections, is defined in the `internal/svc` directory.
- Configuration is stored in `.yaml` files in the `etc` directory.

## How to Run the Project

1. **Install goctl**:
   ```shell
   go install github.com/zeromicro/go-zero/tools/goctl@latest
   ```

2. **Create an API file**:
   ```go
   type (
     Request {
       Name string `path:"name,options=[you,me]"`
     }
     Response {
       Message string `json:"message"`
     }
   )
   service greet-api {
     @handler GreetHandler
     get /greet/from/:name(Request) returns (Response)
   }
   ```

3. **Generate Go server-side code**:
   ```shell
   goctl api go -api greet.api -dir greet
   ```

4. **Run the server**:
   ```shell
   cd greet
   go mod tidy
   go run greet.go -f etc/greet-api.yaml
   ```
