# Kubernetes Essentials Day 1

No curso de Kubernetes, consegui aprendeu os conceitos fundamentais sobre containers e a importância dos componentes que integram o ecossistema Kubernetes.

Abaixo irei deixar explicado cada parte do meu aprendizado que esse curso me proporcionou

## Containers e Container Engine
- **Containers** são unidades leves de software que empacotam aplicações e suas dependências, garantindo que funcionem de maneira consistente em diferentes ambientes.
- **Container Engine** é responsável por gerenciar imagens e volumes, isolando os recursos utilizados pelos containers, incluindo a vida útil, armazenamento e rede. As opções populares de container engines incluem Docker, CRI-O e Podman. O Docker é o mais conhecido e utiliza o **containerd** como seu container runtime.

## Container Runtime
- O **Container Runtime** é a camada que executa os containers. É fundamental para o funcionamento do Kubernetes, pois permite o gerenciamento e a execução efetiva dos containers.

## Kubernetes
- O **Kubernetes** (ou k8s) é um orquestrador de containers desenvolvido pela Google em 2014, inspirado no projeto Borg. Ele automatiza a implantação, escalabilidade e gerenciamento de aplicações em containers.
- O nome "Kubernetes" significa "timoneiro" em grego, e a comunidade frequentemente o chama de "k8s" para facilitar a pronúncia e escrita.

## Arquitetura do Kubernetes (k8s)

O Kubernetes, ou k8s, é uma plataforma poderosa para gerenciar contêineres em larga escala. Para entender como ele funciona, é importante conhecer suas principais ferramentas e componentes. Vamos explorar isso de maneira simples e com exemplos!



## Ferramentas para Implementação de Clusters Kubernetes

### 1. Kind
- **O que é?** Kind (Kubernetes IN Docker) é uma ferramenta que permite simular um cluster Kubernetes usando contêineres Docker.
- **Quando usar?** Ideal para aprendizado, desenvolvimento e testes. **Não é recomendado para ambientes de produção.**
- **Exemplo:** Imagine que você quer aprender a usar o Kubernetes sem precisar de um cluster real. Você pode usar o Kind para criar rapidamente um ambiente de teste no seu computador.

### 2. Minikube
- **O que é?** Minikube cria um cluster Kubernetes localmente, mas com apenas um nó.
- **Quando usar?** Assim como o Kind, é ótimo para aprendizado e desenvolvimento. **Não deve ser usado em produção.**
- **Exemplo:** Se você está desenvolvendo um aplicativo e quer testá-lo em Kubernetes, Minikube permite que você execute tudo em sua máquina.

### 3. MicroK8S
- **O que é?** MicroK8S é uma versão leve do Kubernetes desenvolvida pela Canonical.
- **Quando usar?** Pode ser utilizado em ambientes de produção, especialmente para aplicações em Edge Computing e Internet das Coisas (IoT).
- **Exemplo:** Se você tem um dispositivo IoT e deseja gerenciá-lo com Kubernetes, o MicroK8S é uma excelente escolha.

### 4. k3s
- **O que é?** k3s é uma versão minimalista do Kubernetes, criada pela Rancher Labs.
- **Quando usar?** Ideal para dispositivos com recursos limitados, como o Raspberry Pi, e também para ambientes de produção.
- **Exemplo:** Se você deseja criar um cluster Kubernetes em um Raspberry Pi para controlar uma pequena rede de sensores, o k3s é perfeito.

### 5. k0s
- **O que é?** k0s é uma distribuição do Kubernetes que é fácil de instalar e gerenciar, empacotando tudo em um único binário.
- **Quando usar?** Pode ser usado em ambientes de produção, com foco em simplicidade e baixo esforço técnico.
- **Exemplo:** Se você quer iniciar um cluster Kubernetes rapidamente e sem complicações, o k0s é a escolha ideal.

## Componentes do Kubernetes

### 1. API Server
- **O que é?** O API Server é o coração do Kubernetes, responsável por gerenciar as comunicações entre os componentes.
- **Como funciona?** Ele expõe uma API que usa JSON sobre HTTP. Administradores interagem com o cluster usando a ferramenta `kubectl`.
- **Exemplo:** Quando você executa o comando `kubectl get pods`, ele se comunica com o API Server para obter a lista de pods.

### 2. etcd
- **O que é?** O etcd é um banco de dados chave-valor que armazena informações sobre o estado do cluster.
- **Como funciona?** Ele guarda configurações e status dos objetos no Kubernetes.
- **Exemplo:** Se você configurar um deployment para ter 3 réplicas de um pod, o etcd armazenará essa informação para garantir que o cluster sempre tenha 3 réplicas em execução.

### 3. Scheduler
- **O que é?** O Scheduler decide em qual nó (máquina) um pod deve ser executado.
- **Como funciona?** Ele avalia os recursos disponíveis em cada nó e seleciona o mais adequado.
- **Exemplo:** Se você tem um pod que requer 1 CPU e 1GB de memória, o Scheduler procurará um nó com esses recursos disponíveis.

### 4. Controller Manager
- **O que é?** O Controller Manager é responsável por garantir que o estado atual do cluster corresponda ao estado desejado definido no etcd.
- **Como funciona?** Ele monitora o cluster e faz ajustes conforme necessário.
- **Exemplo:** Se você tem um deployment que deve ter 5 réplicas, mas apenas 3 estão em execução, o Controller Manager iniciará 2 novas réplicas para atingir a meta.

### 5. Kubelet
- **O que é?** O Kubelet é um agente que roda em cada nó worker do cluster.
- **Como funciona?** Ele gerencia os pods e containers em execução naquele nó, garantindo que tudo funcione conforme o planejado.
- **Exemplo:** Se um pod falhar, o Kubelet pode reiniciá-lo automaticamente para garantir que o serviço continue disponível.

### 6. Kube-proxy
- **O que é?** O Kube-proxy é responsável por gerenciar a rede e as comunicações entre os pods.
- **Como funciona?** Ele roteia o tráfego de rede para os pods corretos e atua como um balanceador de carga.
- **Exemplo:** Se você tem múltiplas réplicas de um serviço, o Kube-proxy garante que as requisições dos usuários sejam distribuídas entre todas as réplicas.

