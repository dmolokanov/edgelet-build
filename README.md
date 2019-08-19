# edgelet-build
A Dockerfile contains all necessary packages to `cargo` commands for [edgelet](https://github.com/Azure/iotedge/tree/master/edgelet)

# Usage
The Dockergile can be used to build or run `iotedged` inside docker container using cargo cache.

```
git clone https://github.com/Azure/iotedge.git
cd iotedge/edgelet

docker run --rm -v cargo-git:/root/.cargo/git -v cargo-registry:/root/.cargo/registry -v $PWD:/edgelet -w /edgelet/iotedged dmolokanov/edgelet-build cargo build

```

# Build image
```
git clone https://github.com:dmolokanov/edgelet-build
cd edgelet-build

# build docker image
docker build -t {username}/edgelet-build .

# push docker image to Docker Hub
docker push {username}/edgelet/build
```
