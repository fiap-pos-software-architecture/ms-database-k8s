# MS-DATABASE-K8S

Este repositório contém os manifests do Kubernetes para o serviço **MySQL**, responsável pelo armazenamento de dados da aplicação.

## 📂 Estrutura do Repositório

```
kubernetes/
└── MySQL/
    ├── mysql-configmap.yaml   # Configurações do ambiente para o banco de dados
    ├── mysql-deployment.yaml  # Definição do Deployment do MySQL
    ├── mysql-pv.yaml          # Definição do Persistent Volume (PV)
    ├── mysql-pvc.yaml         # Configuração do Persistent Volume Claim (PVC)
    ├── mysql-service.yaml     # Serviço do Kubernetes para expor o MySQL
```

## 🚀 Deploy no Kubernetes

Para implantar os recursos no seu cluster Kubernetes, siga os passos abaixo:

### 1️⃣ Aplicar ConfigMap

O ConfigMap contém as variáveis de ambiente para a configuração do **MySQL**. Para aplicá-lo, execute:

```bash
kubectl apply -f kubernetes/MySQL/mysql-configmap.yaml
```

### 2️⃣ Criar Persistent Volume (PV) e Persistent Volume Claim (PVC)

Esses recursos garantem o armazenamento persistente dos dados do **MySQL**.

```bash
kubectl apply -f kubernetes/MySQL/mysql-pv.yaml
kubectl apply -f kubernetes/MySQL/mysql-pvc.yaml
```

### 3️⃣ Criar o Deployment

O Deployment gerencia a criação e manutenção dos pods do **MySQL**.

```bash
kubectl apply -f kubernetes/MySQL/mysql-deployment.yaml
```

### 4️⃣ Criar o Service

Por fim, crie o serviço para permitir o acesso ao **MySQL**:

```bash
kubectl apply -f kubernetes/MySQL/mysql-service.yaml
```

## 🌍 Acessando o Banco de Dados

Após a implantação, o serviço estará disponível internamente no cluster Kubernetes. Para verificar os detalhes, utilize:

```bash
kubectl get svc -n <namespace>
```

Se precisar acessar o banco diretamente dentro do cluster, utilize:

```bash
kubectl exec -it <mysql-pod> -- mysql -u root -p
```