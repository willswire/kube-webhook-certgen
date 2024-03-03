# kube-webhook-certgen

An APK build of [kube-webhook-certgen](https://github.com/jet/kube-webhook-certgen) using [melange](https://github.com/chainguard-dev/melange) (my first Melange build, yay!). Also create a container image using [apko](https://github.com/chainguard-dev/apko).

## Commands

```shell
# y u no have keys
docker run --rm -v "${PWD}":/work cgr.dev/chainguard/melange keygen

# build apk
docker run --privileged --rm -v "${PWD}":/work \
  cgr.dev/chainguard/melange build melange.yaml \
  --arch x86,amd64,aarch64,armv7 \
  --signing-key melange.rsa

# build container

```
