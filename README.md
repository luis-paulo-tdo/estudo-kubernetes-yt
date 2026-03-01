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

## 3. Criando um Pod
- Dentro de um Cluster, é possível utilizar diferentes recursos de aplicação que ele oferece.
- O Pod é a menor unidade criada e gerenciada em um Cluster, sendo um ou mais Contêineres.
- Eles compartilham o mesmo IP e a mesma porta, como se estivessem dentro da mesma máquina.
- Através de um arquivo manifesto, descrevemos exatamente como o Cluster deve funcionar.
- No Manifesto definimos a versão da API, tipo do recurso, metadados e especificações.
