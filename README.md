# README

## Building and pushing bundles

```
$ docker build -t quay.io/agreene/busybox-dependency-bundle:X.0.0 .
$ docker push quay.io/agreene/busybox-dependency-bundle:x.0.0
```

## OPM Command to build Index

```bash
$ opm index add --bundles quay.io/agreene/busybox-dependency-bundle:1.0.0,quay.io/agreene/busybox-bundle:1.0.0 --tag quay.io/agreene/busybox-dependencies-index:1.0.0 -c docker

$ docker push quay.io/agreene/busybox-dependencies-index:1.0.0

$ opm index add --bundles quay.io/agreene/busybox-dependency-bundle:2.0.0,quay.io/agreene/busybox-bundle:2.0.0 --tag quay.io/agreene/busybox-dependencies-index:2.0.0 --from-index quay.io/agreene/busybox-dependencies-index:1.0.0 -c docker

$ docker push quay.io/agreene/busybox-dependencies-index:2.0.0
```

## Inspect running containers

```bash
$ docker run -p 50051:50051 quay.io/agreene/busybox-dependencies-index:1.0.0

$ grpcurl -plaintext  localhost:50051 api.Registry/ListBundles
```
