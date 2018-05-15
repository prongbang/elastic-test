# Elastic

# Create Project

## Initial dependencies
```
$ dep init
```

## Adding a new dependency
```
$ dep ensure -add github.com/foo/bar github.com/baz/quux
```

## Updating dependencies
```
$ dep ensure -update github.com/foo/bar
```

## Rule changes in `Gopkg.toml`
[https://golang.github.io/dep/docs/daily-dep.html#rule-changes-in-gopkgtoml](https://golang.github.io/dep/docs/daily-dep.html#rule-changes-in-gopkgtoml)

## Visualizing dependencies

> Linux

```
$ sudo apt-get install graphviz
$ dep status -dot | dot -T png | display
```

> macOS

```
$ brew install graphviz
$ dep status -dot | dot -T png | open -f -a /Applications/Preview.app
```

> Windows

```
> choco install graphviz.portable
> dep status -dot | dot -T png -o status.png; start status.png
```

## Run
```
$ go run main.go setup
$ go run main.go build
```

## Usage:

`go command [arguments]`
The commands are:

```
build       compile packages and dependencies
clean       remove object files and cached files
doc         show documentation for package or symbol
env         print Go environment information
bug         start a bug report
fix         update packages to use new APIs
fmt         gofmt (reformat) package sources
generate    generate Go files by processing source
get         download and install packages and dependencies
install     compile and install packages and dependencies
list        list packages
run         compile and run Go program
test        test packages
tool        run specified go tool
version     print Go version
vet         report likely mistakes in packages
```

Use "`go help [command]`" for more information about a command.

## Compile packages and dependencies

Usage:

```
go build [-o output] [-i] [build flags] [packages]
```

The build flags are shared by the build, clean, get, install, list, run, and test commands:

```
-a
	force rebuilding of packages that are already up-to-date.
-n
	print the commands but do not run them.
-p n
	the number of programs, such as build commands or
	test binaries, that can be run in parallel.
	The default is the number of CPUs available.
-race
	enable data race detection.
	Supported only on linux/amd64, freebsd/amd64, darwin/amd64 and windows/amd64.
-msan
	enable interoperation with memory sanitizer.
	Supported only on linux/amd64,
	and only with Clang/LLVM as the host C compiler.
-v
	print the names of packages as they are compiled.
-work
	print the name of the temporary work directory and
	do not delete it when exiting.
-x
	print the commands.

-asmflags '[pattern=]arg list'
	arguments to pass on each go tool asm invocation.
-buildmode mode
	build mode to use. See 'go help buildmode' for more.
-compiler name
	name of compiler to use, as in runtime.Compiler (gccgo or gc).
-gccgoflags '[pattern=]arg list'
	arguments to pass on each gccgo compiler/linker invocation.
-gcflags '[pattern=]arg list'
	arguments to pass on each go tool compile invocation.
-installsuffix suffix
	a suffix to use in the name of the package installation directory,
	in order to keep output separate from default builds.
	If using the -race flag, the install suffix is automatically set to race
	or, if set explicitly, has _race appended to it. Likewise for the -msan
	flag. Using a -buildmode option that requires non-default compile flags
	has a similar effect.
-ldflags '[pattern=]arg list'
	arguments to pass on each go tool link invocation.
-linkshared
	link against shared libraries previously created with
	-buildmode=shared.
-pkgdir dir
	install and load all packages from dir instead of the usual locations.
	For example, when building with a non-standard configuration,
	use -pkgdir to keep generated packages in a separate location.
-tags 'tag list'
	a space-separated list of build tags to consider satisfied during the
	build. For more information about build tags, see the description of
	build constraints in the documentation for the go/build package.
-toolexec 'cmd args'
	a program to use to invoke toolchain programs like vet and asm.
	For example, instead of running asm, the go command will run
	'cmd args /path/to/asm <arguments for asm>'.
```