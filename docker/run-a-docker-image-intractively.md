# Run a docker image intractively

## Pull the image

```text
docker image pull ubuntu:18.04
```

## Run the image to interactively

```text
docker container -it --rm \
    ubuntu:18.04 \
    /bin/bash
```

参数解析：

* -i : Keep STDIN open even if not attached 允许对stdin进行交互
* -t : Allocate a pseudo-TTY 建立一个伪TTY，没有TTY无法对容器进行交互
* --rm: Automatically remove the container when it exits



