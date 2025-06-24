# ELK Stack - Descrição do Laboratório

Este laboratório tem o intuito de mostrar algumas funcionalidades da plataforma open source Elastic Stack(ELK), sendo composta por quatro componentes: Elasticsearch, Logtash, Kibana e Beats. Mas afinal, o que é essa plataforma ELK? Ela tem várias funcionalidades, e para o nosso uso na cibersegurança ela se torna interessante para visualizar dados, análise de logs, detecção de ameaças, monitoramento de infraestrutura e segurança. No Kibana, da qual esse laboratório irá dar mais ênfase, ele permite ao usuário criar dashboards, gráficos e tabelas com os dados armazenados no Eletricsearch. Outro ponto positivo referente ao Elastic Stack, é que ele pode ser uma base para construir um SIEM(Security Information and Event Management), ficando devendo apenas recursos referentes à correlações de eventos, alertas e gerenciamento de incidentes. 

Depois de apresentado as principais funcionalidades do Kibana, iremos resolver um desafio do TryHackMe, simulando um ambiente SOC, utilizando as ferramentas do Kibana perante a uma detecção de ameaça.

# Visão Geral - Elastic Stack

<a href='https://postimages.org/' target='_blank'><img src='https://i.postimg.cc/CKr3LdVZ/elk.jpg' border='0' alt='elk'/></a>

Elastic Stack é uma coleção de diferentes componentes de código aberto interligados para ajudar os usuários a obter dados de qualquer fonte e em qualquer formato, além de realizar pesquisas, analisar e visualizar os dados em tempo real.

O <b>Elasticsearch</b> é um mecanismo de busca e análise de texto completo usado para armazenar documentos no formato JSON . O Elasticsearch é um componente importante usado para armazenar, analisar e correlacionar dados, entre outros. O Elasticsearch oferece suporte à API RESTFul para interação com os dados.

O <b>Logstash</b> é um mecanismo de processamento de dados usado para obter dados de diferentes fontes, aplicar filtros ou normalizá-los e, em seguida, enviá-los ao destino, que pode ser o Kibana ou uma porta de escuta. Um arquivo de configuração do Logstash é dividido em três partes, conforme mostrado abaixo:

  - <b>Entrada</b> é onde o usuário define a fonte de onde os dados serão ingeridos.
  - <b>Filtro</b> é onde o usuário especifica as opções de filtro para normalizar o log ingerido acima.
  - <b>Saída</b> é para onde o usuário deseja que os dados filtrados sejam enviados. Pode ser uma porta de escuta, uma interface Kibana , um banco de dados Elasticsearch , um arquivo, etc.

<b>Beats</b> é um agente baseado em host conhecido como Data-shippers, usado para enviar/transferir dados dos endpoints para o Elasticsearch. Cada beat é um agente de propósito único que envia dados específicos para o Elasticsearch. 

O <b>Kibana</b> é uma visualização de dados baseada na web que funciona com o Elasticsearch para analisar, investigar e visualizar o fluxo de dados em tempo real. Ele permite que os usuários criem múltiplas visualizações e dashboards para melhor visibilidade. Vamos nos aprofundar a respeito da interface Kibana neste laboratório.

# Kibana




  

