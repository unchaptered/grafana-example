# Grafana Example

## Versions

```shell
tabby 1.0.207                  # VMWare에 접속을 편하게 하기 위한 도구

vmware-fusion 13.6.1,24319021  # VMWare Fusion

vagrant 2.4.1
vagrant-vmware-utility 1.0.22
```

## Get Started

필요한 도구 설치

```shell
sudo ./ch2/2.4/.cmd
```

실습을 위한 가상환경 셋팅

```shell
cd ./ch2/2.4/k8s-adv

vagrant up
```

### helm repo

```shell
ssh cp-k8s

# Install Helm
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

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