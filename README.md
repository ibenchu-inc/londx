## 使用
1. cp env-example .env
2. 修改 .env 配置
3. docker-compose up  caddy postgres nodejs  


## Local runtime/binary

本机无需安装 yarn 而使用 yarn 的方法：

修改  `~/.bashrc` 或者  `~/.zshrc` ，在结尾添加：

然后 `source ~/.bashrc`

alipine 版，同线上

```
yarn () {
    tty=
    tty -s && tty=--tty
    docker run \
        $tty \
        --interactive \
        --rm \
        --user $(id -u):$(id -g) \
        --volume /etc/passwd:/etc/passwd:ro \
        --volume /etc/group:/etc/group:ro \
        --volume $(pwd):/usr/src/app \
        -w /usr/src/app \
        node:alpine-lts yarn ”$@“
}
```

debian 版，同本地

```
yarn () {
    tty=
    tty -s && tty=--tty
    docker run \
        $tty \
        --interactive \
        --rm \
        --user $(id -u):$(id -g) \
        --volume /etc/passwd:/etc/passwd:ro \
        --volume /etc/group:/etc/group:ro \
        --volume $(pwd):/usr/src/app \
        -w /usr/src/app \
        node:lts yarn ”$@“
}
```
