# Produzindo e consumindo mensagens da fila SQS ☁️

## Descrição

Neste projeto, compartilho a minha experiência ao trabalhar com o Amazon SQS usando Java. Durante essa jornada, explorei como enviar e receber mensagens em uma fila local usando o LocalStack.

## Pré-Requisitos 🛠️

Antes de começar, você precisará ter os seguintes itens instalados:

- **Docker** 🐳: Para executar o LocalStack.
- **AWS CLI** 📡: Para interagir com o SQS localmente.
- **Java JDK** ☕: Para compilar e executar o código Java.

## Passo a Passo 🛠️

1. **Instalação do LocalStack** 🐳
   - Inicie o LocalStack utilizando o Docker com o seguinte comando:
     ```bash
     localstack start
     ```

2. **Criação da Fila SQS** 📦
   - Após configurar o LocalStack, crie uma fila chamada "MinhaFila" através do comando AWS CLI:
     ```bash
     aws --endpoint-url=http://localhost:4566 sqs create-queue --queue-name MinhaFila
     ```

3. **Listar Filas SQS** 📋
   - Para confirmar que a fila foi criada, execute:
     ```bash
     aws --endpoint-url=http://localhost:4566 sqs list-queues
     ```

4. **Configuração do Cliente SQS em Java** 💻
   - No meu código Java, utilizei o SDK da AWS para criar um cliente SQS. Aqui, o mais importante foi especificar o endpoint do LocalStack:
     ```java
     SqsClient sqsClient = SqsClient.builder()
                     .region(Region.US_EAST_1)
                     .endpointOverride(URI.create("http://localhost:4566"))
                     .build();
     ```
   - Esse endpoint é crucial porque estou interagindo com a versão local do SQS, não com a AWS real.

5. **Envio e Recepção de Mensagens** 📬
   - Com o cliente configurado, foi possível enviar mensagens para a fila e, em seguida, recebê-las.

6. **Reflexões Finais** 🤔
   
    Neste projeto, tive a oportunidade de aprender sobre a configuração do cliente SQS e a gestão de mensagens. Foi possível entender como definir a região e o endpoint para me comunicar com o serviço SQS, utilizando o LocalStack como simulação local da AWS.
    Através da exploração das operações de envio e recebimento de mensagens, pude ver como funcionam os sistemas baseados em filas. Além disso, enfrentei e resolvi desafios relacionados à configuração do ambiente.

    <img src="https://github.com/user-attachments/assets/f91dfcf6-f453-49e7-8d13-14b8e6b2fa9b" alt="captura tela localstack" width="750"/>
    <img src="https://github.com/user-attachments/assets/1902ccc3-13a9-4962-8bea-6177a97519ad" alt="captura tela sqsproducer" width="750"/>
    <img src="https://github.com/user-attachments/assets/59366cca-7b0d-46b1-8cc8-d745dce8eaa6" alt="captura tela sqsconsumer" width="750"/>


