# Install Kompose

```
wget https://github.com/kubernetes/kompose/releases/download/v1.26.1/kompose_1.26.1_amd64.deb 
sudo apt install ./kompose_1.26.1_amd64.deb
```

## Getting Started
```
mkdir -p samples
cd samples
wget https://raw.githubusercontent.com/kubernetes/kompose/master/examples/docker-compose.yaml
kompose convert
kubectl apply -f ../samples
```


