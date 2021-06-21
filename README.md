# Generate Structure

```shell
$ helm create hello
```

> them cleanup with:

```shell
# Folder Structure
.
├── .helmignore
├── Chart.yaml
├── charts
├── example
│   └── templates
│       └── message
├── templates
│   └── message
├── values-override.yaml
└── values.yaml

# Chart.yaml:
name: example
version: 0.1.0

# templates/message:
This is the most {{ .Values.description }} message: {{ .Values.message }}

# values.yaml:
description: awesome
message: hello world!

# values-override.yaml:
message: hello helm!
```



## Play with Template

```shell
$ helm template .
---
# Source: example/templates/message
This is the most awesome message: hello world!

$ helm template . -f values-override.yaml
---
# Source: example/templates/message
This is the most awesome message: hello helm!

$ helm template . -f values-override.yaml --output-dir .
wrote ./example/templates/message

$ cat example/templates/message 
##---
# Source: example/templates/message
This is the most awesome message: hello helm!

$ cat example/templates/message | tail -n +3
This is the most awesome message: hello helm!
```



## Enviroment

```shell
$ helm version
version.BuildInfo{Version:"v3.6.0", GitCommit:"7f2df6467771a75f5646b7f12afb408590ed1755", GitTreeState:"dirty", GoVersion:"go1.16.4"}
```



# Reference

* https://medium.com/@maorfr/template-everything-with-helm-48e5a32ff72d