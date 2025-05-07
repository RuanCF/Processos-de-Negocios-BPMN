# Tema: Pedido de Comida via Aplicativo com Pagamento e Entrega
Este projeto apresenta uma modelagem detalhada do processo de solicitação de comida por meio de um aplicativo, abrangendo algumas das etapas desde o login do cliente até a confirmação final de entrega. O fluxo contempla diferentes possibilidades operacionais, incluindo falhas no pagamento, rejeição de pedidos pelo restaurante, ausência de entregadores disponíveis e problemas no momento da entrega ao cliente.

## Participantes e Raias (Swimlanes):
### Cliente
Responsável por iniciar e acompanhar todo o processo. Realiza o login ou cadastro, seleciona o endereço de entrega, escolhe os itens desejados, define a forma de pagamento e acompanha o andamento do pedido até sua conclusão.

### Aplicativo (Sistema)
Atua como intermediador entre os envolvidos (cliente, restaurante e entregador). É responsável por validar pagamentos, gerenciar o envio de dados entre as partes e notificar os participantes sobre o andamento do pedido.

### Restaurante
Recebe os pedidos do sistema, decide pela aceitação ou recusa, realiza o preparo dos pedidos aceitos e sinaliza ao sistema quando estiverem prontos para retirada.

### Entregador
Responsável pela logística de entrega. Aceita ou recusa a corrida, realiza a retirada do pedido no restaurante e executa a entrega ao cliente. Caso enfrente dificuldades, como ausência de resposta do cliente, comunica-se com o restaurante para buscar uma solução.

Observação: O modelo considera que o restaurante não possui entregadores próprios fixos, utilizando um sistema de entrega terceirizado.


# Descrição das Etapas do Processo
## Login / Registrar (Cliente)
### Descrição:
O cliente inicia o processo acessando sua conta pessoal por meio de login ou, se for a primeira utilização, realizando o registro com informações básicas (nome, e-mail, senha, telefone). Essa autenticação é essencial para garantir segurança, associar o pedido a um perfil individual, acessar histórico de pedidos, endereços salvos e métodos de pagamento previamente cadastrados. Além disso, permite a personalização de ofertas e comunicação com o cliente ao longo do processo.

## Adicionar Endereço (Cliente)
### Descrição:
O cliente insere um novo endereço de entrega ou seleciona um previamente salvo em sua conta. Essa informação é crítica para verificar a área de cobertura dos restaurantes, estimar o tempo de entrega, calcular a taxa de deslocamento (se aplicável) e fornecer instruções precisas ao entregador. O endereço pode incluir referências adicionais, como número de apartamento ou pontos de referência.

## Escolher o Item (Cliente)
### Descrição:
O cliente navega no aplicativo e seleciona um restaurante disponível com base em filtros (ex: tipo de comida, Taxa de entrega, avaliações). Em seguida, escolhe os itens desejados no cardápio, podendo ajustar quantidades, adicionar complementos, remover ingredientes ou incluir observações específicas (ex.: “sem cebola”).

## Escolher Forma de Pagamento (Cliente)
### Descrição:
O cliente opta por uma forma de pagamento entre as disponíveis, como cartão de crédito ou débito, PIX, dinheiro. A escolha impacta diretamente a validação do pedido e pode influenciar a logística (por exemplo, necessidade de troco para pagamento em dinheiro). O sistema também pode permitir o salvamento de métodos de pagamento para uso futuro.

## Validar Pagamento (Sistema)
### Descrição:
O sistema realiza automaticamente a verificação do método de pagamento selecionado. Em casos de pagamento eletrônico (como cartão ou PIX), uma solicitação é enviada ao provedor de pagamentos (gateway), aguardando autorização.

## Falha no Pagamento (Sistema)
### Descrição:
Se o gateway retornar uma falha na transação (ex: saldo insuficiente, cartão vencido, chave PIX inválida), o sistema imediatamente notifica o cliente, informando o motivo da recusa. O processo é então pausado, e o cliente tem a oportunidade de revisar ou trocar o método de pagamento para tentar novamente, garantindo continuidade sem perda do pedido montado.

## Enviar Pedido para o Restaurante (Sistema)
### Descrição:
Com o pagamento confirmado, o sistema envia automaticamente o pedido ao restaurante selecionado, incluindo todos os detalhes necessários: itens, quantidades, personalizações, endereço completo de entrega e instruções adicionais.

## Receber Pedido (Restaurante)
### Descrição:
O restaurante recebe o novo pedido através de seu sistema de atendimento (painel, aplicativo parceiro ou terminal integrado). A solicitação é exibida com todos os dados relevantes para análise de viabilidade (itens, localização de entrega, etc.).

## Avaliar Capacidade (Restaurante)
### Descrição:
O restaurante avalia se consegue atender ao pedido naquele momento. Fatores considerados incluem disponibilidade de ingredientes, equipe de cozinha, tempo estimado, horário de funcionamento, entre outros. Essa avaliação evita pedidos que não possam ser cumpridos com qualidade.

## Rejeitar Pedido (Restaurante)
### Descrição:
Se o restaurante determinar que não é possível cumprir o pedido (por restrições operacionais, ausência de insumos, excesso de demanda, etc.), ele o recusa pelo sistema. A recusa aciona uma notificação automática ao cliente, encerrando o processo daquele pedido.

## Confirmar Pedido (Restaurante)
### Descrição:
Caso aceite o pedido, o restaurante confirma a solicitação no sistema, liberando formalmente a etapa de preparo. Essa ação também pode disparar uma notificação ao cliente, informando que o pedido foi aceito e está sendo processado.

## Preparar Pedido (Restaurante)
### Descrição:
O restaurante inicia a produção dos itens solicitados, conforme as especificações do cliente. O preparo segue o tempo padrão da cozinha e pode ser ajustado com base em complexidade ou volume de pedidos. Ingredientes, embalagens e padrões de qualidade.

## Notificar Sistema: Pedido Pronto (Restaurante)
### Descrição:
Quando o pedido está finalizado e embalado para retirada, o restaurante envia uma notificação ao sistema. Essa comunicação sinaliza o fim da etapa de preparo e permite que o aplicativo inicie o processo de alocação de entregador, otimizando o tempo entre preparo e entrega.

## Notificar Entregadores (Sistema)
### Descrição:
O sistema identifica entregadores disponíveis na região e envia notificações com os detalhes da corrida: localização do restaurante, itens do pedido, destino da entrega e valor da remuneração. Os entregadores interessados podem aceitar a solicitação em tempo real, iniciando a logística de entrega.

## Escolher a Corrida (Entregador)
### Descrição:
Após o sistema identificar entregadores disponíveis, uma notificação contendo as informações da corrida (local de retirada, destino, valor estimado, distância e tempo previsto) é enviada aos entregadores. Eles têm a opção de aceitar ou recusar. O tempo de resposta é limitado para garantir agilidade. Pode haver rejeições múltiplas.

## Aceitar corrida (Entregador)
### Descrição: 
Quando um entregador aceita a corrida, o sistema registra sua decisão, bloqueia a oferta para os demais entregadores e envia a ele os dados detalhados do pedido, localização do restaurante e rota de entrega. O restaurante é notificado de que o entregador está a caminho para retirada. Essa ação também atualiza o status do pedido no painel do cliente.

## Recusar corrida (Entregador)
### Descrição:
Caso o entregador recuse a corrida ou não responda dentro do tempo limite, o sistema registra essa recusa e envia a oferta para outro entregador disponível. O número de recusas pode ser usado para ajustar algoritmos de prioridade de oferta. Se todos os entregadores disponíveis recusarem, o sistema aciona medidas alternativas.

## Notificar Atraso (Sistema)
### Descrição:
Se nenhuma aceitação ocorrer dentro de um tempo determinado (ex.: 3 a 5 minutos), o sistema envia automaticamente uma notificação ao cliente informando que a entrega pode sofrer atraso devido à indisponibilidade temporária de entregadores. O status do pedido é mantido em espera até que algum entregador aceite ou novas alternativas sejam acionadas (como outro restaurante ou pedido cancelado com reembolso).

## Buscar Pedido no Restaurante (Entregador)
### Descrição:
Após aceitar a corrida, o entregador segue para o local do restaurante utilizando as informações fornecidas pelo sistema, como endereço, nome do estabelecimento, e eventuais instruções específicas (por exemplo, “retirada no balcão lateral” ou “informar número do pedido”).

## Pedido Retirado (Entregador)
### Descrição:
Ao chegar, o entregador confirma sua chegada via aplicativo, permitindo ao restaurante identificar e validar a retirada. Confirmando de que está com o pedido em mãos.

## Realizar Entrega ao Cliente (Entregador)
### Descrição:
O entregador se desloca até o endereço de entrega informado pelo cliente durante o pedido. O trajeto pode ser monitorado em tempo real tanto pelo cliente quanto pelo restaurante, possibilitando o acompanhamento da entrega. O sistema utiliza geolocalização para otimizar o trajeto e estimar o tempo de chegada.

## Cliente Atendeu
### Descrição:
Após as tentativas de contato, o cliente responde ao entregador (seja por atendimento presencial, ligação, mensagem ou interfone). Com a confirmação, o entregador pode prosseguir com a entrega do pedido.

## Contato com Cliente (Entregador)
### Descrição:
Ao chegar ao local de entrega, o entregador tenta realizar a entrega diretamente ao cliente. Essa tentativa inicial pode envolver tocar a campainha, chamar pelo interfone ou simplesmente bater à porta, conforme a situação permitir. Essa ação representa o primeiro esforço de entrega presencial, com base nas informações fornecidas no pedido. Caso não haja resposta imediata, o entregador deve iniciar procedimentos adicionais de contato, conforme protocolos estabelecidos pelo aplicativo.

## Tentar Contato com Cliente (Entregador)
### Descrição:
Diante da ausência de resposta no primeiro contato, o entregador ativa métodos alternativos para localizar o cliente. Isso pode incluir ligações telefônicas para o número cadastrado, envio de mensagens via aplicativo ou SMS, ou novos toques no interfone. O objetivo é confirmar a disponibilidade do cliente e evitar o insucesso da entrega. O sistema registra automaticamente todas as tentativas realizadas, servindo como histórico de tentativas válidas e base para decisões posteriores no fluxo do processo.

## Cliente Não Responde
### Descrição:
Se, após diversas tentativas, o cliente permanece inacessível, o entregador deve acionar o restaurante por meio do sistema. O contato visa informar a falha na entrega e obter orientação sobre os próximos passos, como aguardar por mais tempo, retornar o pedido ou descartar conforme políticas da plataforma.

## Entrar em Contato com Restaurante (Entregador)
### Descrição:
Caso o cliente não responda após várias tentativas, o entregador aciona o restaurante em busca de orientação. Essa comunicação tem como objetivo decidir os próximos passos, que podem incluir aguardar por mais tempo, retornar com o pedido ao restaurante, ou redirecionar a entrega conforme diretrizes internas. O contato pode ser feito por telefone, chat do aplicativo ou outros canais estabelecidos.

## Encerrar Pedido (Sistema)
### Descrição:
Quando não é possível concluir a entrega (seja por ausência do cliente, falhas de comunicação ou problemas operacionais) o sistema encerra o pedido como "não entregue". Esse encerramento automático ou manual inclui o registro do incidente com informações como horário da tentativa, localização do entregador e histórico de contato. Em casos aplicáveis, o sistema aciona o processo de reembolso total ou parcial ao cliente e também gera alertas para análise posterior.

## Entrega Confirmada (Cliente)
### Descrição:
Após o recebimento do pedido, o cliente acessa o aplicativo para confirmar a entrega. Essa confirmação serve como validação final do processo logístico, liberando o pagamento ao entregador (se for o caso) e finalizando o atendimento. A confirmação pode ser manual (botão "Pedido Recebido") ou automática, dependendo da configuração do sistema (por exemplo, após reconhecimento de entrega pelo entregador).

## Feedback Final (Cliente)
### Descrição:
Com o pedido finalizado, o sistema convida o cliente a avaliar sua experiência por meio de uma nota e/ou comentário. A avaliação pode abranger a qualidade da comida, o tempo de entrega, o atendimento do entregador e a experiência geral com o aplicativo. Esse feedback é essencial para aprimorar o serviço, alimentar algoritmos de recomendação e fornecer dados relevantes a restaurantes e operadores logísticos. Além disso, avaliações negativas podem acionar protocolos de suporte ao cliente.

# Possíveis Melhorias
- Implementação de funcionalidade como links, mensagens e dados(se aplicáveis).
- Desenvolvimento em outro site ou programa, para uma melhora visual.
- Melhora no fluxo do diagrama.

# Melhorias aplicadas após apresentação prévia
- Melhor desenvolvimento da documentação do processo de cada etapa.

![bpmn project image](https://github.com/RuanCF/Processos-de-Negocios-BPMN/blob/main/ProcessosDeNeg%C3%B3ciosBPMN.jpg)
