# webhookshell

A container image based on Rancher shell with WebbHook installed. Will be used to execute command against kubernetes cluster.

Use following commands to build & push to Quay.io

```
export WEBHOOK_VER=2.8.1
export SHELL_VER=v0.1.21
docker build --pull -t quay.io/enterprisecoding/webhookshell:${WEBHOOK_VER}-${SHELL_VER} --build-arg="WEBHOOK_VER=${WEBHOOK_VER}" --build-arg="SHELL_VER=${SHELL_VER}" .
docker push quay.io/enterprisecoding/webhookshell:${WEBHOOK_VER}-${SHELL_VER}
```

Usage:

```
docker run -p 9000:9000 -v $(pwd)/sample/hooks.yaml:/etc/webhook/hooks.yaml -v $(pwd)/sample/sample.sh:/var/scripts/sample.sh -it --rm quay.io/enterprisecoding/webhookshell:${WEBHOOK_VER}-${SHELL_VER} -verbose -hooks=/etc/webhook/hooks.yaml -hotreload
```