How to use the docker-setup for this project

build image

```bash
$ docker build . -t {{cookiecutter.module_name}}
```

test if it runs
```bash
$ docker run {{cookiecutter.module_name}} --help
```
