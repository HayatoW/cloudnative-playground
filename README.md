# CloudNative Playground

https://github.com/cloudnativedaysjp/cnd-handson を参考にして、ローカルで Cloud Native 技術を勉強する

## 開発環境

- M4 Max
- メモリ 128 GB
- Docker Desktop

## よく使用するコマンド

```zsh
```

## 初期セットアップ

### kind のインストール

[Installing With A Package Manager](https://kind.sigs.k8s.io/docs/user/quick-start#installing-with-a-package-manager)

```zsh
brew install kind
```

### Cilium CLI のインストール

CNI (Container Network Interface) として Cilium を使用するので必要です。

https://github.com/cilium/cilium-cli#installation

```zsh
CILIUM_CLI_VERSION=$(curl -s https://raw.githubusercontent.com/cilium/cilium-cli/main/stable.txt)
GOOS=darwin
GOARCH=arm64
curl -L --remote-name-all https://github.com/cilium/cilium-cli/releases/download/${CILIUM_CLI_VERSION}/cilium-${GOOS}-${GOARCH}.tar.gz{,.sha256sum}
sha256sum --check cilium-${GOOS}-${GOARCH}.tar.gz.sha256sum
sudo tar -C /usr/local/bin -xzvf cilium-${GOOS}-${GOARCH}.tar.gz
rm cilium-${GOOS}-${GOARCH}.tar.gz{,.sha256sum}
```
