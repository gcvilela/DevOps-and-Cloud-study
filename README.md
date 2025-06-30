# DevOps and Cloud Basics

Nesta trilha de aprendizado, o objetivo foi aplicar na prática os conceitos de DevOps e Cloud, evoluindo um programa simples em Python. A jornada demonstrou que, tão importante quanto saber um conceito, é saber repassar o conhecimento.

## Tema 01: DevOps Culture Principles

Artigo sobre as vantagens que uma cultura DevOps pode trazer para uma equipe técnica e como implementá-la.

## Tema 02 e 03: Arquiteturas On-Premises e Cloud

Artigo sobre as melhores práticas para arquiteturas On-Premises e em Nuvem, e quando utilizar cada abordagem.

## Tema 04: AWS Basic

- Criação de uma instância **EC2** (free-tier) e um bucket no **S3**.
- Sincronização de arquivos entre o bucket S3 e a instância EC2 em ambas as direções.
- Criação de um resumo em Markdown sobre os serviços de rede da AWS: **VPC, Roles, NAT, Security Groups, Routes e VPC Peering**.

## Tema 05: GCP Basic

- Criação de uma instância **GCE** (free-tier) e um bucket no **GCS (Google Cloud Storage)**.
- Sincronização de arquivos entre o bucket GCS e a instância GCE em ambas as direções.
- Criação de um resumo em Markdown sobre os serviços da GCP: **VPC, Monitoring, GCE, GCS e Functions**.

## Tema 06: Python

Desenvolvimento de um programa em Python que se conecta à API do Twitter (X) e recupera os 10 tweets mais recentes sobre os 10 atores que mais fizeram filmes nos últimos 10 anos (com base em dados do IMDB).

## Tema 07 e 08: Tarefas Agendadas em Linux e Windows

> **Tema 07 (Linux):** Criação de uma instância Linux na AWS (free-tier) para rodar o script Python de forma agendada via **Cron Job**. O código foi aprimorado para gerar arquivos de texto com os resultados, que foram sincronizados com um bucket S3.

> **Tema 08 (Windows):** Instalação de uma VM com Windows via VirtualBox para replicar o processo anterior. O agendamento foi realizado pelo **Agendador de Tarefas do Windows**, executando um script **PowerShell**.

## Tema 09: Jenkins

Automatização do processo de deploy com **Jenkins**. O pipeline foi configurado para buscar o código mais recente no GitHub e realizar o deploy automaticamente na instância EC2 Linux.

## Tema 10: Docker and Containers

Transformação da aplicação Python para rodar de forma isolada e portável em um **contêiner Docker**.

## Tema 11: Stack ELK

Instalação da **Stack ELK (Elasticsearch, Logstash, Kibana)** em contêineres Docker para observabilidade. Os logs do processo de pesquisa do Twitter (termos, resultados e quantidade) foram capturados e enviados para visualização no **Kibana**.

## Tema 12: Terraform

Como passo final, toda a infraestrutura na AWS foi codificada utilizando **Terraform (Infraestrutura como Código - IaC)**. O código gerado permite criar todo o ambiente do zero de forma automatizada e declarativa.
