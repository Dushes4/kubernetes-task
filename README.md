# Создаем структуру проекта

mkdir kubernetes-homework
cd kubernetes-homework
nano hello.html

nano Dockerfile

# Docker

sudo docker build -t dashevsky/web:1.0.0 .

sudo docker images


sudo docker run --rm -p 8000:8000 dashevsky/web:1.0.0
curl http://127.0.0.1:8000/hello.html


sudo docker login

sudo docker push dashevsky/web:1.0.0

# Kubernetes Deployment

nano deployment-web.yaml


cd ~
curl -Lo kind https://kind.sigs.k8s.io/dl/v0.26.0/kind-linux-amd64
chmod +x kind
sudo mv kind /usr/local/bin/
kind version


kind create cluster --name hw-cluster1

kubectl get nodes

kubectl apply -f deployment-web.yaml

kubectl get pods

kubectl describe deployment web

kubectl port-forward deployment/web 8080:8000

curl http://127.0.0.1:8080/hello.html
