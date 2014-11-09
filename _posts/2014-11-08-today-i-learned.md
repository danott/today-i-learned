Responding to http in Go on Dreamhost is pretty easy. The trick is to use
FactCGI to serve it up.

I did this via a trivial conditional for my setup of developing on OSX, and
deploying to Linux.

```golang
if runtime.GOOS == "linux" {
  fcgi.Serve(nil, nil)
} else {
  http.ListenAndServe(":2112", nil)
}
```

To cross-compile to Linux, you use the Go runtime flags.

```bash
GOOS=linux GOARCH=386 go build
```
