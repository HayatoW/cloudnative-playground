# CloudNative Playground

https://github.com/cloudnativedaysjp/cnd-handson を参考にして、ローカルで Cloud Native 技術を勉強する

## 開発環境

- M4 Max
- メモリ 128 GB
- Docker Desktop

## よく使用するコマンド

```zsh
# kind で Kubernetes クラスターを作成
kind create cluster --config=config.yaml

# Gateway API の CRD (Custom Resource Definitions) をデプロイ
kubectl apply --server-side -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.5.1/standard-install.yaml

# kind で作成した Kubernetes クラスターを削除
kind delete cluster
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

### Helm のインストール

https://helm.sh/docs/intro/install/#from-homebrew-macos

```zsh
brew install helm
```

### Helmfile のインストール

Helmfile は Helm チャートをデプロイするための宣言的スペックらしい。。。

https://helmfile.readthedocs.io/en/latest/#step-1-install-helmfile

```zsh
brew install helmfile
```
