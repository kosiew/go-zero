# Repository Guidelines

## Development Workflow

- **Code Formatting**: Run `gofmt -w` on all changed `.go` files before committing.
- **Dependency Management**: Execute `go mod tidy` and include any resulting changes.
- **Static Analysis**: Run `go vet -stdmethods=false $(go list ./...)` and resolve issues.
- **Testing**: Ensure `go test -race ./...` passes before committing.

## Commit Messages

Write clear commit messages describing why the change is made.

## PR Guidance

Summaries should mention major changes and reference the tests run.
