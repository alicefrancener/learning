# Designing a Notifications Service with SQS and SNS

Article: [Designing a Notifications Service with SQS and SNS](https://itnext.io/designing-a-notifications-service-with-sqs-and-sns-176adad42fa1)

## Objetivos:

- Enviar notificações aos usuários em reposta a eventos do sistema
- Outros serviços não precisam saber sobre as notificações
- Os eventos podem se originar de diferentes serviços e podemos enviá-los ao usuários por múltiplos canais (push notivications, slack messages, etc).
- Deve ser fácil e rápido alterar o texto das notificações e quando/onde são entregues

## Opções

1. APIs de serviços individuais enviam notificações diretamente por meio de APIs  para slack, iOS, etc.
2. APIs de serviços individuais enviam notificações para Amazon SNS. Nós criamos um Amazon SQS para cada canal que queremos enviar notificações. Então ter um serviço de notificação para cada um desses canais. Cada serviço de notificação "escuta" por novas mensagens na fila SQS e tem a responsabilidade de mandar notificação.

Apesar da opção 1 ser a mais rápida para ser implementada seria mais difícil para escalar, uma vez que cada serviço de API precisaria lidar com a complexidade de enviar cada tipo de notificação.

## Diagramas de sistema

- *Diagrama 1*: cada serviço de API teria seu tópico SNS no qual publica eventos (ex. tópico de contatos, tópico de vendas). Cada serviço de notificação (ex. slack service, whatsapp service) teria sua fila SQS (ex. fila slack, fila whatsapp), e essa fila SQS é subscrita a múltiplos tópicos SNS.
- *Diagrama 2*: cada serviço de API envia eventos para somente um tópico SNS compartilhado. Cada serviço de notificação (ex. slack service, whatsapp service) teria sua fila SQS (ex. fila slack, fila whatsapp) que é subscrita ao único tópico de notificação SNS.

## Conteúdo do evento

Os eventos que fluem nesses sistema pode ter dois formatos

1. Descreve **o que aconteceu** (exemplo: um contato foi editado). Nesse caso, o serviço de notificação teria a responsabilidade de decidir como lidar com essa notificação.
2. Descreve **o que deve acontecer** (exemplo: diz qual notificação mandar, no formato definido, quais usuários notificar). O serviço de notificação não precisa saber sobre o domínio do negócio, só precisa saber como mandar a mensagem.

## APIs pública e encapsulamento

- **Qual o limite ao redor de cada serviço? Qual é a API pública de cada serviço?**
  - **Diagrama 1:**
    - Cada par de API & tópico SNS são agrupados em um serviço (ex. Sales API & Sales SNS Topic)
    - Você pode subscrever ao tópico SNS para receber eventos desse serviço de API
    - O serviço de notificação não tem uma API pública, ao invés disso eles consomem os endpoints das APIs SNS e enviam para os serviços externos (ex. Whatsapp SQS consome de algum tópico e é consumido pelo Whatsapp Service que envia a notificação para o Whatsapp).
  - **Diagrama 2:**
    - No diagrama 2, com o tópico SNS compartilhado tudo fica um pouco mais arbitrário. O tópico SNS não pode fazer parte dos serviços de API porque se não estariam pertencendo a múltiplos serviços.
    - Nesse casso ele precisaria de sua própria API pública para os serviços de API que enviam notificação para ele e também para os serviços de notificações.

Logo, é mais fácil que cada serviço tenha seu tópico SNS separado.

Considerando, por outro lado o conteúdo do evento, também fica claro que o tipo de mensagem e o que fazer com ela é uma preocupação do serviço de notificação. Dessa forma, é melhor seguir com o modelo de conteúdo de mensagem que descreve um evento que ocorreu e não qaul notificação deveria ser enviada.

## Tradeoffs

- Serviços de API cientes da estrutura e conteúdo das notificações push
  - Nesse caso precisaria de uma única estrutura de evento para vários serviços de notificação que são diferentes
  - Os eventos também não poderiam ser reusados facilmente se quisermos gerar outras ações em reposta a mudanças nas APIs
- Serviço de notificação cientes do dados do negócio
  - Dessa forma o serviço de notificação fica menos abstrato
  - Adicionar uma notificação para um evento totalmente novo envolve duas outras mudanças: adicionar o evento no serviço de API e adicionar um handler para o evento no serviço de notificação

Nesse caso, mesmo que o custo de seguir com a segunda escolha (*serviço de notificação cientes do dados do negócio*) seja maior, o custo é compensando pelo benefício , uma vez que simplificará os serviços de API. Além disso, todo o template da mensagem e a lógica para decidir qual notificação mandar estará centralizado em um lugar.
