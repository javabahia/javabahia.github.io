---
layout: post
title:  "Como fazer um bom design de código em Java"
date:   2020-07-20 18:00:00 +0300
image:  javaba.png
author: Paula Santana
tags:   [arquitetura, java, javabahia,soujava,devjavagirls]
---

Post de hoje é uma prévia do conteúdo que será apresentado no Oracle Webinar em homenagem aos 25 anos do Java, próxima quarta-feira, 22/07 as 10h por [Paula Santana](https://twitter.com/psanrosa13){:target="\_blank"}, que atua como organizadoras das comunidades: [Sou Java](https://twitter.com/soujava){:target="\_blank"} e [Devs Java Girl](https://twitter.com/devsjavagirl){:target="\_blank"}, com [Rafael Benevides](https://twitter.com/rafabene){:target="\_blank"}. O evento é online e gratuito, você pode garantir sua presença no [link](https://go.oracle.com/LP=96279?elqCampaignId=256156){:target="\_blank"}.

## Explicando um pouco sobre os grupos de comunidade citados na introdução

Sou Java: "_O SouJava é um grupo de usuários, formado por desenvolvedores e evangelistas da tecnologia Java no Brasil, e tem como objetivo fortalecer, expandir e profissionalizar o uso de Java no país. O SouJava é um dos mais ativos e importantes grupos de usuários do mundo, e realiza diversas atividades no Brasil, e ajuda na organização do movimento Java mundial. O SouJava mantém reuniões presenciais, eventos e uma presença online, ajudando a comunidade Java brasileira a aplicar a tecnologia Java em projetos reais._" [ (fonte do texto)](https://soujava.org.br/sobre/){:target="\_blank"} 

- [Site](https://soujava.org.br/){:target="\_blank"} 
- [Youtube](https://www.youtube.com/soujava){:target="\_blank"} 
- [Twitter](https://twitter.com/soujava){:target="\_blank"} 

Devs Java Girl: "_Criamos um maravilhoso Grupo de Estudos, estamos organizando DOJOS, meetups e juntando quem manja com quem quer manjar! Em caso de encontros para estudo, pareamos quem não sabe com quem já sabe codar. Entendemos que a prática nos levará para onde queremos e que a evolução técnica é consequência. De quebra, ainda conhecemos pessoas maravilhosas!_"[ (fonte do texto)](https://medium.com/@paulasantana/devsjavagirlha-7b2277c7c922){:target="\_blank"} 

- [Site](https://medium.com/@paulasantana/devsjavagirlha-7b2277c7c922){:target="\_blank"} 
- [Youtube](https://www.youtube.com/channel/UCgoGOLleKmM9ikxQhGhhOhQ){:target="\_blank"} 
- [Twitter](https://twitter.com/devsjavagirl){:target="\_blank"} 


## Como fazer um bom design de código em Java por Paula Santana

### Tópicos Abordados:

1. O porquê do design.
1. Boas práticas Para Orientação a Objetos
1. Effective Java nos métodos
1. Divisão de camadas
1. Estrutura de pacotes
1. Over engineering
1. Exceções
1. Qualidade em Testes
1. Pair Programing
1. Code Review E Pull Request
1. Documentação e Configuração
1. Code Style e Ferramentas de anaĺise estática

#### O porquê do design.

* É muito fácil se perder entre Arquitetura, design e implementação.
* Quando falamos de design, devemos focar nas características das interfaces de comunicação entre partes do sistema ou entre sistemas.
* Um bom design permite modificações com mais facilidade, permite evoluir o sistema com segurança e acima de tudo com menos esforço, e neste último ponto está relacionado diretamente com custos que aumentam em projetos que foram mal projetados e que requerem equipes e horas e horas de desenvolvimento até mesmo para simples alterações.
* Se pararmos para pensar, a própria plataforma Java foi construída com preocupações de design, preocupações em não quebrar quem utilizasse a plataforma.
* Se olharmos os exemplo da JCP e das decisões que foram tomadas ao longo dos anos e sobre como o uso de especificações permitiu que não houvesse vendor lock-in com bibliotecas e apis no ecossistema Java, temos um grande exemplo prático de decisões de design que possibilitam termos uma boa estrutura em nossos projetos.

#### Boas práticas Para Orientação a Objetos

A linguagem Java é multi paradigma, ela acaba abordando vários paradigmas, mas quase sempre estamos em projetos que tem como paradigma principal Orientação a Objetos, então se você desenvolve projetos com Java é quase que certo que você esteja trabalhando com o paradigma de Orientação a Objetos ( ou tentando pelo menos aplicar né?). Mesmo com o fato do Java atender múltiplos paradigmas, como reativo e funcional, os projetos em Java acabam mesclando um pouco destes paradigmas e se baseando muito em OO. Existem muitas boas práticas relacionadas a este paradigma, porém vou destacar algumas aqui.

* __Programe voltado a interface:__ este tópico é citado no livro de Bob Martin que cita que ao utilizarmos objetos, utilizarmos a interface que ele implementa ao invés de usar o objeto em específico, pois isso nos permite não termos tantas quebras em casos de modificações.
Demorou muito a entender de fato o porque ao receber um Arraylist em um método eu deveria na verdade receber um List ou uma Collection ao invés do tipo ArrayList.
E isso não quer dizer que você deva fazer Interface indiscriminadamente, existe uma cultura de que precisamos criar interface sempre, mas muitas vezes para situações que são somente uma única implementação essa abordagem não faz sentido.
* __Nomes:__ criar bons nomes leva tempo, mas economiza mais tempo depois, não economize com o tamanho do nome, desde que ele descreva bem o propósito do que está no método, variável, classe, etc.
1. Classes devem ter nome de substantivo não verbo.
1. Métodos devem ter nomes que descrevem sua ação interna, use verbos para nomes de método.
* __Evite herança, favoreça composição:__ Um problema com a herança é que existe um alto acoplamento com a classe mãe, fazendo com que muitas vezes a classe filha tenha que conhecer o código da classe mãe, tirando o encapsulamento. Usar interface para composição permite usar os benefícios da herança sem gerar alto acoplamento ou quebrar o encapsulamento.
* __Favoreça imutabilidade e simplicidade:__ Um grande exemplo de imutabilidade no Java é a classe String, quem nunca no começo demorou a entender o porque um replace não estava funcionando em uma variável do tipo String? Isso porque uma vez que você instância a String ela não sofre alterações, o que você consegue é gerar novas instâncias a partir dela.
Muito problemas são ocasionados por mutabilidade dos objetos.
Dicas para criar uma classe imutável:
1. Ela deve ser final, para evitar que filhas permitam mutabilidade.
1. Os atributos devem ser privados
1. Os atributos devem ser final
1. Caso sua classe tenha composição com objetos mutáveis eles devem ter acesso exclusivo pela sua classe, devolvendo cópias defensivas quando necessário.

* __Getters e Setters:__ Crie quando realmente precisar, alguns casos de frameworks usam a api de Reflection para executar parse de dados, então não é necessário que você crie eles até mesmo para objetos anêmicos, se não for necessário.
* __Enum:__ Use enums no lugar de constantes, isso permite deixar o código mais limpo. Além Enum podem ser classes bem ricas e podem facilitar muito a implementação de alguns padrões de projeto. Os Enums são muito ricos para o design de aplicações pois pode iniciar como uma simples coleção de dados e ao longo da ampliação do sistema evoluir para uma abstração completa.

#### Effective Java nos métodos

Trabalhar com bom design na construção de métodos é fundamental no Java.
O livro Effective Java é bem conhecido na comunidade Java e podemos dizer que a leitura dele é ótima para nosso dia a dia. Vamos entender alguns pontos que são abordados no livro sobre o design de métodos.

* __Verifique a validade dos parâmetros:__ se seu método requer que um objeto seja não nulo, ou que um dado seja corretamente passado, no início do seu método deverá realizar as validações dos parâmetros antes de realizar as demais ações. O não uso das validações pode acarretar em maior dificuldade em rastrear erros posteriores. Além disso como uma boa prática, em métodos public e protected que tenham validação devemos usar a tag do Javadoc @throws para documentar a exceção que será lançada no método.
Além disso no livro é recomendado usar o Objects.requireNonNul que foi adicionado no Java 7 e que é muito útil para validação de objetos nulos.
Mas calma lá que isso não significa que você deva adicionar validação em tudo, a grande questão é que você projete seu método para que ele execute de maneira satisfatória sem tantas restrições, mas quando houver a necessidade de algo, você o faça para impedir que problemas futuros ocorram. Além disso ainda devemos contrabalancear a questão de performance destas validações em métodos.
* __Faça cópias defensivas quando necessário:__ falando de imutabilidade, quando sua classe utiliza classes que são mutáveis, mesmo que você não crie métodos que alterem o estado, deixando acessar essas dependências, você corre o risco de alterações modificarem elas.
Neste caso ao receber esse objeto na construção, realize uma cópia defensiva dele de forma que garanta a sua imutabilidade.
* __Projete assinatura de métodos com cuidado:__ evite lista longa de parâmetros em seu método, considere quatro parâmetros ou menos. Para reduzir a quantidade de parâmetros você pode utilizar objetos auxiliares que representem estes parâmetros, ou utilizar a criação de Builder para compor o objeto, especialmente em casos onde algum deles for opcional.
Em seus parâmetros prefira o uso de interfaces ao de implementações, em casos onde o parâmetro receber apenas dois valores, prefira o uso de Enum ao invés de boolean.
* __Utilize a sobrecarga com critério:__ não crie sobrecargas com o mesmo número de parâmetros.
* __Retorne coleções ou arrays vazios em vez de nulos:__ retornos nulos para listas ou coleções dificultam para o cliente do método, visto que exige um tratamento para a resposta. Existe um argumento que muitos desenvolvedores usam de que esta criação alocaria memória, isso no livro do Effective Java fica bem claro que raras exceções isso faria diferença e ele explica como criar o contêiner vazio que seria a criação de um único contêiner vazio e utilizar ele como referência em retornos que exijam seu uso.


#### Divisão de camadas e responsabilidades

Um dos grandes problemas que desenvolvedores enfrentam no começo de carreira é sobre a divisão de camadas da aplicação.
Existem dois conjuntos de padrões que são essenciais para entender estas divisões.

1. __O GRASP, sigla que significa General Responsibility Assignment Software Patterns__, possui um conjunto de princípios que norteiam sobre a responsabilidade das camadas no desenvolvimento de software. Este modelo visa principalmente que a estrutura do seu software  seja adaptável a mudanças. Aplicação desse pattern resulta em um código mais organizado, de fácil manutenção e capaz de ser compreendido por diferentes desenvolvedores. O catálogo inclui padrões como ESPECIALISTA , CREATOR, CONTROLLER, BAIXO ACOPLAMENTO, ALTA COESÃO, POLIMORFISMO, PURA FABRICAÇÃO, INDIREÇÃO, PROTEÇÃO CONTRA VARIAÇÕES.

1. __Os Padrões de Aplicativos Corporativos__ junta uma gama de tipos de classes que criamos ao longo do desenvolvimento do software, o interessante é que no livro do Martin Fowler é possível ter acesso ao catálogo completo que detalha bem cada um deles.
Alguns deles estão disponíveis no próprio blog do Martin Fowler, como DTO, View, Controller, Service, Repository, Mapper, Model, etc.
Existe uma máxima que é a arquitetura evolutiva, existe uma necessidade dos desenvolvedores criarem as camadas também por criar sem avaliar se realmente existe a necessidade desta camada. Um artigo que li recentemente do Otávio Santana no Dzone fala exatamente sobre os prós e contras por exemplo do uso de Dto’s em aplicações Java.
O que percebemos hoje é que muitos criam as camadas de maneira indiscriminada, como se fosse uma regra ter estas camadas.

#### Estrutura de pacotes

Existem Arquiteturas que segue estruturas diferentes no projetos, mas basicamente devemos nos atentar a dois modelos de organização: por layer(camada) ou por feature(recursos).

* __Package by layer:__ os pacotes fazem referência às camadas da aplicação, geralmente apontando as responsabilidades destas camadas. Essa abordagem tem como vantagem a simplicidade de implementação e de entendimento, trás uma boa visão técnica do projeto. Mas como desvantagem, essa abordagem não é boa em grande escala, a medida que o projeto cresce pode ficar complicado de organizar e encontrar o código, além disso não permite uma boa coesão, visto que para que as camadas sejam acessíveis devem expor muito de si, permitindo uso incorreto das implementações. Quando essa abordagem é efetiva? Quando existe necessidade de simplicidade na estrutura do projeto e quando requer uma curva de aprendizado baixa, quando a aplicação é manipulada por um único time, como no exemplo de microserviços ou em aplicações com poucos ou nenhum cenários de negócios complexos, como CRUD ou REST simples.
* __Package by feature:__ os pacotes fazem referência a um recurso de negócio. Esta abordagem permite uma alta coesão dos recursos, visto que todas as camadas dele pertence a um pacote e somente o que é necessário é deixado público. A estrutura do projeto permite ter uma visão das funcionalidades do sistema, permite um crescimento mais sustentável a medida que a base de código aumenta. Porém sua desvantagem é sua curva de aprendizagem, já que para este modelo é necessário bom conhecimento do negócio, além disso o escopo dessa abordagem é simples e com poucas regras, o que gera muita dúvida na implementação e pode gerar padrões diferentes de projeto para projeto, podendo ser um problema para onboarding de novos desenvolvedores ou para projetos que múltiplos times atuam. É recomendado antes de seu uso que a empresa defina um escopo correto para trabalhar com esse modelo, de forma que não vire uma grande bagunça nos projetos. Além disso é importante que os profissionais que realizam a implementação sigam modelo de DDD.


#### Over engineering

O mercado exige uma constante atualização e até mesmo quando vemos um recurso que é muito bom queremos implementar, mas em alguns casos existe um exagero nessa adoção de novas coisas, quando muitas vezes essa adoção pode complicar ao invés de facilitar.
O bom design tem um objetivo, que é o de facilitar as coisas e não complicá-las.
Com as atualizações do Java nos últimos 3 anos, surgiram muitas novidades, mas será que estas novidades estão sendo utilizadas com coerência?
Quando muitas vezes alguém implementa um stream que mais complica a leitura do código do que facilita? O uso excessivo de streams torna a leitura e manutenção complexa.
Quando muitas vezes os recursos estão sendo utilizados indiscriminadamente como por exemplo métodos default  em interfaces.
Se uma biblioteca faz algo, não reinvente a roda, use ela.
Existe um padrão para isso também ! __O padrão KISS ( keep it simple, stupid or keep it stupid simple)__, fala exatamente como manter as coisas simples, portanto, a simplicidade deve ser uma meta fundamental no design e a complexidade desnecessária deve ser evitada.
Além desse padrão existe um princípio da Programação Extrema chamado You aren't gonna need it - YAGNI, ou seja, você não vai precisar disso. Este princípio afirma que uma funcionalidade não deve ser adicionada até que se faça necessária, deixando claro que prever a necessidade de algo e adicionar na aplicação só o torna complexo e atrapalha o design da aplicação.

#### Exceções

__Existem 3 tipos de Throwables:__ exceções verificadas, exceções não verificadas que são de runtime e erros.

1. __Exceções verificadas:__ o chamador do método que lança a exception verificada é obrigado a tratar ela ou propagá-la. Existe uma enorme discussão sobre o uso delas dentro da comunidade, pelo Clean Code é considerada uma má prática o desenvolvimento delas em aplicações, salvo casos no desenvolvimento de bibliotecas críticas. Pelo Effective Java a orientação é de que sejam utilizadas em contextos que permitam o chamador do método se recuperar, porém é frisado que o seu uso seja com sabedoria. Minha opinião é que na dúvida você lance uma não verificada
1. __Exceções não verificadas - Runtime:__ Exceções de runtime  devem ser utilizadas para indicar erros de programação, por exemplo quando alguma condição pré estabelecida não foi executada. Todas as exceptions não verificadas devem herdar direta ou indiretamente de RuntimeException.
1. __Exceções não verificadas - Error:__ não existe nada na especificação Java informando sobre o uso de Error, porém é considerada como uso da JVM. Dada adoção disso pela comunidade não considere criar filhas da classe Error.

* __Enriqueça suas exceções:__ as exceções são classes e muitos acabam se esquecendo disso e implementando apenas mensagem nas exceções,  é importante implementarmos informações que indiquem dados de quando, como e onde ocorreu o problema, além disso em caso de exceções verificadas é importante que a exceção informe dados que permitam o chamador tratar esse problema.Além disso é importante que a mensagem da exception traga todas as informações sobre os dados dela.
* __Priorize o uso das exceções existentes no Java:__ existem muitas, que abrangem a maioria dos cenários no desenvolvimento de software. Ter esse uso permite que todos conheçam o problema gerado de maneira mais padronizada, além da reutilização de código existente. Porém não é considerada uma boa prática usar diretamente Exception, RuntimeException, Throwable ou Error, pois trataria de maneira genérica o erro, visto que elas são classes utilizadas por todas as outras exceptions.
* __Evite lançar exceptions que não tem relação com o contexto da execução:__ o ideal neste caso é que sejam capturadas estas exceções e seja lançada uma exception que tenha relação com o contexto, além disso deve-se verificar se a exceção criada requer dados da exceção capturada, como por exemplo em casos de depuração. Esta prática é conhecida como Tradução da Exceção.
Padronize seu tratamento de exceptions em apis: apesar de não termos uma convenção a RFC 7807 tem orientações importantes que vale a pena aplicar no tratamento de respostas de erros. ( ver https://tools.ietf.org/html/rfc7807)


#### Qualidade em Testes

Testes estão relacionados a qualidade do software, a qualidade do software também é um item a ser analisado quando falamos de design. Porém podemos ter testes sem qualidade.
Existe muito a questão da análise de cobertura para entender se o conjunto de testes está satisfatório ou não. A questão é que a análise de cobertura identifica as linhas do projeto que foram executadas mediante aos testes. Isso nem sempre significa que você garantiu que todos os cenários possíveis fossem implementados, ou se em caso de modificação do código o seu teste garante o comportamento.
Quer saber se um teste vai garantir um comportamento? Image que haja modificação na estrutura do seu código, em caso que mude o comportamento seu teste deverá quebrar, certo? Pois então, em muitos casos os testes continuam passando.
Além disso os testes permitem maior segurança nas modificações de design de uma aplicação, e esta segurança está atrelada a qualidade que o teste existe possui.
Outro ponto é entender que quanto maior for sua gama de testes automatizados, melhor para que você tenha feedback dos problemas das alterações realizadas, principalmente em estruturas já existentes.
* __BDD:__ Não é uma tarefa, mas basicamente é integrar a qualidade no processo de desenvolvimento de software, costumo usar como referência que quando você usa BDD não existe uma coluna de testes ou uma tarefa de testes, porque qualidade está dentro do fluxo todo. Muitos acham que usar o Cucumber e ter um arquivo Gurkin é ter BDD, mas é muito mais que isso, é muito bom o uso do Cucumber, você ter os cenários escritos no seu Gerkin, mas isso são só um dos poucos artefatos que podem ser gerados durante a adoção do BDD no seu processo.
* __TDD:__ Um dos grandes problemas é que desenvolvedores são instruídos a programar para depois testar e acabam executando os testes para passarem, a abordagem do TDD no dia a dia requer investimento porque isso garante realmente uma melhoria na qualidade dos testes e também no desenvolvimento, mas como citei requer investimento pois a abordagem muda como pensamos e é normal que no começo tudo pareça confuso e difícil, especialmente quando você não tem noção do design que deseja.
* __Testes de Mutação:__ Permite verificar se nossos testes estão garantindo que mudanças no comportamento da aplicação serão identificadas por eles. Isso garante que modificações de design não impactem no comportamento, pelo menos nossos testes sinalizaram se houver mudanças.
* __Testes de Unidade:__ Testa a menor parte de um código
* __Testes de Contrato:__ Realiza verificação do contrato estabelecido por uma interface. Utilizado para testes de API, onde é verificado modelo de requisição e de resposta.
* __Testes de Integração:__ Requer testar fluxos com chamadas externas a aplicação
* __Testes end-to-end:__ testes que executam o fluxo completo de negócio.
* __Testes de componente:__ Teste o escopo de componentes, no caso do Java esse teste faz sentido quando queremos analisar a interação de componentes e seus dependentes.


#### Pair Programing

Pair Programing permite não só o nivelamento do time, como permite que um design seja construído com mais qualidade. 
Pontos de vista diferentes auxiliam para que problemas de design sejam identificados e corrigidos rapidamente, além de pensar em soluções mais amplas. Isso porque cada programador tem um background diferente de experiências, o que permite juntando elas obter um resultado melhor.
Time que está ganhando muda neste caso, é muito importante que sejam realizadas rotações entre os pares, para melhor a disseminação de conhecimento e para que haja mudança de pontos de vista sobre o design.
Muitas horas em pair também acabam não sendo produtivas, a recomendação é que não exceda mais da metade do seu dia, mas assim, varia de empresa para empresa, o que todas concordam é que 8 horas acaba sendo muito improdutivo.
É importante que o time tenha planejamento para aplicar pair, pois envolve agendas múltiplas e isso pode impactar para a aplicação do pair.
Em espaços físicos é importante que haja infra para trabalho em par e online é importante adoção de ferramentas que permitam acesso múltiplo ao mesmo ambiente.
É importante entendermos que par é com 2 pessoas envolvidas e existem várias abordagens, mas em nenhum dos casos é uma pessoa que faz só o que quer e domina pelo tempo inteiro o desenvolvimento, por isso evite distrações durante o pareamento, procure não fazer microgestão do seu par o que ele faz, tenha paciência com tempo de desenvolvimento do outro.

#### Code Review E Pull Request

A cultura de Code Review também possibilita nivelamento do time, e porque nivelamento do time é algo bom? Porque isso permite que todos entendam os problemas e estruturas existentes no contexto que trabalham e isso abre a possibilidade de através desse entendimento, conseguirem identificar os problemas e apresentar melhorias.
Além de permitir aumento do conhecimento técnico do time, o code review permite identificar e corrigir problemas rapidamente.
Para que um CR seja bem feito, é importante que haja uma boa descrição na abertura de um Pull Request, coloque as tarefas, épicos relacionados a mudança, os motivos das decisões tomadas, referências, impactos no produto e no design da aplicação. O ideal é que quem ler a descrição entenda o contexto da demanda e motivos pelos quais algumas decisões foram tomadas ou quais abordagens foram verificadas antes da solução ser implementada.
Porém para que o Code Review seja eficaz é necessário que todos entendam que análise humana é mais cara que automatizada e que isso requer analisar pontos que não são fáceis de automatizar através de ferramentas. É importante o time seguir um checklist e sempre revisitar ele conforme problemas forem identificados. Fazer comentários claros e nos trechos de códigos que estejam relacionados ao comentário Devemos entender o porquê da solução e não impor a solução que achamos mais adequada, a intenção é que a proposta de mudança faça sentido e não porque é preferência de quem revisou o código.

#### Documentação e Configuração

Porque precisamos de documentação? Qual a melhor documentação? Bom, pode ser que você assim como eu diga que a melhor documentação é o próprio código e como eu já descrevi faz todo sentido para mim. A questão é que todo projeto possui particularidades que até são possíveis entender lendo o código e “batendo cabeça”, porém, faz sentido fazer o desenvolvedor ou cliente perder tempo? O quanto isso é eficiente para o time? Será que ter informações de como executar a aplicação, informações sobre restrições de ambientes não auxiliam para que a energia seja focada em melhoria? Uma boa prática é que a documentação esteja no projeto para o desenvolvedor, quanto menos locais para gerenciar, melhor para manter atualizado. Por isso é importante que seu projeto tenha um README com informações do projeto como, descrição, funcionalidades, status do projeto, deploy da aplicação, como executar localmente, como executar testes, tecnologias envolvidas no projeto, acessos, links externos, qualquer informação que seja importante quem está trabalhando no projeto saber e que não deveriam estar na mente somente de uma pessoa da empresa.
Na dúvida, eu super recomendo este repositório git que possui templates ótimos de READMES https://github.com/jehna/readme-best-practices.
Além disso outra prática que percebo não ser muito adotada no dia a dia é a utilização de Javadoc em projetos, é claro que o código limpo é melhor que Javadoc, mas ainda assim, é uma alternativa. Isso permite que você tenha ao final do seu projeto uma boa documentação para o desenvolvedor.
Sobre a configuração, devemos entender que hardcode  não é uma opção e que inviabiliza muitas coisas no projeto. Devemos ter a prática de externalizar as configurações da aplicação, facilitando modificações necessárias sem a necessidade de realizar deploy na aplicação. Informações fixas bloqueiam melhorias no design de software.


#### Code Style e Ferramentas de anaĺise estática

Code Style é uma ótima forma de manter o padrão no desenvolvimento do código e isso impacta na construção e evolução do design da sua aplicação, além de garantir uma ótima qualidade. Talvez o primeiro que você ouviu falar foi o da Sun que possui convenções do Java, um outro muito adotado é o da Google.
Pensem que ter seu próprio code style é algo bom, pois sua empresa vai aplicar o que faz sentido para ela e para seus projetos.
Muitas empresas criaram seu próprio Code Style, muitas empresas partem desses modelos conhecidos e ainda criam mais itens, como é o caso do Twitter.
O que temos em um Code Style? É um conjunto de padrões de codificação de uma linguagem, abrangendo itens como formatação, convenções, regras de codificação.
Ferramentas de análise estática de código utilizam os parâmetros de code style para analisar o código em tempo de desenvolvimento, garantindo um mínimo de padrão entre os projetos de uma empresa.
Algumas ferramentas como Sonar, Checkstyle, Findbugs são utilizadas para análises de código e evita que problemas simples cheguem a etapa de Code Review. Além disso é importante que durante o Code Review práticas que podem ser adicionadas ao Code Style da empresa sejam adicionadas nos arquivos de configuração destas ferramentas para facilitar que o problema seja identificado em tempo de desenvolvimento.


## Conclusão   

Esse post foi uma primeira colaboração de alguém externo ao Java Bahia e que gostaríamos de apresentar nossa idéia e forma de fazer comunidade. Comunidade não é competição, a palavra chave é colaboração.