# Componentes de Rede na AWS

## 1. VPC (Virtual Private Cloud)

A **VPC** é a base da rede na AWS. Trata-se de uma rede virtual isolada dentro da nuvem da AWS, onde você define sua topologia de rede, incluindo:

- Bloco de endereços IP (CIDR block) para definir o range de endereços usados dentro da VPC.
- Sub-redes públicas (acessíveis diretamente da internet) e privadas (sem acesso direto).
- Tabelas de rotas para determinar como o tráfego se move dentro e fora da VPC.
- Gateways como Internet Gateway ou NAT Gateway para permitir comunicação com a internet.

A VPC oferece controle total sobre configuração de roteamento, segurança e segmentação da rede. É fundamental para criar arquiteturas seguras e escaláveis.

Principais recursos associados:
- **Internet Gateway (IGW)**: conecta sub-redes públicas à internet.
- **VPN Gateway / AWS Direct Connect**: conecta a rede local (on-premises) à AWS.
- **VPC Peering / Transit Gateway**: conecta VPCs entre si.

## 2. Roles (IAM Roles)

As **Roles** no AWS Identity and Access Management (IAM) permitem conceder permissões temporárias a usuários, serviços ou contas para executar ações na AWS, sem precisar armazenar credenciais de acesso.

Quando um recurso (ex.: uma instância EC2 ou uma função Lambda) assume uma Role, ele passa a agir com as permissões associadas a essa Role. Isso elimina a necessidade de salvar chaves de acesso em servidores ou código.

Principais usos de Roles:
- Permitir que instâncias EC2 acessem serviços como S3 ou DynamoDB.
- Permitir que aplicações em Lambda interajam com outros serviços AWS.
- Conceder acesso entre contas (cross-account access), permitindo que recursos em uma conta da AWS acessem recursos de outra conta.

## 3. NAT Gateway

O **NAT Gateway** é um serviço gerenciado pela AWS que permite que instâncias em sub-redes privadas iniciem conexões para a internet ou outros serviços fora da VPC, mas impede que a internet inicie conexões para essas instâncias.

Exemplo de uso:
- Instâncias privadas precisam baixar atualizações ou pacotes de um repositório externo.
- As instâncias privadas enviam a requisição para o NAT Gateway, que as encaminha para a internet através de um Internet Gateway.

Diferenças principais entre NAT Gateway e NAT Instance:
- NAT Gateway é gerenciado, escalável automaticamente e de alta disponibilidade em uma zona de disponibilidade (AZ).
- NAT Instance é uma máquina EC2 configurada manualmente como NAT, com maior flexibilidade, mas exige manutenção e escalabilidade manual.

## 4. Security Groups

**Security Groups** são firewalls virtuais que controlam o tráfego de entrada e saída de instâncias e outros recursos dentro da VPC. São definidos por regras que permitem ou negam tráfego com base em portas, protocolos, endereços IP de origem ou destino e outros Security Groups.

Características principais:
- São **stateful**: se uma conexão é permitida de entrada, a resposta automática de saída é permitida.
- Regras de Security Groups são permissivas (listas de autorização) — não existem regras de negação explícita.
- Podem ser aplicados a múltiplos recursos, como EC2, RDS, ELB, entre outros.
- Regras podem referenciar outros Security Groups, permitindo controlar acesso entre diferentes camadas de aplicações (ex.: permitir apenas que o Load Balancer acesse servidores de aplicação).

## 5. Routes (Route Tables)

As **Tabelas de Rotas** são componentes que definem como o tráfego é roteado dentro da VPC, determinando para onde devem ser enviados pacotes destinados a determinados blocos de IP.

Principais elementos de uma tabela de rotas:
- **Destino (Destination)**: o range de endereços IP para o qual a rota é válida.
- **Alvo (Target)**: o recurso para onde o tráfego deve ser enviado, como Internet Gateway, NAT Gateway, VPC Peering, Transit Gateway ou Local (sub-redes da VPC).

Cada sub-rede deve estar associada a uma única tabela de rotas:
- Sub-redes públicas geralmente têm uma rota para o Internet Gateway.
- Sub-redes privadas têm rota para o NAT Gateway para acesso de saída.

## 6. VPC Peering

O **VPC Peering** conecta duas VPCs, permitindo que recursos em ambas se comuniquem como se estivessem na mesma rede, usando endereços IP privados.

Principais características:
- Conexão ponto a ponto — não existe roteamento transitivo. Ou seja, se VPC A faz peering com VPC B e B com C, A não consegue se comunicar com C automaticamente.
- Pode ocorrer entre VPCs na mesma conta ou em contas diferentes.
- Pode ser intra-regional ou inter-regional.
- Cada VPC Peering requer configuração de tabelas de rotas para garantir que os CIDRs das VPCs sejam roteáveis entre si.
- Não é necessário tráfego passar pela internet — a comunicação é feita pela backbone privada da AWS.

## Fluxo de Rede Comum

Exemplo de fluxo de comunicação para uma instância privada acessar a internet:
