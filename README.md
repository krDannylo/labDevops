# 🚀 Lab DevOps - Projeto de Estudos AWS

Este é um projeto de estudos práticos focado em DevOps, envolvendo tecnologias como **AWS ECR**, **EC2**, **Security Groups**, **Docker** e **Git**. O projeto demonstra um pipeline completo de desenvolvimento e deploy de uma aplicação web simples.

## 📋 Sobre o Projeto

Este mini projeto foi desenvolvido para praticar e consolidar conhecimentos em:
- **Containerização** com Docker
- **Registro de containers** no AWS ECR
- **Deploy** em instâncias EC2
- **Configuração de segurança** com Security Groups
- **Gerenciamento de versões** com Git

## 🏗️ Arquitetura

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Local     │    │   AWS ECR   │    │   AWS EC2   │
│  Docker     │───▶│  Registry   │───▶│  Instance   │
│  Build      │    │             │    │             │
└─────────────┘    └─────────────┘    └─────────────┘
```

## 🛠️ Tecnologias Utilizadas

- **Docker** - Containerização da aplicação
- **AWS ECR** - Registro de containers
- **AWS EC2** - Servidor de produção
- **AWS Security Groups** - Configuração de segurança
- **Git** - Controle de versão

## 📁 Estrutura do Projeto

```
labDevops/
├── Dockerfile          # Configuração do container
├── README.md          # Documentação do projeto
└── website/           # Aplicação web
    ├── css/
    │   └── style.css
    ├── index.html
    └── js/
        └── script.js
```

## 🚀 Como Executar

### Pré-requisitos
- Docker instalado
- AWS CLI configurado
- Acesso a uma instância EC2
- Chave SSH para conexão com EC2

### Comandos Utilizados durante o Desenvolvimento

1. **Configurar AWS CLI**
   ```bash
   aws configure
   ```

2. **Fazer login no ECR**
   ```bash
   aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin [ACCOUNT-ID].dkr.ecr.us-east-2.amazonaws.com
   ```

3. **Listar imagens Docker locais**
   ```bash
   docker images
   ```

4. **Taggear a imagem para o ECR**
   ```bash
   docker tag website-lab-devops:v1.0 [ACCOUNT-ID].dkr.ecr.us-east-2.amazonaws.com/lab-devops-prod:v1.0
   ```

5. **Fazer push da imagem para o ECR**
   ```bash
   docker push [ACCOUNT-ID].dkr.ecr.us-east-2.amazonaws.com/lab-devops-prod:v1.0
   ```

6. **Conectar na instância EC2**
   ```bash
   ssh -i [CHAVE-PEM].pem ec2-user@[IP-INSTANCIA]
   ```

7. **Fazer pull da imagem no servidor**
   ```bash
   docker pull [ACCOUNT-ID].dkr.ecr.us-east-2.amazonaws.com/lab-devops-prod:v1.0
   ```

## 🔧 Configurações de Segurança

### Security Groups
- **Porta 22 (SSH)** - Acesso remoto
- **Porta 80 (HTTP)** - Acesso web
- **Porta 443 (HTTPS)** - Acesso web seguro

### IAM Roles
- Permissões para ECR
- Permissões para EC2

## 📝 Comandos Úteis

### Docker
```bash
# Construir imagem
docker build -t website-lab-devops:v1.0 .

# Executar container
docker run -d -p 80:80 website-lab-devops:v1.0

# Listar containers
docker ps

# Parar container
docker stop [CONTAINER-ID]
```

### AWS CLI
```bash
# Listar repositórios ECR
aws ecr describe-repositories --region us-east-2

# Listar imagens no repositório
aws ecr describe-images --repository-name lab-devops-prod --region us-east-2
```

## 🎯 Objetivos de Aprendizado

- ✅ Compreensão do fluxo de CI/CD básico
- ✅ Configuração e uso do AWS ECR
- ✅ Deploy automatizado em EC2
- ✅ Configuração de segurança na AWS
- ✅ Containerização com Docker
- ✅ Gerenciamento de versões com Git

## 📚 Recursos de Estudo

- [AWS ECR Documentation](https://docs.aws.amazon.com/ecr/)
- [Docker Documentation](https://docs.docker.com/)
- [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)

## 🤝 Contribuição

Este é um projeto de estudos pessoal, mas sugestões e melhorias são sempre bem-vindas!

## 📄 Licença

Este projeto é de uso educacional e pessoal.

---

**Desenvolvido com ❤️ para estudos de DevOps**
