# helm 저장소 추가
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add bitmani https://charts.bitnami.com/bitnami
```

# Git에서 Yaml 파일 Pull
git clone https://github.com/leelax22/basic-prom.git

# 모니터링을 위한 네임스페이스 생성
```
kubectl create ns monitoring
```

# 비밀 생성
```
cat <<EOF > objsto_conf.yaml
type: AZURE
config:
  storage_account: 
  storage_account_key: 
  container: 
  endpoint: "blob.core.windows.net"
  max_retries: 0
EOF
```

# kube-prometheus-stack 배포
```
helm install i-n monitoring -f values-kube-prometheus-stack.yaml kube-prometheus-stack prometheus-community/kube-prometheus-stack 
```

# loki stack 배포
```
helm install -n monitoring loki-stack grafana/loki-stack
```

# thanos 배포
```
helm install -n monitoring thanos bitnami/thanos
```
