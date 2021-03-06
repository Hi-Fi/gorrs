# gorrs

Pronounced like "gore's", abbreviation for "GO Robot Remote Server", a generic [Robot Framework](http://robotframework.org) [remote library server implementation](https://github.com/robotframework/RemoteInterface) in go.

This is a proof of concept prototype. Not fully working at the moment. See the source code for insight/details. Others are welcome to pick up where I left off.

## Setup

1. Have a version of [go](https://golang.org/dl/) installed. Recommend go 1.13+. And set up your $GOPATH and $GOBIN environment variables.
2. Get a copy of gorrs: ```go get -u github.com/daluu/gorrs```

The combination of go modules (`go.mod` + `go.sum`) & `go get -u` should pick up all the (versioned) dependencies to build gorrs. If you prefer using a different method of go dependency management, feel free to do so yourself.

## Intended usage (when gorrs is fully working):

1. Add an import statement/entry into ```protocol/protocol.go``` for the desired go-based library (go src path) to be served with gorrs. e.g. for the example remote library, ```import "github.com/daluu/gorrs/libraries"```.
2. Run the server: from source from repo path via ```go run main.go [args]```; or from compiled binary with ```go build``` or ```go install```, then run ```gorrs [args]```.

With ```go build```, the executable is in repo path, and you may move it elsewhere for use. With ```go install```, the binary is set to the $GOPATH/bin or $GOBIN paths, and can typically be executed from anywhere.

There's some issues with the gorrs XML-RPC library integration dependencies to resolve for it to fully work, and the go code reflection for dynamically serving remote libraries hasn't been implemented yet due to the existing issues. See source code for details.
