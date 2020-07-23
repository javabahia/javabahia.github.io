---
layout: post
title:  "Como posso colaborar com o site do Java Bahia?"
date:   2020-07-22 22:00:00 +0300
image:  javaba.png
author: Antonio Lazaro
tags:   [Jekyll, github, javabahia,comunidade]
---

## Como posso colaborar com o site?

Algumas pessoas nos procuraram para questionar como podem contribuir com o blog do Java Bahia. Resolvemos fazer esse post explicativo. Basicamente existem duas formas:

1. Submetendo um PR diretamente no post do github.
1. Clonando o repositório, rodando localmente e submetendo um PR para o repositório.

### 1. Quero escrever um post

#### 1. Acesse o diretório de posts

https://github.com/javabahia/javabahia.github.io/tree/master/_posts

#### 2. No canto superior direito, clique no botão Add File -> Create New File (ou faça upload)

1. Padrão do nome do arquivo: aaaa-mm-dd-titulo-separado-hifen.md Exemplo: 2020-07-22-como-contribuir-com-blog-com-pr.md
1. Estrutura do arquivo:

{% highlight powershell %}
---
layout: post
title:  "__Título desejado__"
date:   __Data da publicação__
image:  javaba.png
author: __SEU NOME__
tags:   [tag1, assunto, tema]
---

content em markdown 

{% endhighlight%}

##### Como usar markdown: 

1. https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
1. https://www.markdownguide.org/

#### 3. Ao concluir, submeter clicando no botão "Propose new file" 

Na mensagem do commit descreva quem é você e porque quer divulgar esse post no blog

#### 4. Isso vai te levar para tela para você criar o Pull Request

Descreva o objetivo do Pull Request.

#### 5. Aguarde revisão e aprovação ou comentários do Pull Request pelo time que administra o repositório do Java Bahia

Agora é só aguardar.

### 2. Clonando o repositório, rodando localmente o site e fazendo um PR

#### Como clonar o repositório?

https://docs.github.com/pt/github/creating-cloning-and-archiving-repositories/cloning-a-repository

#### Como o site funciona? Onde está hospedado?

Site funciona com o GithubPages que utiliza Jekyll com Markdown para linguagem de escrita.
1. https://pages.github.com/
1. jekyhttps://docs.github.com/en/github/working-with-github-pages/about-github-pages
1. https://docs.github.com/en/github/working-with-github-pages

#### Como instalo Jekyll?

##### Instalar gems (gerenciador de dependencias do ruby)
https://guides.rubygems.org/rubygems-basics/#installing-gems

##### Instalando e rodando Jekyll

{% highlight powershell %}

$ gem install bundler jekyll

$ jekyll new my-awesome-site

$ cd my-awesome-site

$ bundle exec jekyll serve

# => Now browse to http://localhost:4000 
{% endhighlight %}

Mais sobre instalação: https://jekyllrb.com/docs/installation/
Mais sobre jekyll: https://jekyllrb.com/

###### Como configurar um Domain .dev no githubs pages

Tem interesse em criar seu próprio blog e configurar com domínio ".dev"? Veja esse post: 
https://malaquias.dev/posts/como-configurar-um-dominio-do-google-domains-no-github-pages

##### Templates Jekyll

https://jekyllthemes.io/free
http://jekyllthemes.org/


## Conclusão

Tem alguma dúvida de como contribuir com a comunidade Java Bahia? Tem algo que possamos ajudar você a entender o fluxo? Comente e vamos tentar se ajudar para fazer nossa comunidade colaborativamente crescer. Pode abrir também uma Issue no github para entendermos as expectativas de vocês. 

No [primeiro post](http://localhost:4000/primeiro-post-novo-blog-java-bahia/){:target="\_blank"} falamos sobre isso um pouco e como geraram dúvidas, resolvemos fazer um post mais explicativo.