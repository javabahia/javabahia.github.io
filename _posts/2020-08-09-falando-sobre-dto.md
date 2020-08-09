---
layout: post
title:  "Design Patterns - DTO"
date:   2020-08-09 09:00:00 +0300
image:  javaba.png
author: Montival Junior
tags:   [java,design patters,dto spring, javabahia, comunidade]
---

# DTO – Objeto de Transferencia de Dados

## Ideia do Post

A idéia deste post é apresentar o conceito do Padrão DTO e as conversões que precisam acontecer entre as entidades internas da aplicação e os DTOs externos (objetos de transferência de dados) publicados de volta para o cliente.

## Padrão de arquitetura

O __wikipedia__ define padrão de arquitetura como:
 “_...uma solução geral e reutilizável para um problema que ocorre com frequência em arquitetura de software dentro de um determinado contexto...._” 

Um Padrão de arquitetura é uma solução genérica que pode ser repetida de uma forma geral para um problema comum no design de software. Como o próprio nome sugere, não é algo acabado que pode ser transformado diretamente em algum tipo de código. É um modelo ou uma forma de resolver determinado problema que pode ser usado em várias situações diferentes. 
Nesse post iremos falar um pouco sobre um padrão de arquitetura bastante importante no desenvolvimento de aplicações.


## DTO – Objeto de Transferencia de Dados

Padrão __Objeto de Transferência de Dados__ (do inglês, __Data transfer object__ design pattern, ou simplesmente DTO) é um padrão de arquitetura de objetos que agregam e encapsulam dados para transferência.

Diferente dos objetos de negócio e dos objetos de acesso a dados (DAO), o DTO não possui qualquer tipo de comportamento. A sua função é  obter e armazenar dados.
Quando estamos trabalhando com uma interface remota, cada chamada ao servidor pode custar muito tempo de processamento, a depender da quantidade de dados. Com o DTO, podemos filtrar quais dados serão transmitidos e assim reduzir esse problema.

O DTO é bastante usado também quando não queremos expor todos os dados da nossa camada de persistência, mas precisamos exibir ao nosso cliente estes mesmos dados.
Vamos focar nosso post nessa linha de raciocício. 

## Entendo o contexto da aplicação

Utilizaremos como exemplo uma API REST criada com Spring Boot e que possui uma área de cadastro de usuários no sistema. 


Essa é a classe que representa os Usuários na nossa API:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura1.jpg)


A parte em que queremos focar do nosso Controller de Usuários ficou assim:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura2.jpg)

O método responsável pela criação de um usuário na nossa aplicação espera como parametro um Usuario. Este Usuario será recebido num formato Json no corpo da requisição, passará pela nossa regra de negócio na camada Service e posteriormente será persistido no banco de dados na nossa camada repository (Esses passos foram abstraídos no exemplo e nas imagens mas eles estão lá).

Aqui já começamos a perceber uma falha grave de segurança. Analisando nossa classe Usuário, veremos que ela possui um atributo do tipo Booleano, “Admin”, inicializada com valor “false”.

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura3.jpg)

Logo, caso seja passado o valor true para este parametro na requisição, qualquer um poderá se tornar aministrador da nossa aplicação. 
Tornar um usuário administrador não deve ser algo acessível a qualquer um, exige uma lógica e um tratamento individual na nossa aplicação, deve seguir regras e não ser liberado para qualquer um que tenha acesso ao nosso método salvar().  Sendo assim, o atributo “Admin” não deve ser recebido por meio deste tipo de requisição.

Se tivessemos uma classe apenas com os atributos essenciais para a criação de um cliente, não correríamos esse tipo de risco. Poderíamos usá-la para receber os parametros e assim, manipulá-los da forma que quisermos. 

A idéia do DTO é essa.

Vamos criar uma classe que, seguindo a convenção, se chamará UsuarioDTO e vamos dizer que esperamos um objeto desse tipo como parâmetro do método salvar() do nosso UsuarioController. 
Nesta classe vamos usar apenas os atributos que de fato devem ser passados pelo Cliente.

A permissão para transforamar um Usuário em Admin será feito posteriormente numa lógica seguindo a regra para tal. 
Como anotamos o id da nossa Classe Usuario com @GeneratedValue, ele será gerado automaticamente, não sendo assim necessario neste momento.


Dessa forma teremos como atributos da nossa Classe UsuarioDTO apenas nome, email e senha:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura4.jpg)


Agora sim podemos, em vez de, receber um Usuário com todos os atributos, receber um UsuarioDTO com apenas os atributos necessarios para a criação do Usuário.

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura5.jpg)


Só que agora temos um novo problema. O método salvar() do nosso UsuarioService, espera um Usuário como parametro, e não um UsuarioDTO. Isso é simples de resolver e existem diversas formas de fazer isso. Podemos falar sobre isso num outro post. Neste post aqui nós iremos fazer a conversão DTO – Entity utilizando a biblioteca ModelMapper.

### DOC ModelMapper: http://modelmapper.org/javadoc/


Adicionando Model Mapper ao nosso projeto

Para podermos utilizar o modelMapper em nosso projeto precisamos adcionar sua dependência no pom.xml:


![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura6.jpg)


É necessario também definirmos o bean ModelMapper em nossa configuração do Spring:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura7.jpg)

## Como funciona

O Model Mapper, entre outros, possui um método chamado map(), que espera receber dois parametros. O primeiro seria o objeto que estamos querendo converter e o segundo, a classe destino.
Recebidos, os dois parametros serão analisados ​​para determinar quais propriedades correspondem implicitamente de acordo com uma estratégia de correspondência e outra configuração. Traduzindo... serão checadas quais propriedades o objeto de origem têm em comum com a classe de destino e  mapeando de acordo com essas correspondências. Dessa forma criaremos um método específico para fazer essa conversão. No nosso exemplo ficará assim:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura10.jpg)

E nosso salvar() do UsuarioController ficará dessa forma:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura11.jpg)


Porém ainda temos um problema. Tanto a classe Usuario, como UsuarioDTO, possuem o atributo senha. Dessa forma ao enviarmos um Usuário ou até mesmo um UsuarioDTO para o Cliente como resposta a requisição, a senha deste ficará visível gerando uma nova falha de segurança. Quando enviamos uma resposta, queremos passar um Usuário para o cliente sem informar a senha. Como podemos fazer isso? É isso mesmo. Vamos criar um novo DTO e esse será exclusivo para respostas ao cliente. O nome dessa classe será UsuarioRespostaDTO e ficará assim:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura12.jpg)


Assim como fizemos com o UsuarioDTO , precisaremos agora converter um Usuário em UsuarioRespostaDTO. De forma similar criaremos um método para isso:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura13.jpg)


Por fim o retorno do nosso método de salvar() do nosso Controller será:

![Modelo de Classes](/img/posts/2020-08-09-falando-sobre-dto/figura14.jpg)


## Conclusão

Este post explicou a idéia central do padrão de projeto DTO e tentou mostrar sua utilidade e a forma de manipular os dados recebidos e enviados na comunicação servidor – cliente.
Existem outras formas de fazer a conversão entidade – DTO. Como a idéia central era explicar sobre o DTO, esses outras formas não foram abordadas nesse post. Deixe seu comentário caso você queira u post específico sobre esse tema.

## Links Interessantes:
- [Dev Media](https://www.devmedia.com.br/diferenca-entre-os-patterns-po-pojo-bo-dto-e-vo/28162)
- [Model Mapper](http://modelmapper.org/)
- [Baeldung](https://www.baeldung.com/entity-to-and-from-dto-for-a-java-spring-application)


## Montival Junior(Estudante Desenvolvimento Java)

- [Github:](https://github.com/MonthAlcantara)
- [Linkedin:](https://www.linkedin.com/in/montivaljunior)
- [Blog pessoal:](https://monthalcantara.github.io/)
