# Descomplicando Kubernetes

## O que iremos ver hoje?

Durante a aula de hoje, iremos ver todos os detalhes importantes sobre o menor objeto do Kubernetes, o **Pod**. Vamos ver desde a criação de um simples Pod, passando por Pods com múltiplos containers, com volumes e ainda com limitação ao consumo de recursos, como CPU ou memória. E claro, vamos aprender como ver todos os detalhes de um Pod em execução e brincar bastante com nossos arquivos YAML.

## O que é um Pod?

Primeiro, o Pod é a menor unidade dentro de um cluster Kubernetes.

Quando estamos falando sobre Pods, precisamos pensar que o Pod é uma "caixinha" que contém um ou mais containers. Esses containers compartilham os mesmos recursos do Pod, como, por exemplo, o IP, o namespace, o volume, etc.

Então, quando falamos de Pod, estamos falando de um ou mais containers que compartilham os mesmos recursos.

## Criando um Pod

Temos basicamente duas formas de criar um Pod: através de um comando no terminal e através de um arquivo YAML.

### Criando um Pod via terminal

Vamos começar criando um Pod através de um comando no terminal:

```bash
kubectl run giropops --image=nginx --port=80
```
O comando acima irá criar um Pod chamado giropops, com uma imagem do Nginx e com a porta 80 exposta.

Para ver o Pod criado, podemos usar o comando:

```bash
kubectl get pods
```
O comando acima irá listar todos os Pods que estão em execução no cluster, na namespace default.

Listando Pods
Para ver os Pods em execução em todas as namespaces, você pode usar o comando:

```bash
kubectl get pods -A
```
Para ver todos os Pods de uma namespace específica, você pode usar o comando Por exemplo:

```bash
kubectl get pods -n kube-system
```
Esse comando irá listar todos os Pods que estão em execução na namespace kube-system, que é onde o Kubernetes cria objetos relacionados ao cluster.

Visualizando detalhes do Pod
Para ver os detalhes de um Pod em formato YAML, você pode usar o comando:

```bash
kubectl get pods giropops -o yaml
```

Usando a saída wide
A saída wide é interessante, pois ela mostra mais detalhes sobre o Pod, como, por exemplo, o IP do Pod e o Node onde o Pod está sendo executado:

```bash
kubectl get pods giropops -o wide
```
Usando o comando describe
Se você quiser ver os detalhes do Pod em formato YAML, mas sem usar o comando get, você pode usar o comando:

```bash
kubectl describe pods giropops
```
Removendo o Pod:
Agora vamos remover o Pod que criamos usando o comando:
```bash
kubectl delete pods giropops
```