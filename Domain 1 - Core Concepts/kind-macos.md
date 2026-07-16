### Documentation Referred:

https://kind.sigs.k8s.io/docs/user/quick-start/

### Commands Used in the Video

#### Option 1 - Easiest way 

```sh
brew install kind
```

#### Option 2 - Manual Way

This is for Apple Silicon Based macOS
```sh
[ $(uname -m) = arm64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.32.0/kind-darwin-arm64

chmod +x kind

sudo mkdir /usr/local/bin

sudo mv kind /usr/local/bin
```

```sh
kind
```
 