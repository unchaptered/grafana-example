# Grafana Example

```
Vagrant 2.4.3.
```

## Pre-requisites

```shell
git init

# 3. 원격 저장소 추가
git remote add origin https://github.com/sysnet4admin/_Lecture_k8s_learning.kit.git

# 4. sparse-checkout 설정
git sparse-checkout init
git sparse-checkout set ch2/2.4

# 5. 파일 가져오기
git pull origin main
```

## Get Started

```shell
sudo ./ch2/2.4/.cmd

ssh cp-k8s

# Install Helm
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

### helm repo

```shell
# Install Prometheus, Grafana
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts

helm repo update
helm repo list
# NAME                    URL                                               
# grafana                 https://grafana.github.io/helm-charts             
# prometheus-community    https://prometheus-community.github.io/helm-charts
```

### prometheus-node-exporter

```shell
helm upgrade prometheus-node-exporter prometheus-community/prometheus-node-exporter --namespace monitoring --install --create-namespace
```