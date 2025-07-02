```bloco de comando```

# Registro de Atividades TEMA-04

Este documento é um registro dos passos que realizei para configurar e sincronizar uma pasta em uma instância EC2 com um bucket no Amazon S3.

## 1. Configuração Inicial na AWS
Primeiro, realizei as seguintes configurações no painel da AWS:

- Utilizei minha conta pessoal da AWS.

- Criei uma nova instância EC2 (usando o Free Tier) e baixei o par de chaves SSH (.ppk) gerado durante o processo.

- Criei um bucket de uso geral no S3, que nomeei de ``meu-bucket-teste-teste``.

- Para a autenticação da CLI, gerei um Access Key ID e uma Secret Access Key.

> Nota: Para este procedimento, utilizei as chaves do usuário root. Fica o registro de que a prática recomendada é sempre criar um usuário IAM com permissões mínimas.

## 2. Conexão com a Instância EC2
Para acessar a instância, segui estes passos:

- Baixei e instalei o PuTTY no meu computador.

- Iniciei uma conexão SSH usando o PuTTY, configurando o IP público da instância (ec2-user@<ip-publico>) e associando a chave .ppk salva para autenticação.

## 3. Preparação do Ambiente na EC2
Dentro da sessão SSH da instância EC2, executei os seguintes comandos:

- Criei o diretório ``TEMA-04``.
  
```
mkdir TEMA-04
```

- Naveguei para dentro da pasta recém-criada.

```
cd TEMA-04
```

- Criei um arquivo de texto de exemplo chamado ``teste-texto.txt`` com o editor vim.

```
vim teste-texto.txt
```

## 4. Configuração da AWS CLI
Para permitir que a instância se comunicasse com o S3, configurei a AWS CLI:

- Rodei o comando de configuração.

```
aws configure
```

- Informei meu AWS Access Key ID, AWS Secret Access Key e a região padrão (Default region name) quando solicitado pelo prompt.

## 5. Sincronização dos Arquivos com S3
Finalmente, realizei a sincronização dos dados entre a EC2 e o S3.

- Usei o comando aws s3 sync para enviar a pasta local para o bucket S3 (Upload), dentro de um "diretório" de mesmo nome.

```
aws s3 sync "/home/ec2-user/TEMA-04" "s3://meu-bucket-teste-teste/TEMA-04"
```
- Para testar o caminho inverso, executei o mesmo comando, apenas invertendo a origem e o destino (Download).

```
aws s3 sync "s3://meu-bucket-teste-teste/TEMA-04" "/home/ec2-user/TEMA-04"
```
