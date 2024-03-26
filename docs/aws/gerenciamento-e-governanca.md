# Gerenciamento e governança

## Amazon CloudWatch

- É um serviço da web que permite monitorar e gerenciar várias métricas e configurar ações de alarme com base nos dados dessas métricas.
- Os serviços da AWS enviam métricas para o _CloudWatch_.
    - O CloudWatch usa essas métricas para criar gráficos automaticamente que mostram como o desempenho mudou ao longo do tempo.

### CloudWatch alarm

- Com o _CloudWatch_, você pode criar alarmes que executam ações automaticamente se o valor de sua métrica estiver acima ou abaixo de um limite predefinido.
- Exemplo de aplicação:
    - Suponha que os desenvolvedores de sua empresa usem instâncias do Amazon EC2 para fins de desenvolvimento ou teste de aplicativos. Se os desenvolvedores ocasionalmente esquecerem de parar as instâncias, as instâncias continuarão em execução e incorrerão em cobranças.
    - Nesse cenário, você pode criar um alarme do _CloudWatch_ que interrompa automaticamente uma instância do Amazon EC2 quando a porcentagem de utilização da CPU permanecer abaixo de um determinado limite por um período especificado. 
- Ao configurar o alarme, você pode especificar para receber uma notificação sempre que este alarme for acionado.

### CloudWatch dashboard

- Permite acessar todas as métricas de seus recursos em um único local.
- Exemplo de aplicação:
    - Você pode usar um painel do _CloudWatch_ para monitorar a utilização da CPU de uma instância do Amazon EC2, o número total de solicitações feitas a um bucket do Amazon S3 e muito mais.
- Você pode personalizar dashboards separados para diferentes finalidades de negócios, aplicativos ou recursos.

## AWS CloudTrail

- Registra chamadas de API para sua conta, como um log de ações.
    - As informações registradas incluem a identidade do chamador da API, a hora da chamada da API, o endereço IP de origem do chamador da API e muito mais.
- Você pode visualizar um histórico completo da atividade do usuário e chamadas de API para seus aplicativos e recursos.
- Os eventos geralmente são atualizados no _CloudTrail_ dentro de **15 minutos** após uma chamada de API.
- Você pode filtrar eventos especificando a hora e a data em que ocorreu uma chamada de API, o usuário que solicitou a ação, o tipo de recurso envolvido na chamada de API e muito mais.

### CloudTrail Insights

- No _CloudTrail_, você também pode habilitar o _CloudTrail Insights_.
- Esse recurso opcional permite que o _CloudTrail_ detecte automaticamente atividades de API incomuns em sua conta da AWS.
- Exemplo de aplicação:
    - Pode detectar que um número maior de instâncias do Amazon EC2 do que o normal foi iniciado recentemente em sua conta.
    - Você pode então revisar os detalhes completos do evento para determinar quais ações você precisa realizar em seguida.

## AWS Trusted Advisor

- É um serviço da web que inspeciona seu ambiente da AWS e fornece **recomendações em tempo real** de acordo com as melhores práticas da AWS.
- Compara suas descobertas com as melhores práticas da AWS em cinco categorias:
    - **otimização de custos**
    - **desempenho**
    - **segurança**
    - **tolerância a falhas**
    - **limites de serviço**
- Para as verificações em cada categoria, o Trusted Advisor oferece uma lista de ações recomendadas e recursos adicionais para saber mais sobre as melhores práticas da AWS.
- Pode beneficiar sua empresa em todos os estágios de implantação.
- Exemplo de aplicação:
    - Você pode usar o AWS Trusted Advisor para ajudá-lo enquanto cria novos fluxos de trabalho e desenvolve novos aplicativos.
    - Pode usá-lo enquanto faz melhorias contínuas em aplicativos e recursos existentes.

### AWS Trusted Advisor dashboard

- Mostrando o número de itens sem problemas detectados, investigações recomendadas e ações recomendadas para as categorias de otimização de custos, desempenho, segurança, tolerância a falhas e limites de serviço.
- Para cada categoria:
    - A verificação verde indica o número de itens para os quais não detectou problemas.
    - O triângulo laranja representa o número de investigações recomendadas.
    - O círculo vermelho representa o número de ações recomendadas.

## AWS CloudFormation

- É um serviço que ajuda você a modelar e configurar seus recursos da AWS.
- Você cria um modelo (em inglês, _template_) que descreve todos os recursos da AWS que você deseja e o CloudFormation cuida do provisionamento e da configuração desses recursos para você.
- Não é necessário criar e configurar individualmente os recursos da AWS e descobrir o que depende do que; o CloudFormation lida com isso.

## Auto Scaling

### Amazon EC2 Auto Scaling

- Escalona automaticamente instâncias **EC2** conforme necessário.
- Você pode usar duas abordagens:
    - Dimensionamento dinâmico (_Dynamic scaling_): responde à demanda em constante mudança.
    - Dimensionamento preditivo (_Predictive scaling_): agenda automaticamente o número certo de instâncias do Amazon EC2 com base na demanda prevista.
- Ao configurar o tamanho do _Auto Scaling group_, você pode definir o número mínimo, desejado e máximo de instâncias do Amazon EC2.
    - Se a quantidade desejada não for definida, será utilizada a quantidade mínima.

### Application Auto Scaling

- O _Application Auto Scaling_ é um serviço da Web para desenvolvedores e administradores de sistemas que precisam de uma solução para escalar automaticamente os recursos escaláveis para serviços individuais da AWS para além do Amazon EC2.
- O _Application Auto Scaling_ permite que você configure a escalabilidade automática para os seguintes recursos:
    - Frotas do AppStream 2.0
    - Réplicas do Aurora
    - Classificação de documentos e endpoints de reconhecimento de entidade do Amazon Comprehend
    - Tabelas e índices secundários globais do DynamoDB
    - Serviços do Amazon Elastic Container Service (ECS)
    - ElastiCache para clusters Redis (grupos de replicação)
    - Clusters do Amazon EMR
    - Tabelas do Amazon Keyspaces (for Apache Cassandra)
    - Simultaneidade provisionada pela função do Lambda
    - Armazenamento de agente do Amazon Managed Streaming for Apache Kafka (MSK)
    - Clusters do Amazon Neptune
    - Variantes de endpoint do SageMaker
    - Solicitações de frota spot
    - Os recursos personalizados fornecidos por seus próprios aplicativos ou serviços.

#### Scheduled scaling (Escalabilidade programada)

- Escalabilidade com base em uma programação
    - Permite que você defina sua própria programação de escalabilidade de acordo com alterações de carga previsíveis. Por exemplo, vamos supor que toda semana o tráfego para sua aplicação Web comece a aumentar na quarta-feira, permaneça alto na quinta-feira e comece a diminuir na sexta-feira. É possível configurar uma programação para o Application Auto Scaling para aumentar a capacidade na quarta-feira e diminuir a capacidade na sexta-feira.

#### Step scaling (Escalabilidade em etapas)

- Escale um recurso com base em um conjunto de ajustes de escalabilidade que variam de acordo com o tamanho da ruptura do alarme do _CloudWatch_.
    - Com a escalabilidade em etapas, você escolhe valores de métricas e limites de escalabilidade para os alarmes do _CloudWatch_ que acionam o processo de escalabilidade, além disso, você define como seu destino escalável deve ser escalado quando o limite é a falha para um número especificado de períodos de avaliação.

#### Target tracking scaling (Escalabilidade de monitoramento do objetivo)

- Escale um recurso com base em um valor de destino para uma métrica específica do _CloudWatch_.
    - Para criar uma política de escalabilidade com monitoramento de objetivo, você especifica uma métrica do _Amazon CloudWatch_ e um valor de objetivo que representa a utilização média ideal ou o nível de _throughput_ para seu aplicativo. Em seguida, o _Application Auto Scaling_ pode aumentar a escala horizontalmente do destino dimensionável (adicionar capacidade) para processar picos de tráfego, e reduzir a escala horizontalmente do destino dimensionável (remover capacidade) para reduzir custos durante períodos de baixa utilização ou throughput.
    - Por exemplo, digamos que você tenha um aplicativo atualmente executado em uma frota _spot_ e queira que a utilização de CPU da frota permaneça próximo de 50% quando a carga no aplicativo mudar. Isso fornece capacidade extra para lidar com picos de tráfego sem manter um número excessivo de recursos ociosos. Você pode satisfazer essa necessidade criando uma política de escalabilidade com monitoramento de objetivo visando uma utilização média de 50% da CPU. Em seguida, o _Application Auto Scaling_ dimensionará o número de instâncias para manter o valor efetivo da métrica em ou perto de 50%.

## Quiz

1. Para garantir que todos os recursos da AWS em sua VPC não ultrapassem o limite de serviço. Qual serviço pode ajudar nesta tarefa?
    - **Resposta**: AWS Trusted Advisor

## Referências

- <https://explore.skillbuilder.aws/learn/course/134/play/31418/aws-cloud-practitioner-essentials-all-modules>
