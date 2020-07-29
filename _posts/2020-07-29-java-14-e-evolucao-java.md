---
layout: post
title:  "Java 14 e o que vem por ai?"
date:   2020-07-29 19:00:00 +0300
image:  javaba.png
author: Antonio Lazaro
tags:   [Java14,Java]
---

## Sistema de versionamento atual do Java (LTS x Non-LTS)

As pessoas seguem batendo na tecla reclamando do Java informando que é uma linguagem verbosa, antiga e volta e meia ouvimos que o "Java morreu". Entretanto, Java, vai além de uma simples linguagem de programação, O Java criou um ecosistema robusto e maduro de desenvolvimento que bem ou mal, diversas plataformas e linguagens caminham para desenvolver o mesmo tipo de estrutura.

Um comitê para definir evolução da linguagem (JCP), sistema de gerenciador de dependências (MAVEN, depois veio gradle e Ivy), padrões de codificação (code style), flexibilidade para criação de frameworks (início do desenvolvimento) até consolidação de especificações que definem padrões de implementações para frameworks que surjam dentro da plataforma. Essas, ao meu ver, são algumas das contribuições das comunidades e do ecosistema Java que observo em outras linguagens. Não quero dizer com isso, que Java inventou isso, mas tudo que aprendi foi no Java e vejo hoje algumas linguagens lançando isso, depois de tantos anos de uso. 

Versão | Lançamento | Fim do suporte público
JDK Beta | 1995 | ?
JDK 1.0 | 01/1996 | ?
JDK 1.1 | 02/1997 | ?
J2SE 1.2 | 12/1998 | ?
J2SE 1.3 | 05/2000 | ?
J2SE 1.4 | 02/2002 | 10/2008
J2SE 5.0 | 09/2004 | 11/2009
Java SE 6.0 | 12/2006 | 04/2013
Java SE 7.0 | 07/2011 | 04/2015
Java SE 8.0 (LTS) | 03/2014 | 01/2019 Versão da JDK da Oracle 05/2026 AdoptOpenk JDK 06/2023 Amazon Correto
Java SE 9.0 | 09/2017 | 03/2018 
Java SE 10.0 | 03/2018 | 09/2018
Java SE 11.0 (LTS) | 09/2018 | 10/2024 AdoptOpenk JDK 08/2024 Amazon Correto
Java SE 12.0 | 03/2019 | 09/2019
Java SE 13.0 | 09/2019 | 03/2020
Java SE 14.0 (ATUAL) | 03/2020 | 09/2021
Java SE 15.0 | 09/2020 | 03/2021
Java SE 16.0 | 03/2021 | 09/2021
Java SE 17.0 (LTS) | 09/2021 | Não definido

Antes do lançamento das releases semestrais, O Java teve ciclos de lançamentos irregular e muito longo pra uma plataforma de tecnologia, como se pode observar com releases demorando anos para serem atualizadas. A partir da versão 8.0, houve uma mudança estrutura e na forma de fazer a gestão do Java.

O documento "Java is Still Free" que pode ser lido 
<a download="Java Is Still Free (PT-BR).pdf" href="/img/docs/Java-Is-Still-Free-(PT-BR).pdf" title="Java Is Still Free (PT-BR).pdf">
    aqui, 
</a>
explica o que mudou e que as vezes gera confusão na cabeça das pessoas sobre a gratuidade ou não do Java.

Deve se observar com bastante cautela a questão das releases não LTS (Long-Term-Support) para ambientes produtivos, porque o tempo de suporte a essa release é até o próximo lançamento. [Esse artigo do Baldeung, apresenta de maneira bem didática sobre como funciona esse novo modelo.](https://www.baeldung.com/java-time-based-releases){:target="\_blank"}

O java Evolui a partir de JEPs, que são JDK Enhancement Proposal e podem ser entendida na especificação como [JEP 1](http://openjdk.java.net/jeps/1){:target="\_blank"}.

A [JEP 2](http://openjdk.java.net/jeps/2){:target="\_blank"}, define o template de escrita de propostas e a [JEP 3](http://openjdk.java.net/jeps/3){:target="\_blank"}, descreve o processo de release do JDK

## Explicado o modelo, vamos ao Java 14

Extraído de um post da Oracle, referenciado na seção de referências, trago aqui algumas informações sobre o Java 14.

### Java 14, juntos
Similar ao Java 11, Java 12 e Java13, celebra as contribuições feitas ao Java 14 por vários indivíduos e organizações da Comunidade do OpenJDK — todos compilaram Java, juntos!

### Índice de correção do JDK 14
O índice geral de alterações no JDK ao longo do tempo permaneceu essencialmente constante por muitos anos, mas, na cadência de seis meses, o ritmo em que inovações prontas para produção são entregues melhorou imensamente. Em vez de se disponibilizarem dezenas de milhares de correções e cerca de cem JDK Enhancement Proposals (JEPs) disponíveis em um grande lançamento a cada poucos anos, os aperfeiçoamentos são fornecidos em versões menores de recursos em um cronograma de seis meses, mais gerenciável e previsível. Essas alterações podem variar de um recurso significativo a pequenos aprimoramentos e manutenção de rotina, correção de bugs e melhorias na documentação. Cada alteração é representada em um único commit para um único problema no JDK Bug System.

### Novidades no Java 14

O Java 14 oferece aos usuários dezesseis aperfeiçoamentos/alterações principais, que incluem dois módulos incubadores, três recursos em versão prévia, dois recursos preteridos e duas remoções.

Os 16 JEPs fornecidos com o JDK 14 são:

#### 1. JEP 305 - Pattern Matching for instanceof (Preview)

Este recurso em versão prévia melhora o Java com correspondência de padrão para o operador instanceof.  Isso melhora a produtividade do desenvolvedor ao eliminar a necessidade de código padrão e permite código fortemente tipado mais conciso.

#### 2. JEP 343 - Packaging Tool (Incubator)

Esta ferramenta incubadora fornece uma forma para desenvolvedores empacotarem aplicativos Java para distribuição em formatos específicos da plataforma.  A ferramenta ajuda desenvolvedores com aplicativos modernos em que limitações requerem que tempos de execução e aplicativos sejam empacotados em uma única entrega.

#### 3. JEP 345 - NUMA-Aware Memory Allocation for G1

Este recurso melhora o desempenho geral do coletor de lixo G1 em sistemas de acesso não uniforme à memória NUMA).

#### 4. JEP 349 - JFR Event Streaming

Este recurso expõe dados do JDK Flight Recorder (JFR) para monitoramento contínuo, o que simplificará o acesso a dados do JFR a várias ferramentas e aplicativos.

#### 5. JEP 352 - Non-Volatile Mapped Byte Buffers

Este recurso adiciona um modo de mapeamento de arquivos para o JDK quando se usa memória não volátil.  A natureza persistente da memória não volátil altera muitos pressupostos de persistência e desempenho que podem ser aproveitados com este recurso.

#### 6. JEP 358 - Helpful NullPointerExceptions

Este recurso melhora a usabilidade de NullPointerExceptions ao descrever precisamente qual variável era nula e outras informações úteis.  Isso melhorará a produtividade de desenvolvedor e a qualidade de muitas ferramentas de desenvolvimento e de depuração.

#### 7. JEP 359 - Records (Preview)

Este recurso em versão prévia fornece uma sintaxe compacta para declarar classes que contêm dados superficialmente imutáveis.  Superficialmente, este ótimo recurso reduz muito códigos padronizados em classes deste tipo, mas, em última análise, o objetivo é permitir uma melhor modelagem de dados como dados.  Declarar agregados de dados nominais superficialmente imutáveis deve ser fácil, claro e conciso.

#### 8. JEP 361 - Switch Expressions

Este era um recurso em versão prévia no JDK 12 e no JDK 13 e agora está concluído.  Ele permite que switch seja usado tanto como uma instrução quanto como uma expressão.  Este recurso simplifica a codificação cotidiana e preparou o caminho para o recurso de correspondência de padrão (JEP 305) incorporado como versão prévia nesta versão.

#### 9. JEP 362 - Deprecate the Solaris and SPARC Ports

Este JEP substitui as portas Solaris e SPARC com o objetivo de removê-las em uma versão futura.  

#### 10. JEP 363 - Remove the Concurrent Mark Sweep (CMS) Garbage Collector

O coletor de lixo de CMS foi dispensado há dois anos e o G1, que é o sucessor pretendido da CMS desde o JDK 6, tem sido o coletor padrão e usado em larga escala há muitos anos.  Também vimos a introdução de dois novos coletores, ZGC e Shenandoah, com muitos aperfeiçoamentos no G1 no mesmo período.  

#### 11. JEP 364 - ZGC on macOS

Embora a maioria dos usuários que precisam do ZGC também precisem da escalabilidade de ambientes baseados em Linux, ele também é frequentemente necessário para desenvolvimento e teste em Windows e macOS.  Também há certos aplicativos de área de trabalho que se beneficiarão das capacidades do ZGC.  Portanto, o recurso ZGC foi transferido para o Windows e o macOS.

#### 12. JEP 365 - ZGC on Windows

Consulte o resumo do JEP 364.

#### 13. JEP 366 - Deprecate the ParallelScavenge + SerialOld GC Combination

Este dispensa a combinação dos algoritmos Parallel Scavenge e Serial Old, que é raramente usada, com a intenção de removê-la em uma versão futura.

#### 14. JEP 367 - Remove the Pack200 Tools and API

Este remove as ferramentas pack200 e unpack200 e a API Pack200 no pacote java.util.jar. Essas ferramentas e API foram dispensadas para remoção no Java SE 11.

#### 15. JEP 368 - Text Blocks (Second Preview)

Após receber feedback quando Text Blocks foi introduzido como um recurso em versão prévia (JEP 355) como parte do Java 13, duas novas sequências de escape foram adicionadas e Text Blocks está sendo oferecido como um recurso em versão prévia pela segunda vez. Os benefícios do recurso Text Blocks incluem: escrita simplificada de programas usando cadeias de caracteres que abrangem várias linhas de código-fonte, ao mesmo tempo em que evita sequências de escape em casos comuns; legibilidade aprimorada de cadeias de caracteres em programas Java que denotam código escrito em linguagens não Java; suporta a migração de cadeia de caracteres literais ao estipular que qualquer novo constructo pode expressar o mesmo conjunto de cadeias de caracteres que uma cadeia de caracteres literal, interpretar as mesmas sequências de escape e ser manipuladas das mesmas formas que um cadeia de caracteres literal.

#### 16.JEP 370 - Foreign-Memory Access API (Incubator)

Este módulo incubador introduz uma API para permitir que programas Java acessem memória externa fora do heap Java de maneira segura e eficiente.

### Suporte a ferramentas

O suporte corrente e atualizado a ferramentas ajuda a aumentar a produtividade do desenvolvedor.  Com o Java 14, continuamos a acolher os esforços de fornecedores líderes de IDE cujas soluções de ferramentas oferecem aos desenvolvedores suporte para as versões atuais do Java.  Os desenvolvedores podem esperar receber o suporte ao Java 14 com os seguintes IDEs:

1.    [JetBrains IDEA](https://blog.jetbrains.com/idea/2020/03/java-14-and-intellij-idea/?source=:ow:evp:cpo:::rc_lamk200615p00076:oer400070758,:ow:lp:cpo::){:target="\_blank"}
2.    [Apache NetBeans](https://netbeans.apache.org/download/nb113/index.html?source=:ow:evp:cpo:::rc_lamk200615p00076:oer400070758,:ow:lp:cpo::){:target="\_blank"}
3.    [Eclipse IDE](https://marketplace.eclipse.org/content/java-14-support-eclipse-2020-03-415/help?source=:ow:evp:cpo:::rc_lamk200615p00076:oer400070758,:ow:lp:cpo::){:target="\_blank"}

#### Download JDK

Pode ser baixada nesse [link.](https://jdk.java.net/14/?source=:ow:evp:cpo:::rc_lamk200615p00076:oer400070758,:ow:lp:cpo::){:target="\_blank"}. Recomendo fortemente a utilização do SDK Man como ferramenta de gestão de JDK em sua máquina. [Link para instalação e configuração](https://sdkman.io/){:target="\_blank"}.

#### Recurso mais expressivo

[Nesse artigo](https://blogs.oracle.com/oracle-brasil/java-14-torna-codigo-super-expressivo-dizem-desenvolvedores?source=:ow:evp:cpo:::RC_LAMK200615P00076:OER400070758&intcmp=:ow:evp:cpo:::RC_LAMK200615P00076:OER400070758&elqTrackId=e69482bb6fd0429bb1697f3ec9b22fc3&elqaid=96279&elqat=2&source=:ow:lp:cpo::){:target="\_blank"}, é possível obter a opnião de especialistas renomados, inclusive o Dr Venkat Subramaniam, autor premiado e fundador da Agile Developer, que veio ao Brasil e a Salvador no ano passado.

Vejam o que ele diz: "__Eu sou uma daquelas pessoas que vivem reclamando que o Java é detalhado demais", diz Venkat Subramaniam, autor premiado e fundador da Agile Developer. Embora as ferramentas de edição de código (IDEs) aliviem esse fardo ao produzir automaticamente algumas instruções no código-fonte, diz ele, elas podem produzir o que os desenvolvedores chamam pejorativamente de "vômitos de código__

É por esse motivo que há um esforço contínuo, com o ciclo de lançamento a cada seis meses, para simplificar a linguagem, removendo o excesso de detalhes e reduzindo os recursos obsoletos. “__O Java 14 remove muito ruído no código", diz Subramaniam, apontando para os recursos Records,  Pattern Matching e Switch Expressions. (Switch Expressions foi lançado pela primeira vez no JDK 12). Esses recursos removem o código clichê e tornam o código altamente expressivo e intuitivo—fácil de escrever e manter.__”

## Conclusão

Por fim, para dar dimensão da grandeza do Java e sua utilização, separei alguns projetos Java de grande relevância do artigo especial da Oracle sobre os melhores aplicativos Java já escritos.

### Maestro, controlador de rovers em Marte. 

Em 2004, o Java se tornou a primeira linguagem de programação a expandir o alcance planetário da humanidade. Durante três meses naquele ano, cientistas que trabalhavam no Laboratório de Propulsão a Jato (JPL, Jet Propulsion Laboratory) da NASA em Pasadena, Califórnia, usaram o sistema Maestro Science Activity Planner em Java, construído pela equipe de interface de robôs do JPL, para controlar o rover Spirit em suas explorações pelo planeta vermelho. A experiência com Java havia começado muitos anos antes no JPL, com a criação de um sistema de comando e controle para o rover Sojourner de 1995. O fundador do Java, James Gosling, passou tanto tempo no JPL que se tornou membro do conselho consultivo.

### Wikipedia Search. 

Faz sentido que uma enciclopédia criada para as pessoas e pelas pessoas seja executada em software de código aberto — e ofereça um mecanismo de pesquisa desenvolvido em Java. O Lucene, escrito por Doug Cutting em 1999 e batizado com o nome do meio de sua esposa, era na verdade o quinto mecanismo de pesquisa desenvolvido por Cutting. Ele criou os outros como engenheiro para a Xerox PARC, Apple e Excite. Em 2014, a Wikipedia substituiu o Lucene pelo Elasticsearch, um mecanismo de pesquisa distribuído, habilitado por REST e também escrito em Java.

### Hadoop. 

O Lucene não é a única contribuição de Cutting para a nossa lista. Inspirado em um artigo de pesquisa da Google que descreve o algoritmo MapReduce para processamento de dados em grandes clusters de computadores convencionais, em 2003 Cutting escreveu uma estrutura de código aberto para operações do MapReduce em Java e a chamou de Hadoop, em homenagem ao elefante de brinquedo de seu filho. O Hadoop 1.0 foi lançado em 2006, impulsionando a tendência do big data e inspirando muitas empresas a criar "data lakes", definir estratégias para analisar os "dados de exaustão" e considerar os dados como "o novo petróleo". Em 2008, o Yahoo (onde Cutting trabalhava na época) alegou que seu Search Webmap, executado em um cluster Linux com 10 mil núcleos, era o maior aplicativo Hadoop de produção do mundo. Em 2012, o Facebook afirmou ter mais de 100 petabytes de dados no maior cluster Hadoop do mundo.

### Minecraft. 

O ambiente pacífico desse jogo — com biomas, pessoas e casas que você mesmo constrói usando blocos de construção — mantém crianças e adultos do mundo todo em um estado prolongado de fascinação, o que faz dele o videogame mais popular da história. Desenvolvido em Java por Markus "Notch" Persson e lançado em versão alfa em 2009, o Minecraft e seu universo 3D são uma fonte inesgotável de criatividade, porque não há dois mundos criados que sejam iguais. O uso de Java pelo videogame também permite que programadores, em casa e na escola, criem seus próprios mods. 

### Jenkins. 

Criado em 2004 por Kohsuke Kawaguchi, engenheiro da Sun Microsystems, o Jenkins é um poderoso servidor de integração contínua de código aberto. Escrito em Java, o Jenkins ajuda a criar, testar e implantar aplicativos de maneira rápida e automática. Ele costuma ser reconhecido como uma das primeiras ferramentas de DevOps que possibilitaram a "infraestrutura como código". O Jenkins e seus mais de 1.500 plugins criados pela comunidade dão conta de inúmeras tarefas de implantação e teste, incluindo trabalhar com o GitHub, dar suporte a desenvolvedores daltônicos e fornecer um arquivo JAR do MySQL Connector.

### Integrated Genome Browser. 

A corrida para mapear o genoma humano começou em 1990 e terminou 13 anos depois, quando pesquisadores médicos conseguiram sequenciar os 3 bilhões de pares de bases de DNA do biotecnólogo Craig Venter, após uma década de trabalho envolvendo 3 mil pessoas a um custo de 3 bilhões de dólares. Quando o sequenciamento foi concluído, os cientistas ficaram ansiosos para mergulhar no código fonte da nossa espécie — mas como? Entre no navegador de genoma baseado em Java, uma ferramenta de visualização desenvolvida por uma equipe, que incluía a professora de bioinformática Ann Loraine, para explorar os datasets básicos e as anotações dos genes de referência. O código aberto do Integrated Genome Browser permite que os pesquisadores aumentem e diminuam o zoom e representem graficamente os dados genômicos, a fim de identificar e anotar características genéticas. Em linha com essa iniciativa mundial, uma ferramenta semelhante foi desenvolvida na Universidade da Califórnia, em Santa Cruz, na forma do Genome Browser, gerenciado por Jim Kent.

### Visible Tesla. 

Esse aplicativo escrito em Java foi criado por Joe Pasqua, um entusiasta dos automóveis Tesla, em 2013 como um programa gratuito para monitorar e controlar seu Tesla Model S. O VisibleTesla, inspirado na comunidade do Tesla Motors Club, oferece recursos semelhantes aos encontrados no aplicativo móvel oficial da montadora de carros elétricos. Os usuários podem configurar cercas geográficas e notificações para eventos, como uma porta destrancada ou o estado da carga da bateria, além de coletar e manipular dados de viagem. O código aberto do projeto está no GitHub.

Quer saber um pouco mais do código-fonte do JDK tem o [repositório no Github](https://github.com/openjdk/jdk).

O que vem no JDK 15? Alguns artigos e o roadmap nos links abaixo:

- https://openjdk.java.net/projects/jdk/15/
- https://www.infoworld.com/article/3534133/jdk-15-the-new-features-in-java-15.html
- https://www.techgeeknext.com/java/java15-features


## Referencias

- https://blogs.oracle.com/oracle-brasil/o-java-14-chegou?source=:ow:evp:cpo:::RC_LAMK200615P00076:OER400070758&intcmp=:ow:evp:cpo:::RC_LAMK200615P00076:OER400070758&elqTrackId=900c3919f5ad4fa0aa8e09f032f04610&elqaid=96279&elqat=2&source=:ow:lp:cpo::
- https://blogs.oracle.com/java-platform-group/the-arrival-of-java-14?source=:ow:evp:cpo:::rc_lamk200615p00076:oer400070758,:ow:lp:cpo::
- https://blogs.oracle.com/oracle-brasil/nosso-mundo-movido-a-java?source=:ow:evp:cpo:::rc_lamk200615p00076:oer400070758,:ow:lp:cpo::
- https://blog.ippon.tech/comparing-java-lts-releases/
- 