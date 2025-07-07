# Registro de Atividades TEMA-05

Este documento é um registro dos passos que realizei para configurar e sincronizar uma pasta em uma instância de VM (Google Compute Engine) com um bucket no Google Cloud Storage.

### **1. Configuração Inicial no Google Cloud Platform (GCP)**

Primeiro, realizei as seguintes configurações no painel do GCP:

* Utilizei minha conta pessoal do Google Cloud Platform.
* Criei uma nova instância de VM no Compute Engine, chamada `instancia-teste`.
* Criei um bucket de uso geral no Google Cloud Storage, que nomeei de `meu-bucket-teste-dev`.
* Autentiquei a `gcloud` CLI na VM, permitindo que o `gsutil` interagisse com o bucket.

### **2. Preparação do Ambiente na Instância**

Dentro da sessão SSH da instância, executei os seguintes comandos:

* Criei o diretório `TEMA-05`.
    ```bash
    mkdir TEMA-05
    ```
* Naveguei para dentro da pasta recém-criada.
    ```bash
    cd TEMA-05
    ```

### **3. Sincronização dos Dados (Bucket -> VM)**

* Usei o comando `gsutil rsync` para baixar e sincronizar o conteúdo do bucket para a minha pasta local na VM.

    ```bash
    gsutil rsync -r "gs://meu-bucket-teste-dev/TEMA-05" "/home/gustavoccvilela/TEMA-05"
    ```

### **4. Modificação Local e Sincronização (VM -> Bucket)**

* Dentro da pasta `TEMA-05`, criei um novo arquivo de texto de exemplo.
    ```bash
    vim GoogleCloudBasic.txt
    ```
* Para enviar o novo arquivo de volta para o bucket (Upload), executei novamente o comando `gsutil rsync`, invertendo a origem e o destino.
    ```bash
    gsutil rsync -r "/home/gustavoccvilela/TEMA-05" "gs://meu-bucket-teste-dev/TEMA-05"
    ```
