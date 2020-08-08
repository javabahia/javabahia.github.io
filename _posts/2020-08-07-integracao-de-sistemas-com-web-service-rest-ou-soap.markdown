---
layout: post
title:  "Integração de Sistemas com Web Service: REST ou SOAP?"
date:   2020-08-07 18:00:00 +0300
image:  javaba.png
author: Angelo Brandão
tags:   [web service, rest, soap, javabahia, comunidade]
---

![Integração de Sistemas](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/integracao.jpeg)

Este artigo apresenta um estudo sobre *web service* com a finalidade de demonstrar através de uma análise comparativa entre as tecnologias REST e SOAP as vantagens e desvantagens em utilizá-las como soluções para prover serviços e integrar sistemas. Será abordado uma introdução sobre *web services* e uma contextualização sobre as tecnologias REST e SOAP para explicar como tais tecnologias são utilizadas para a integração entre sistemas. As informações abordadas e levantadas através de uma pesquisa exploratória com abordagem qualitativa e fundamentado no levantamento bibliográfico serão analisadas e comparadas para concluir quais as vantagens e desvantagens de utilizá-las. A partir das análise comparativa realizada, foi possível concluir que as duas tecnologias mesmo possuindo suas peculiaridades, cabe ao desenvolvedor escolher qual delas utilizar para atender a necessidade da integração.

### **Tópicos**

- [**1. Introdução**](#1-introdução)
- [**2. Web Service**](#2-web-service)
- [**3. SOAP**](#3-soap)
- [**4. REST**](#4-rest)
- [**5. Analise comparativa**](#5-analise-comparativa)
- [**6. Conclusão**](#6-conclusão)
- [**Referências**](#referências)

## **1. Introdução**

A cada vez mais os processos estão se tornando *online*, devido a ampla concorrência entre as empresas. O mundo esta interligado, vários aplicativos nas redes sociais estão integrados, fazendo uso das suas funções básicas de comunicação, como exemplo o *Twitter*. Sendo assim, com os processos *online* um cliente tem a comodidade de realizar uma compra de forma segura e sem se locomover bastante e por outro lado as empresas a partir do perfil dos clientes pode twitar para eles as melhores ofertas. [SAUDATE, 2012].

Empresas passaram as últimas décadas desenvolvendo e evoluindo sistemas e nos últimos anos vem se preocupando em como manter esses sistemas legados e como integrá-lo às novas necessidades de negocio. No cenário atual do mercado tecnológico, as empresas tem buscado cada vez mais a utilização de *web services* para fazer a integração entre sistemas, como solução para atender as novas necessidades do mercado.

Com base forte nas suas necessidades, as empresas empregam o uso de *web services*, mas para esse emprego ser possível é necessário realizar estudos e análise comparativa das tecnologias existentes, podendo ser utilizado SOAP (*Simple Object Access Protocol*) ou REST (*Representational State Transfer*). Cada tecnologia tem suas características, sendo elas vantajosas ou não, e com isso o comparativo entre elas é de grande importância na escolha da melhor solução que atenda os requisitos do sistema.

Este artigo descreve um estudo sobre *web services* que utilizam a arquitetura SOA (*Service-Oriented Architecture*) e os que seguem o estilo arquitetural ROA (*Resource-Oriented Architecture*), especificadamente, será apresentado uma análise comparativo sobre seus protocolos, respectivamente SOAP e REST, com a finalidade de demonstrar a partir das suas características as vantagens e desvantagens em utilizá-las como soluções para prover serviços e integrar sistemas.

Este artigo está dividido da seguinte maneira: a sessão 2 introduz a tecnologia *Web Services* descrevendo seus conceitos importantes, a sessão 3 conceitua o protocolo SOAP explicando sobre suas principais características, a sessão 4 conceitua sobre o protocolo REST também explicando as suas principais características, a sessão 5 demonstra uma analise comparativas entre os dois protocolos e a sessão 6 apresenta a conclusão e os trabalhos futuros.

## **2. Web Service**

Um web service é um sistema de software projetado para suportar interação entre máquinas através de uma rede. Ele tem uma interface descrita em um formato processável por máquina (especificamente WSDL (*Web Services Descriptor Language*)). Outros sistemas interagem com o serviço web de uma maneira prescrita pela sua descrição usando mensagens SOAP, normalmente transmitidas utilizando HTTP (*Hypertext Transfer Protocol*) com uma serialização XML (*Extensible Markup Language*) em conjunto com outras normas relacionadas à Web. [W3C, 2004]

Conforme a [W3C, 2004], uma das características essenciais dos web services é a possibilidade de utilização de diferentes formas de transferência de dados pela rede. Sendo assim, um serviço *web service* permite que dois ou mais sistemas se comuniquem independente da linguagem de programação ou sistema operacional através de uma *interface* bem definida. A comunicação entre estes sistemas só é possível a partir da utilização de protocolos, principalmente os relacionados ao formato de transmissão de dados, tais como: HTTP, SMTP (*Simple Mail Transfer Protocol*), FTP (*File Transfer Protocol*), RMI (*Remote Method Invocation*) / IIOP (*Internet Inter-ORB Protocol*) ou protocolos de mensagem proprietários.

Segundo [JUNIOR e MATOS, 2011], é desejável que os *web services* possam ser facilmente encontrados a partir de mecanismos de busca, sejam auto-descritivo e usem padrões comuns da internet. Para que esses serviços sejam encontrados de forma fácil existe um diretório comum onde as informações sobre esses serviços são armazenadas, denominado UDDI (*Universal Description, Discovery and Integration*).

A WSDL é conceituada como uma linguagem utilizada para criar uma autodescrição do serviço. As informações contidas neste documento são: padrão utilizado para a troca de mensagens (SOAP, JMS (*Java Message Service*), etc.), protocolo de transporte (HTTP, HTTPR (*Hyper Text Transfer Protocol Reliable*), DIME (*Direct Internet MessageEncapsulation*), etc.) e endereço lógico (URL (*Uniform Resource Locator*)) do serviço.

Dentre os protocolos utilizados na comunicação entre os sistemas através do serviço web service, os mais utilizados são o protocolo SOAP e o protocolo REST, que unidas a estrutura básica a XML compõem a estrutura básica dos Web Services. O XML é o responsável pela maior parte da interoperabilidade entre aplicações de ambientes heterogêneos permitida pelos Web Services. [JUNIOR e MATOS, 2011]

Como alternativa para o XML para a transmissão de dados na comunicação entre sistema existe o JSON (*JavaScript Object Notation*). O JSON se popularizou com o uso do AJAX (*Asynchronous JavaScript and XML*) e por possuir o formato menor que o equivalente ao XML e também por sua interpretação ser mais simples. Este utilizado nos serviços web service implementados utilizando o protocolo REST para comunicação entre os sistemas como alternativa para o uso do SOAP e WSDL para oferecer serviço, conforme citado por [SAUDATE, 2012].

A Figura 1 demonstra o funcionamento dos web services utilizando os protocolos REST e SOAP, explicados nas próximas sessões.

![Funcionamento dos web services REST e SOAP](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/funcionamento_web_services_rest_soap.jpeg)

Figura 1: Funcionamento dos web services REST e SOAP. Fonte: <[](http://www.emmielewis.com/to-rest-or-not-to-rest/){:target="\_blank"}>.

## **3. SOAP**

A [W3C, 2007] define o SOAP como um protocolo leve destinado à troca de informações estruturadas em um ambiente distribuído descentralizado. Como já explicado na sessão anterior, o SOAP usa tecnologias XML para definir uma estrutura de mensagens extensível possibilitando a construção de mensagem que pode ser trocada por uma variedade de protocolos subjacentes. Segundo a [W3C, 2007] esta estrutura foi projetada para ser autônoma, não dependendo de qualquer modelo de programação especial e/ou outras semânticas particulares de implementação.

O funcionamento do SOAP é similar ao do RPC (*Remote Procedure Call*), onde a mensagem enviada ao serviço deverá informar qual método deve ser chamado e os valores do seu parâmetro, se existirem. O serviço por sua vez irá devolver uma mensagem contendo o valor retornado pelo método. Um outro modelo utilizado como alternativa ao RPC é o baseado em troca de mensagens, onde o servidor espera receber um documento inteiro para processar, podendo este ter sido implementado de forma síncrona ou assíncrona. Nos dois modelos descritos anteriormente o conteúdo da mensagem estará contido em um envelope SOAP. [JUNIOR e MATOS, 2011]

Existem duas maneiras de enviar mensagens para que um cliente possa realizar solicitações a um web service SOAP, são elas: *One-Way Messaging* e *Request-Resposnse Messaging*. A primeira permite o envio unilateral das mensagens, no qual a solicitação é realizada sem se preocupar com a resposta. Já a segunda maneira o envio das mensagens é bilateral, aonde após realizado o processamento de uma solicitações é enviado uma resposta, conforme demonstrado na Figura 1. [GOMES, 2009]

Segundo [STREIBEL apud MORO, DORNELES e REBONATTO, 2011], um envelope SOAP é um documento XML e seu formato é definido por um XML schema, que faz uso do XML *namespaces* para garantir extensibilidade. Um documento SOAP é constituído estruturalmente por um elemento Envelope, um elemento *Header*, um *Body* e um elemento *Fault*, conforme representado na Figura 2.

![Estrutura de um documento SOAP](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/estrutura_documento_soap.jpeg)

Figura 2: Estrutura de um documento SOAP. Fonte: <[](http://disciplinas.ist.utl.pt/~leic-sod.daemon/2012-2013/labs/lab11/soap_saaj/soap/index.html){:target="\_blank"}>.

A Figura 2 demonstra a estrutura de um documento SOAP onde o Envelope é um elemento raiz que identifica o documento XML como uma mensagem SOAP. No elemento *Header* são inseridos os dados de cabeçalho tais como endereçamento, segurança, transações, entre outros. Os dados de sistema podem ser colocados no *Header* ou não, pois eles são opcionais. O elemento *Body* é responsável por armazenar os dados de negócio sendo estas informações de chamadas e respostas. No *Body* também é possível adicionar um elemento denominado *Fault* responsável por manter informações e status de possíveis erros. A Figura 3 exemplifica a estrutura de um documento XML de uma mensagem SOAP.

![Documento XML de uma mensagem SOAP](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/documento_xml_mensagem_soap.jpeg)

Figura 3 - Documento XML de uma mensagem SOAP. Fonte: Elaboração própria (2015).

Ao criar um serviço e publica-lo, o mesmo fica disponivel para que seja utilizado por um outro sistema. Mas isso só será possivel se o sistema que for consumir o serviço souber os segintes dados: as informações que seram enviadas para o serviço, as informações que seram retornadas pelo serviço e onde o serviço se encontra. Então, para tudo isso acontecer foi adotado o WSDL, que conforme [KALIN, 2010], esse documento deve ser possível de ser publicado e descoberto, pois o mesmo disponibiliza um formato padrão para as informaões a ser consumida de um serviço e por fim o consumo deste serviço torna-se mais simples.

Segundo [WEERAWARANA, et al. apud MORO, DORNELES e REBONATTO, 2011], o WSDL é considerado um vocabulário XML utilizado para descrever e localizar web services. O WSDL possui cinco sessões: *types*, *message* (onde pode existir mais de um elemento), *portType*, *binding* e *service*. [SAUDATE, 2012]. A Figura 4 demonstra a sessões definidas para versões 1.1 e 2.0 do WSDL.

![Definição das versões 1.1 e 2.0 do WSDL](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/definicao_versoes_wsdl.jpeg)

Figura 4 - Definição das versões 1.1 e 2.0 do WSDL. Fonte: <[](http://www.servicetechmag.com/I27/0309-3){:target="\_blank"}>.

Observando a Figura 4 percebe-se que houve algumas mudanças na versão 2.0 da especificação WSDL, o elemento message foi retirado, o elemento definitions passou a ser *description*, o elemento *portType* passou a ser *interface*, e o elemento *port* passou a ser *endpoint*.

Para [MORO, DORNELES e REBONATTO, 2011] e como já citado por [JUNIOR e MATOS, 2011] as descrições dos serviços, tal como os métodos para publicação e localização de informações sobre estes serviços estão contidos no UDDI, mas independentemente de estarem disponíveis no UDDI, o WSDL contém a URL que aponta para o local onde está armazenada o descritivo completo do serviço.

Para [KALIN, 2010], o UDDI não suporta qualquer tipo privado de descrição de serviço, assim como o WSDL, mas disponibiliza seu próprio sistema para aceitar documentos WSDL.

O WSDL não se limita a um modelo de transporte particular, sendo aplicado a qualquer um. O WSDL 2.0 foi expandido para comportar também o modelo REST devido ao atual crescimento dos REST services. [SAUDATE, 2012]

## **4. REST**

REST é um estilo de implementação de *web service* criado por Roy Fielding, também criador do protocolo HTTP. Uma boa prática para o uso do REST é utilização adequada dos métodos HTTP, URL’s, códigos de status padronizados, cabeçalhos HTTP e interligações entre outros recursos diferentes. Em REST, os dados que são trafegados pelo protocolo são definidos em termos de recursos. O HTTP é o único protocolo compatível com o REST, pelo maior motivo, ser o protocolo mais utilizado no mundo. [SAUDATE, 2013]

Conforme [MORO, DORNELES e REBONATTO, 2011], o REST é utilizado para descrever interfaces que transmitam dados sobre HTTP sem o uso de SOAP ou *session tracking*. Os sistemas que seguem estes princípios também são denominados como *RESTful*.

Para que os princípios REST sejam respeitados deve se seguir um conjunto de restrições, que são: Cliente-Servidor, *Stateless*, *Cache*, *Interface Uniforme*, Multicamada e *Code-On-Demand*. A restrição de *interface* uniforme é a característica central que diferencia o REST dos outros modelos arquiteturais, pois tem proeminência em uma *interface* uniforme entre os componentes. O REST define quatro requisitos de *interface* para obter uma *interface* uniforme, são eles: identificação de recurso, manipulação de recurso através de representação, mensagens auto descritivas e hipermídias como mecanismo de estado da aplicação. [FIELDING apud MORO, DORNELES e REBONATTO, 2011]

Um dos pontos importante e como já mencionado anteriormente é a utilização dos métodos disponibilizados pelo HTTP. Diferente do SOAP, que só utiliza o método POST para transmitir os dados, o REST prevê que, dentro de um cenário ideal, o método HTTP a ser utilizado seja diretamente relacionado à funcionalidade do serviço a ser consumido. Então, o REST fornece uma interface uniforme com os métodos GET, PUT, DELETE e POST, conforme demonstrado na Figura 5.

![Métodos básicos do REST](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/metodos_basicos_rest.jpeg)

Figura 5 - Métodos básicos do REST. Fonte: <[](https://msdn.microsoft.com/pt-br/library/dd941696.aspx){:target="\_blank"}>.

Segundo [MORO, DORNELES e REBONATTO, 2011], no REST uma URL é utilizada como identificador único para o recurso na troca de mensagens, este podendo ter um funcionamento diferenciado conforme o método usado para invocá-lo e os dados passados na requisição HTTP.

Uma outra característica importante do REST é a utilização de *media types* para modificar as representações de um mesmo conteúdo, sob ponto de vista distintos. Por exemplo, ao efetivar uma consulta em um sistema por uma determinada informação, pode se tanto desejar um XML com os dados, quanto um JSON, como também uma imagem. Isso pode ser possível utilizando a mesma URL e o que vai distinguir o resultado da solicitação é o valor passado no cabeçalho *Accept*: do HTML (Figura 5). [SAUDATE, 2013]

![Exemplo de media types](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/exemplo_media_types.jpeg)

Figura 6 - Exemplo de *media types*. Fonte: <[](http://manuel-palacio.blogspot.com.br/2012/03/rest-versioning-example.html){:target="\_blank"}>.

Conforme pode ser visualizado na Figura 6, caso seja feito uma solicitação para a URL ou URI (*Uniform Resource Name*) passando o cabeçalho *Accept* com o valor application/xml, irá receber uma representação da informação como XML, assim como, se for passado o valor image/* irá receber uma imagem representando a informação e se for passado application/json irá receber a representação da informação como JSON.

Além da característica de utilização de *media types*, o retorno de *status* na resposta a uma requisição é muito útil na troca de mensagens na web services REST outra característica do protocolo HTTP, muito útil na troca de mensagens nos serviços REST. Por exemplo, caso uma informação não for encontrada pede-se ter como retorno um HTTP/1.1 404 Not Found. [SAUDATE, 2013]

Essas características do REST apontadas anteriormente, será utilizadas para realizar uma análise comparativa com o protocolo SOAP, com o intuito de demonstrar a vantagens de utiliza uma ou a outra na integração de sistemas.

## **5. Analise comparativa**

Muitas são as diferenças entre os protocolos conceituado nas sessões anteriores e cada um desses protocolos possui sua particularidade. Uma análise comparativa entre o protocolo SOAP e o protocolo REST será de grande importância para a tomada de decisão de qual dos dois ser adotado para realizar a integração entre sistemas.

Uma diferença importante entre os dois protocolos é que os *web services* REST são implementados seguindo um modelo arquitetural, enquanto os *web services* SOAP são desenvolvidos utilizando protocolos específicos. Para [KALIN, 2010] "SOAP é um protocolo de mensagem, enquanto que REST é um estilo de arquitetura de software para sistemas hypermedia distribuídos".

Uma das desvantagem da utilização do protocolo SOAP é o fato do mesmo ferir algumas dos princípios de boas praticas da especificação HTML, devido a não utilizar de forma correta seus métodos. O REST por sua vez utiliza corretamente os métodos HTML (PUT, GET, POST, DELETE), o SOAP utiliza apenas o método POST para realizar as requisições através de uma arquivo XML.

Por sua vez, uma das vantagens da utilização do protocolo REST é que o mesmo não restringe o formato de dados a ser trafegado em suas requisições, diferente do protocolo SOAP que só permite utilizar XML para o trafego de dados nas suas requisições.

O protocolo REST se difere do SOAP no quesito desempenho por ser mais leve, pois conforme analise realizada por [MORO, DORNELES e REBONATTO, 2011], o SOAP utilizam envelopes envolvidos por pacotes HTTP, então, para utilizar os dados é necessário realizar um *parse*, ao contrário do REST que só utiliza do HTTP para trafegar os dados. O SOAP perde no desempenho devido a obrigação de sempre realizar *parse* antes da utilização dos dados e também por serem mais pesados devido estarem envolvidos em envelopes HTTP.

Entretanto, o protocolo SOAP possui funcionalidades que são úteis em situações especificas, auxiliando bastante na implementação de serviços para integração de sistemas. Dentre as funcionalidades disponibilizadas pelo SOAP estão a autenticação, a mantenibilidade de sessão entre as requisições, entre outras.

A Tabela 1 demonstra resumidamente as diferenças, vantagens e desvantagem dos protocolos SOAP e REST.

![Exemplo de media types](/img/posts/2020-08-07-integracao-de-sistemas-com-web-service-rest-ou-soap/tabela_soap_x_rest.jpeg)

Tabela 1 - Tabela SOAP x REST. Fonte: Fonte: Elaboração própria (2015).

Conforme pode ser verificado na tabela 1, existem muitas diferenças de cada tecnologia, e através das suas características o desenvolvedor pode escolher qual melhor adotar para o desenvolvimento da integração entre os sistemas. Para o protocolo SOAP, é realizado a partir de solicitações e resposta em objetos complexos na forma de arquivo XML, baseado nas especificações WS, entre outros. Já o protocolo REST, depende de um único protocolo de aplicação, no caso, o HTMP, a padronização de formato de dados não é realizado apenas através de XML, mas também através de JSON ou texto simples, dentre outros. A tabela deixa bem claro as peculariedades de cada protocolo.

## **6. Conclusão**

O presente artigo demonstrou através de uma análise comparativa entre as tecnologias REST e SOAP as vantagens e desvantagens em utilizá-las como solução para prover serviços e integrar sistemas.

As informações abordadas e levantadas através de uma pesquisa exploratória com abordagem qualitativa e fundamentado no levantamento bibliográfico, foram cruciais para realizar uma análise comparativa entre as tecnologias citadas para concluir quais as vantagens e desvantagens de utilizá-las.

A partir do resultado da análise comparativa realizada, foi possível também concluir que mesmo as duas tecnologias possuindo suas peculiaridades, cabe ao desenvolvedor escolher qual delas utilizar para atender a necessidade da integração.

Para trabalhos futuros, têm-se em vista um estudo e aprofundamento sobre metodologias para implementar segurança em serviços desenvolvidos utilizando a arquitetura SOA e também nos que seguem o estilo arquitetural ROA.

## **Referências**

GOMES, D. A. **Web Services SOAP em Java.** Guia prático para desenvolvimento de web services em Java. São Paulo: Novatec Editora, 2009.

JUNIOR, C. R.; MATOS, S. N. **Um Web Service para busca de Preços na Internet.** Revista Tecnológica. Maringá, v. 20, p. 83-96, 2011.

KALIN, M. **Java Web Services: Implementando.** Rio de Janeiro: Alta Books Editora, 2010.

MORO, T. D.; DORNELES, C. F.; REBONATTO, M. T. **Web services WS-* versus Web Services REST.** REIC - Revista de Iniciação Científica, v. 11, n. 1, 2011

SAUDATE, A. **REST: Construa API's inteligentes de maneira simples.** São Paulo. Casa do Código Editora, 2013.

SAUDATE, A. **SOA aplicado: Integrando com web services e além.** São Paulo. Casa do Código Editora, 2012.

W3C. **SOAP Version 1.2 Part 0: Primer (Second Edition).** W3C Recommendation 27 April 2007. Disponível em: <[](http://www.w3.org/TR/2007/REC-soap12-part0-20070427/){:target="\_blank"}>. Acesso em: 03 mai. 2015.

W3C. **Web Services Architecture: W3C Working Group 2004.** Disponível em: <[](http://www.w3.org/TR/ws-arch/){:target="\_blank"}>. Acesso em: 03 mai. 2015.
