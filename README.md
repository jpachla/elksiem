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

A seção "Discover" do Kibana é onde os analistas costumam concentrar grande parte de seu trabalho. Nela, são exibidos os logs recebidos (também chamados de documentos), além da barra de busca, os campos padronizados e outras informações relevantes. É nesse espaço que os analistas podem realizar diversas atividades, como consultar dados, filtrar informações e explorar registros.

  1) <b>Logs (documento)</b>: Cada log aqui também é conhecido como um documento único contendo informações sobre o evento. Ele mostra os campos e valores encontrados naquele documento.
  
  2) <b>Painel de campos</b>: O painel esquerdo da interface exibe a lista de campos analisados ​​dos logs. Podemos clicar em qualquer campo para adicioná-lo ao filtro ou removê-lo da pesquisa.
  
  3) <b>Padrão de índice</b>: Permita que o usuário selecione o padrão de índice na lista disponível.
  
  4) <b>Barra de pesquisa</b>: Local onde o usuário adiciona consultas de pesquisa/aplica filtros para restringir os resultados.
  
  5) <b>Filtro de Tempo</b>: Podemos refinar os resultados com base na duração. Esta aba oferece diversas opções para filtrar/limitar os registros.
  
  6) <b>Intervalo de tempo</b>: Este gráfico mostra as contagens de eventos ao longo do tempo.

  7) <b>Barra SUPERIOR</b>: Esta barra contém várias opções para salvar a pesquisa, abrir as pesquisas salvas, compartilhar ou salvar a pesquisa, etc.

<a href='https://postimages.org/' target='_blank'><img src='https://i.postimg.cc/gcvkvL83/elk24.jpg' border='0' alt='elk24'/></a><br /><a href='https://postimages.org/'>

Conforme podemos analisar na imagem abaixo, no gráfico de linha do tempo há um pico incomum nos logs do dia 11 de janeiro de 2022. Exemplos como este são bastante úteis para o analista de segurança investigar alguma possível anomalia.

<a href='https://postimg.cc/q6rXfqVX' target='_blank'><img src='https://i.postimg.cc/gjXMZLg5/elk3.jpg' border='0' alt='elk3'/></a>

<b>Adicionar Filtros</b>

Adicionar opção de filtro na barra de pesquisa nos permite aplicar um filtro nos campos, como mostrado abaixo.

<a href='https://postimg.cc/JtPsZ8R2' target='_blank'><img src='https://i.postimg.cc/L6Mjd4w2/elk5.gif' border='0' alt='elk5'/></a>

<b>Criar Tabelas</b>

Inicialmente, os documentos são mostrados em seu formato original. No entanto, é possível abrir qualquer um deles e escolher apenas os campos relevantes para montar uma tabela personalizada. Essa abordagem ajuda a eliminar informações desnecessárias, deixando os dados mais organizados, claros e fáceis de interpretar.

<a href='https://postimg.cc/62nw5dYZ' target='_blank'><img src='https://i.postimg.cc/vBSmhhn0/elk6.gif' border='0' alt='elk6'/></a>

<b>Pesquisa de textos livres</b>

A busca por texto livre permite que os usuários busquem os registros com base apenas no texto . Isso significa que uma busca simples pelo termo <i>security</i> retornará todos os documentos que o contêm, independentemente do campo.

<b>Operadores lógicos (AND | OR | NOT)</b>

O KQL também permite que os usuários utilizem operadores lógicos na consulta de pesquisa. Vejamos os exemplos abaixo.

<a href='https://postimg.cc/p9BwspnF' target='_blank'><img src='https://i.postimg.cc/xCr9Tmft/elk9.jpg' border='0' alt='elk9'/></a>

<a href='https://postimg.cc/p5vnRcL7' target='_blank'><img src='https://i.postimg.cc/Fzdbb259/elk14.jpg' border='0' alt='elk14'/></a>

<b>Criar Visualização</b>

A aba de visualização nos permite visualizar os dados em diferentes formatos, como tabelas, gráficos de pizza, gráficos de barras, etc. Esta tarefa de visualização usará várias opções fornecidas por esta aba para criar algumas visualizações simples e apresentáveis.

<a href='https://postimg.cc/jLqdrnbZ' target='_blank'><img src='https://i.postimg.cc/fTm3mYgn/elk25.gif' border='0' alt='elk25'/></a>

<b>Criando Painel personalizado(Dashboard)</b>

Os painéis oferecem boa visibilidade da coleta de logs. Um usuário pode criar vários painéis para atender a uma necessidade específica. Podemos combinar diferentes pesquisas e visualizações salvas para criar um painel personalizado para visibilidade de logs de VPN.

Os passos para criar um painel são:

 - Vá para a aba Painel e clique em <b>Criar painel</b>.
 - Clique em <b>Adicionar da biblioteca</b>. Na biblioteca é aonde ficará armazenado as tabelas, visualizações e gráficos salvos.
 - Clique nas visualizações e pesquisas salvas. Elas serão adicionadas ao painel.
 - Depois que os itens forem adicionados, ajuste-os adequadamente, conforme mostrado abaixo.
 - Não se esqueça de salvar o painel depois de concluí-lo.

<a href='https://postimg.cc/f38KWgqJ' target='_blank'><img src='https://i.postimg.cc/NMcP4317/elk23.gif' border='0' alt='elk23'/></a>







  

