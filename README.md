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
docker run --rm --workdir /work -v ${PWD}:/work cgr.dev/chainguard/apko \
  build apko.yaml kube-webhook-certgen:test kube-webhook-certgen.tar \
  --arch host \
  -k melange.rsa.pub

# run container
docker load < kube-webhook-certgen.tar
docker run --rm kube-webhook-certgen:test-arm64
```
