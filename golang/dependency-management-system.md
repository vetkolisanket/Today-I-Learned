# How to use Go's dependency management system?

* `go mod init` creates a new module, initializing the go.mod file that describes it.
* `go build`, `go test`, and other package-building commands add new dependencies to go.mod as needed.
* `go list -m all` prints the current module’s dependencies.
* `go get` changes the required version of a dependency (or adds a new dependency).
* `go mod tidy` removes unused dependencies.

Note: Go modules are disabled by default inside your GOPATH/src directory, to enable it you'll have to prepend `GO111MODULE=on` for go 1.11 or `GO112MODULE=on` for go 1.12, for e.g. your init command would be something like `GO111MODULE=on go mod init` and so on

[Reference](https://blog.golang.org/using-go-modules)
