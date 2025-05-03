# Modelagem de Processos com BPMN

### Objetivo
Desenvolver a capacidade de interpretar e modelar processos de negócios utilizando a notação BPMN. Esta atividade visa reforçar o entendimento dos elementos e simbologia da notação, além de promover a prática de modelagem de processos reais ou fictícios.

## Instruções
### Análise de Processos Existentes
Análise de Processos Existentes: Escolha um processo de negócio com o qual você tenha familiaridade (pode ser um processo simples do cotidiano, como "Pedido de Compra Online", ou um processo mais técnico, como "Desenvolvimento de Software").

### Modelagem do Processo em BPMN
Usando uma ferramenta de modelagem BPMN, siga os passos abaixo:
- Defina o nome do processo que será modelado.
- Identifique e crie piscinas e raias (swimlanes) se necessário, para organizar as diferentes áreas ou participantes do processo.
- Modele o fluxo do processo, usando:
- Eventos iniciais e finais.
- Atividades, representando as ações ou tarefas realizadas durante o processo.
- Gateways, para identificar pontos de decisão no processo (ex.: se sim, faça isso; se não, faça aquilo).
- Fluxos de sequência, conectando eventos, atividades e gateways.
- Outros artefatos como mensagens, dados, entre outros, conforme necessário.

### Validação do Processo 
Após a criação do diagrama, valide seu processo verificando:
- Se todos os eventos possuem uma conexão lógica.
- Se o fluxo do processo segue uma sequência coerente.
- Se as decisões (gateways) têm resultados bem definidos.


### Documentação do Processo
Junto com o diagrama BPMN, entregue uma documentação breve explicando:
- Qual é o objetivo do processo.
- Quem são os principais participantes.
- Descrição de cada atividade representada no modelo.
- Possíveis melhorias ou otimizações que poderiam ser feitas no processo.

## Exemplos de Processos que Podem Ser Modelados:
- Processo de Compra em Loja Virtual
- Processo de Aprovação de Férias
- Desenvolvimento de um Projeto de Software
- Atendimento ao Cliente em um Call Center
- Processo de Abertura de Chamado em Suporte Técnico

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Tema escolhido: Pedido de Comida via Aplicativo com Pagamento e Entrega
Modelagem de forma clara e "quase" completa do processo de solicitação de comida através de um aplicativo, envolvendo as etapas desde o login do cliente até a entrega do pedido e confirmação de recebimento. O processo contempla situações de falha no pagamento, rejeição de pedido, ausência de entregador, e falhas na entrega.

## Participantes e Raias (Swimlanes)
#### 1. Cliente
Responsável por iniciar o processo, realizando login, escolhendo itens, definindo o endereço e forma de pagamento, e acompanhando a entrega até o recebimento do pedido.

#### 2. Aplicativo (Sistema)
Atua como intermediário entre cliente, restaurante e entregador. Valida o pagamento, gerencia o fluxo das informações e envia notificações.

#### 3. Restaurante
Recebe os pedidos, decide se irá aceitá-los ou não, prepara os pedidos aceitos e informa ao sistema quando estiverem prontos para retirada.

#### 4. Entregador
Responsável por aceitar a corrida, retirar o pedido no restaurante e entregá-lo ao cliente, com manejo de exceções caso o cliente não esteja disponível.

OBS.: Projeto está montado em cima do conceito de que o restaurante não apresenta um entregador fixo.

## Descrição das Etapas do Processo
#### Início do Processo (Cliente)
Login / Registrar: Cliente acessa ou cria uma conta no aplicativo.

Adicionar Endereço: Define onde o pedido será entregue.

Escolher o Item: Seleciona os produtos desejados.

Escolher Forma de Pagamento: Escolhe entre cartão, PIX, dinheiro, etc.

#### Validação de Pagamento (Aplicativo)
Validar Pagamento: Sistema verifica a autorização da transação.

Se pagamento for inválido: Notifica falha ao cliente e o processo continuar com outro tentativa de pagamento.

Se for autorizado: Envia o pedido ao restaurante.

Feedback ao restaurante: após a confirmação do recebimento, cliente pode realizar ou não um feedback e terminando o processo

#### Confirmação pelo Restaurante
Receber Pedido: Restaurante recebe a solicitação.

Aceita Pedido?

Se não: Rejeita pedido e encerra o processo notificando o cliente.

Se sim: Confirma o pedido e inicia preparo.


Preparo do Pedido

Preparar Pedido: Restaurante realiza o preparo.

Pedido Pronto: Restaurante notifica o sistema.

#### Entrega do Pedido
Notificar Entregadores: Sistema busca entregadores disponíveis.

Aceita Corrida?

Se não: Notifica atraso ao cliente.

Se sim: Entregador aceita e busca o pedido.

Buscar Pedido no Restaurante: Entregador realiza a coleta.

Pedido Retirado: Pedido sai do restaurante.

#### Entrega ao Cliente
Realizar Entrega ao Cliente

Cliente Responde?

Se sim: Pedido é entregue.

Se não: Entregador tenta contato com cliente. Se não, entregador entra em contato com o restaurante. Caso não resolvido, pedido é encerrado como não entregue.

# Possíveis Melhorias
- Implementação de funcionalidade como links, mensagens e dados(se aplicáveis).
- Melhora no fluxo do diagrama
