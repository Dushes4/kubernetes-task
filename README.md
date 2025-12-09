## Структура проекта
```
mkdir kubernetes-homework
cd kubernetes-homework
nano hello.html
```
<img width="185" height="115" alt="VirtualBoxVM_fyiz1gnIje" src="https://github.com/user-attachments/assets/6a5cd6cb-4920-433e-a276-91e0250d56f2" />

## Dockerfile
```
nano Dockerfile
```
<img width="464" height="375" alt="VirtualBoxVM_MrJAQ0c66V" src="https://github.com/user-attachments/assets/6ae85ce7-e9d1-4903-9e35-bf59c5274f44" />

## Сборка образа
```
sudo docker build -t dashevsky/web:1.0.0 .
```
<img width="872" height="552" alt="VirtualBoxVM_oTgqnTLfgn" src="https://github.com/user-attachments/assets/f6c22a0d-9335-4800-8c84-a2a524f32958" />

```
sudo docker images
```
<img width="708" height="108" alt="VirtualBoxVM_c8woHYJZWm" src="https://github.com/user-attachments/assets/b895dec4-eb98-4586-b46c-b5b5be735be5" />

## Запуск и проверка контейнера
```
sudo docker run --rm -p 8000:8000 dashevsky/web:1.0.0
curl http://127.0.0.1:8000/hello.html
```
<img width="909" height="187" alt="VirtualBoxVM_PKSi2B7Txt" src="https://github.com/user-attachments/assets/2aa197e6-c4c6-4422-847d-c95d85e93433" />


## Загрузка образа в Docker Hub
```
sudo docker login
```
<img width="1021" height="399" alt="VirtualBoxVM_h88kv3aZ0a" src="https://github.com/user-attachments/assets/4ddbf6c2-860e-42fa-b5ca-a7f59f434a03" />

```
sudo docker push dashevsky/web:1.0.0
```
<img width="991" height="269" alt="VirtualBoxVM_2iAr0ejXUb" src="https://github.com/user-attachments/assets/99def1ed-2689-47b2-80ea-afa8603f40fd" />

## Kubernetes Deployment
```
cd ~
curl -Lo kind https://kind.sigs.k8s.io/dl/v0.26.0/kind-linux-amd64
chmod +x kind
sudo mv kind /usr/local/bin/
kind version
```

<img width="858" height="266" alt="VirtualBoxVM_isUY8xK1Js" src="https://github.com/user-attachments/assets/a4b82229-eaf1-471a-b723-558114005316" />

```
kind create cluster --name hw-cluster1
```

<img width="804" height="323" alt="VirtualBoxVM_WZpFVJSzK0" src="https://github.com/user-attachments/assets/d34c3edd-7f75-42bc-a6a8-d606a67cf54b" />

```
kubectl get nodes
```

<img width="664" height="81" alt="VirtualBoxVM_T7OKMRSMXY" src="https://github.com/user-attachments/assets/d0c15351-d929-4b3c-99cc-667ac7bfb68e" />

```
nano deployment-web.yaml
```

<img width="419" height="568" alt="VirtualBoxVM_K6E5VLUj3L" src="https://github.com/user-attachments/assets/db103e9f-d053-4685-821b-d60667e64bc0" />

```
kubectl apply -f deployment-web.yaml
```

<img width="714" height="66" alt="VirtualBoxVM_KCrfdo0vDh" src="https://github.com/user-attachments/assets/905e7924-6b51-49d9-81aa-6d5004880bec" />


```
kubectl get pods
```

<img width="564" height="105" alt="VirtualBoxVM_u52QBXfdqq" src="https://github.com/user-attachments/assets/f5bd481a-dbee-4301-85f9-b444fb6281f4" />

```
kubectl describe deployment web
```
(Полный вывод в describe.txt)
<img width="797" height="259" alt="VirtualBoxVM_A0poJ2pQyS" src="https://github.com/user-attachments/assets/9459e646-ee04-4afb-8d24-a3067b1a495b" />


## Доступ к приложению
```
kubectl port-forward deployment/web 8080:8000
```
<img width="638" height="103" alt="VirtualBoxVM_cxETRBgtyW" src="https://github.com/user-attachments/assets/2e79d09b-7bc4-476c-b8f9-4ebc20085630" />

```
curl http://127.0.0.1:8080/hello.html
```
<img width="737" height="64" alt="VirtualBoxVM_8yksMNrQKp" src="https://github.com/user-attachments/assets/aca10c7e-4289-4064-aeec-440070685188" />
