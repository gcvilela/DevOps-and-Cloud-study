# Documentação: Serviços Essenciais na GCP

## 1. VPC (Virtual Private Cloud)

A **VPC** na Google Cloud Platform fornece uma rede virtual escalável, isolada e global, que permite a criação de ambientes seguros para hospedar aplicações, bancos de dados e outros recursos.

Características principais:
- Rede global: uma única VPC pode abranger várias regiões do Google Cloud, facilitando a comunicação entre recursos distribuídos globalmente.
- Sub-redes regionais: permitem segmentar a VPC em diferentes regiões, atribuindo intervalos de endereços IP específicos.
- Tabelas de rotas para controlar como o tráfego flui dentro da VPC.
- Firewalls baseados em regras para permitir ou negar tráfego de entrada e saída.
- Compatibilidade com conectividade híbrida, como Cloud VPN, Interconnect e Peering.

Principais recursos associados:
- **Cloud Router**: roteamento dinâmico com BGP para conexões híbridas.
- **VPC Peering**: conecta VPCs de diferentes projetos ou organizações.

## 2. Compute Engine (GCE)

O **Google Compute Engine (GCE)** é o serviço de máquinas virtuais da GCP, permitindo criar instâncias altamente configuráveis com diversos tipos de CPU, memória, armazenamento e sistemas operacionais.

Características principais:
- VMs preemptivas e Spot VMs para cargas temporárias e econômicas.
- Custom Machine Types: escolha personalizada de vCPU e memória.
- Imagens padrão do Google ou imagens customizadas para instâncias específicas.
- Discos permanentes SSD ou HDD que podem ser anexados às instâncias.
- Instâncias gerenciadas (Managed Instance Groups) para escalar horizontalmente aplicações.

Principais casos de uso:
- Hospedagem de servidores web, APIs, bancos de dados, aplicações legadas ou em contêineres (quando não se usa GKE).

## 3. Cloud Storage (GCS)

O **Google Cloud Storage (GCS)** é um serviço de armazenamento de objetos altamente durável e escalável, ideal para armazenar e acessar dados não estruturados, como arquivos, imagens, vídeos, backups, logs, entre outros.

Características principais:
- Classes de armazenamento: Standard, Nearline, Coldline e Archive, otimizadas para diferentes frequências de acesso.
- Buckets: contêineres globais onde os objetos são armazenados.
- IAM e ACLs para controlar permissões de acesso aos buckets e objetos.
- Integração nativa com outras soluções do Google Cloud, como BigQuery e Cloud Functions.
- Suporte a versionamento de objetos, registros de auditoria e criptografia em repouso ou com chaves gerenciadas pelo cliente.

Principais casos de uso:
- Hospedagem de arquivos estáticos.
- Armazenamento de dados para análises.
- Backup e disaster recovery.

## 4. Cloud Functions

O **Cloud Functions** é a plataforma serverless da GCP para executar código em resposta a eventos sem necessidade de gerenciar servidores. Permite criar funções pequenas e independentes que escalam automaticamente com base na demanda.

Características principais:
- Suporte a múltiplas linguagens, incluindo Node.js, Python, Go, Java, entre outras.
- Integração com eventos de mais de 90 serviços da GCP, como mudanças em Cloud Storage, mensagens no Pub/Sub e chamadas HTTP.
- Cobrança baseada no tempo de execução efetivo e na quantidade de recursos consumidos.
- Gerenciamento automático de infraestrutura, escalabilidade e alta disponibilidade.

Principais casos de uso:
- Processamento em tempo real de eventos (por exemplo, redimensionar imagens ao fazer upload em um bucket).
- APIs serverless de baixo custo.
- Automação de tarefas administrativas na nuvem.

## 5. Cloud Monitoring

O **Cloud Monitoring** fornece monitoramento, coleta de métricas, registros e alertas em tempo real para recursos hospedados na GCP, em outras nuvens ou on-premises.

Características principais:
- Coleta de métricas de mais de 150 serviços do Google Cloud e integrações com ambientes externos.
- Dashboards customizáveis para visualizar dados em tempo real.
- Alertas configuráveis para notificar por e-mail, Slack, SMS, PagerDuty, entre outros, quando métricas violarem limites definidos.
- Integração com **Cloud Logging** para correlacionar métricas e logs.
- SLOs (Service Level Objectives) para monitorar acordos de nível de serviço e garantir qualidade.

Principais casos de uso:
- Monitorar a saúde de instâncias, bancos de dados e serviços serverless.
- Detectar anomalias em aplicações em produção.
- Criar relatórios de desempenho e disponibilidade.


## Boas Práticas

- Planeje suas redes VPCs com ranges de IP que evitem conflitos futuros, principalmente em ambientes híbridos.
- Utilize tags e labels em recursos do GCP para organizar e facilitar monitoramento e controle de custos.
- Configure alertas proativos no Cloud Monitoring para detectar problemas antes que afetem os usuários.
- Use Cloud Functions para automatizar tarefas e reduzir custos de infraestrutura.
- Armazene dados não estruturados no Cloud Storage usando a classe de armazenamento apropriada para reduzir custos.


