# edgelet-build
A Dockerfile contains all necessary packages to `cargo` commands for [edgelet](https://github.com/Azure/iotedge/tree/master/edgelet)

## Usage
The Dockerfile can be used to build or run `iotedged` inside docker container using cargo cache.

```
git clone https://github.com/Azure/iotedge.git
cd iotedge/edgelet

# build iotedged inside docker container and re-use cargo registry cache
docker run --rm \
  -v cargo-git:/root/.cargo/git \
  -v cargo-registry:/root/.cargo/registry \
  -v $PWD:/edgelet \
  -w /edgelet/iotedged \
  dmolokanov/edgelet-build \
  cargo build
```

Run `iotedged` inside container with custom configuration file 
```
docker run --rm \
  -v cargo-git:/root/.cargo/git \
  -v cargo-registry:/root/.cargo/registry \
  -v $PWD:/edgelet \
  -v $PWD/../../iotedged-config/config.yaml:/etc/iotedge/config.yaml \
  -w /edgelet/iotedged \
  dmolokanov/edgelet-build \
  cargo run -- -c /etc/iotedge/config.yaml
```

## Build image
```
git clone https://github.com:dmolokanov/edgelet-build
cd edgelet-build

# build docker image
docker build -t {username}/edgelet-build .

# push docker image to Docker Hub
docker push {username}/edgelet/build
```
