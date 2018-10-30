## 使用
1. 修改 env-example 配置
2. cp env-example .env
3. docker-compose up  caddy postgres nodejs  


## Local runtime/binary

本机无需安装 yarn 而使用 yarn 的方法：

修改  `~/.bashrc` 或者  `~/.zshrc` ，在结尾添加：

然后 `source ~/.bashrc`

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
        node:alpine yarn ”$@“
}
```
