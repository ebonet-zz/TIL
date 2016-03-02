### [GO] Compiling GO binary to Ubuntu from MacOS

Plenty of the times our development server (or CI server) is not the same
as our production server. For interpreted languages like Python or Ruby this is no problem .
Java solves it by using the JVM.

In GO, however, binaries are built for a specific architecture, so if you build
your binary on MacOS it will not work on a ubuntu. But after Go 1.5 cross-compilation
became incredibly simple. You just need to set two env variables:

* `GOOS`: The target OS (linux, darvin, ...)
* `GOARCH`: the architecture of the system (286, amd, amd64, ....)

With this, to compile your code to Ubuntu for instance you just need to call:

```
GOOS=linux GOARCH=amd64 go build -v
```

And done! You can safely deploy your binary to your server.

A full list of values for `GOOS`/`GOARCH` can be found [here](https://golang.org/doc/install/source#environment):
