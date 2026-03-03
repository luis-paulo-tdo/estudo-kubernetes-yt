# Curso de Kubernetes: Orquestração de Contêineres

## 1. Introdução
- Kubernetes é uma plataforma que transformou a forma de implantar, escalar e gerenciar contêineres.
- É uma solução que proporciona uma abordagem simplificada e eficiente para computação em nuvem.
- Possibilita a automatização de tarefas como implantação, escalonamento e recuperação de falhas.
- Permite o dimensionamento automático de aplicações, garantindo desempenho e disponibilidade. 
- É portátil e pode ser implementado em ambientes de nuvem públicos, privados e híbridos.
- Ideal na implantação e gerenciamento de microsserviços, trazendo escalabilidade e resiliência.
- Beneficia cargas de trabalho de Big Data, fornecendo uma plataforma escalável e confiável.
- Soluciona a implantação e operação de Aplicações Web de alta disponibilidade e escalabilidade.
- Pode ser utilizado para gerenciar cargas de trabalho bem distribuídas em ambientes de IoT.
- Permite o foco no desenvolvimento do software ao simplificar a implantação e o gerenciamento.
- Confere flexibilidade às empresas na implantação e escalabilidade, dando agilidade operacional.
- Otimiza custos de infraestrutura e operações, reduzindo overhead no gerenciamento de contêineres.
- Tem uma robusta comunidade colaborativa e que promove o compartilhamento do conhecimento.

## 2. Instalando um Cluster
- A ferramenta Kind permite a criação de Clusteres locais do Kubernetes utilizando o Docker.
- Através dele, é criado um ambiente de laboratório antes que a aplicação suba em Produção.
- O Cluster é um conjunto de máquinas que rodam as aplicações como se fossem uma única.
- Um Cluster é composto por um Control Plane ou Nó Master, e os Workers ou Nós Operários.
- O Control Plane é o cérebro do Cluster, responsável por gerenciar os Workers que operam.
- Dentro dos Workers é onde ficarão as Aplicações que rodam e operam como parte do Sistema.
- Um Cluster Multi-Node é uma configuração que tem um Control Plane e mais de um Worker.
- O Controller Manager verifica e garante se os Nós estão funcionando corretamente.
- O Kube Scheduler verifica quais nós estão funcionando, quem e como precisam de alocação.
- O Kube ApiServer de um Cluster é o ponto de contato e intermediador dentro do Cluster.
- O Etcd de um Cluster é uma persistência chave-valor que mantém o seu estado registrado.

## 3. Criando um Pod
- Dentro de um Cluster, é possível utilizar diferentes recursos de aplicação que ele oferece.
- O Pod é a menor unidade criada e gerenciada em um Cluster, sendo um ou mais Contêineres.
- Eles compartilham o mesmo IP e a mesma porta, como se estivessem dentro da mesma máquina.
- Através de um arquivo manifesto, descrevemos exatamente como o Cluster deve funcionar.
- No Manifesto definimos a versão da API, tipo do recurso, metadados e especificações.
- Dentro dos metadados de um Manifesto, definimos o nome e labels de filtragem do recurso.
- Dentro das especificações, informamos os containeres que devem ser instalados no Cluster.

## 4. Criando um Deployment
- Existem situações onde um Pod pode cair por N motivos, deixando então o sistema indisponível.
- Através do recurso ReplicaSet, dizemos o Kube Scheduler que vamos criar uma replica dele.
- Kube Scheduler então repassa a mensagem para o Controller Manager para criar o Nó novamente.
- Esta configuração de réplicas determina quantas instâncias devemos ter rodando no Cluster.
- Podemos configurar estas réplicas para um ou mais contêineres através do recurso Deployment.
- Ao criar o Manifesto do Deployment, conseguimos configurar o número de réplicas para cada um.
- Cada quantidade de replicas configurada tem um matchLabel que será atribuído aos contêineres.
- Cada contêiner deve ter um template com a matchLabel correspondente à quantidade de réplicas.
- A partir destas configurações, um novo Deployment será criado sempre que o Pod for deletado.
- Sendo assim, conseguimos garantir uma alta disponibilidade dentro do recurso de Deployment.

PS: Bash para monitorar Pods
	for /l %g in () do @(kubectl get pods -o wide & timeout /t 1 > nul & cls)
	
## 5. Explicando a Criação de Recursos
- Pelo comando `kubectl explain`, entendemos melhor o que os recursos esperam em seus Manifestos.
- Este comando listará todas as propriedades que compõem o Manifesto e o que é cada uma delas.
- Cada propriedade recebe uma descrição detalhada sobre ela e quais tipos de dados aceita.
- Algumas propriedades como `status` são atribuídas em tempo de execução não sendo obrigatórias.
- Existem propriedades com tipo `object`, que recebem um conjunto de outras propriedades.
- Um `kubectl explain <objeto>` descreve o que é o objeto e as propriedades que ele possui.
- Desta forma, conseguimos navegar dentro de toda a hierarquia de propriedades de um Manifesto.

## 6. Introdução aos Services
- Para prover disponibilidade dos Pods, precisamos prover informações além dos Deployments.
- Alguns Services, como o auto-discovery, permitem a descoberta automática da aplicação.
- A auto-descoberta faz o Kube Scheduler encontrar a aplicação e registrá-la em um DNS.
- Este DNS interno permitirá a comunicação com os recursos do Pod mesmo que ele seja caia.
- Esta ação é necessária porque o endereço IP do Pod pode acabar mudando após ele cair.
- Com um Service, fazemos um encaminhamento das aplicações externas para o IP atualizado.
- Como o `kubectl expose deployment`, criamos um Service e informamos as portas de escuta.
- Assim, as requisições passam a apontar para o nome do Deployment em vez do endereço IP.
- Um Service pode apontar para várias réplicas no Cluster, e que podem mudar o seus nomes.
- Além disso, há Deployments diferentes de uma mesma aplicação em Namespaces diferentes.
- Neste caso, cada Deployment deve ter o seu próprio Service, correspondente ao Namespace.
- Com isso, uma rede de aplicações conseguirá outras através do DNS junto com o Namespace.
- Toda vez que um Service for criado para um Deployment, um DNS será criado para ele.
 