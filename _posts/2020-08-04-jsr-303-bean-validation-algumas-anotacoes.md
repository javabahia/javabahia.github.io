---
layout: post
title:  "Bean Validation, diferença entre: @NotNull,@NotEmpty e @NotBlank"
date:   2020-08-04 07:30:00 +0300
image:  javaba.png
author: Montival Junior
tags:   [Java, Bean Validation, JSR 303, Hibernate Validator]
---

## Idéia e motivação do artigo

Demonstrar a diferença entre anotações que geralmente causam dúvidas em iniciantes 
e estudantes de desenvolvimento Java que querem utilizar o Hibernate Validator, implementação de referência da [JSR 303 – Bean Validation API](https://beanvalidation.org/1.0/spec/){:target="\_blank"}.

## Objetivo

Mostrar aos desenvolvedores que utilizam a API Hibernate Validator, as diferenças entre anotações importantes da API, facilitando a melhor utilização destas em seus projetos.
Pra quem esse artigo pode ser útil
Desenvolvedores que desejam aprender o conceito das validações NotNull, NotEmpty e NotBlank e como integrá-las em suas aplicações.

### Sobre o Bean Validation 

Bean Validation é uma especificação que permite validar objetos com facilidade em diferentes camadas da aplicação. 
As restrições de Bean Validation são em forma de anotações, que estão disponíveis no pacote javax.validation.constraints.
Veja um exemplo de implementação:

{% highlight java %}
public class Carro {

   @NotNull
   private String fabricante;

   @NotEmpty
   @Size(min = 2, max = 14)
   private String placa;

   @Min(2)
   private int numeroDeAssentos;

   // ...
}
{% endhighlight %}

As anotações geralmente são bem intuitivas e autoexplicativas, como por exemplo: 

@Max = Informa que o valor do campo ou propriedade deve ser um valor inteiro menor ou igual ao número no elemento de valor.
@Min = De forma similar informa que é esperado um valor inteiro maior ou igual ao número no elemento de valor.
@Size = Se refere ao tamanho do campo ou propriedade. Este deve corresponder aos limites especificados.
@Null = O valor do campo ou propriedade não deve ser nulo...entre outras.
O Hibernate Validator será a implementação da JSR que utilizaremos no exemplo, você pode ver mais detalhes na própria documentação da biblioteca: https://docs.jboss.org/hibernate/validator/7.0/api/
Existem três anotações que sempre me geravam dúvidas quanto a seus usos e diferenças. E nós vamos focar nelas a partir de agora.
@NotNull, @NotEmpty ou @NotBlank?
É muito fácil imaginar que essas três anotações possuem a mesma função mas olhando na documentação do Hibernate Validator podemos entender as  diferenças entre essas anotações.
Primeiro temos que ter em mente que o  Java distingue entre String nulas e vazias. Uma String vazia é uma instância de String de comprimento zero, enquanto uma String nula, é um objeto sem uma referência de memória.


String teste = null;
@NotNull: false
@NotEmpty: false
@NotBlank: false

Com isso em mente vamos falar da annotation @NotNull.

### @NotNull

{% highlight java %}
public class UsuarioNotNull {

   @NotNull(message = “O campo nome não pode ser nulo”)
   private String nome;

   // ...
}
{% endhighlight %}

Como bem explícito no nome, essa annotation não permite que o valor seja nulo... porém permite campos vazios. Parece incoerente mas lembra do que falei acima? 
Se olharmos a classe NotNullValidator vamos notar a implementação do método isValid() que tem a regra da validação:

{% highlight java %}
   public Boolean isValid(Object object){
	return object != null;
   }
   {% endhighlight %}

Como mostrado acima, o método verifica apenas se o objeto é diferente de null, e vazio é diferente de null, pois existe uma referência de memória. Nesse caso, vazio seria um valor considerado válido.

String teste = "";
@NotNull: true
@NotEmpty: false
@NotBlank: false

Vamos avançar e falar um pouco sobre a annotation @NotEmpty.

### @NotEmpty

{% highlight java %}
public class UsuarioNotEmpty {

   @NotEmpty(message = “O campo nome não pode ser vazio”)
   private String nome;

   // ...
}
{% endhighlight %}

Um ponto importante aqui é que a anotação @NotEmpty faz uso da implementação da classe @NotNull  isValid(). Porém existe um adendo. 
Essa annotation também verifica se o tamanho do objeto fornecido é maior que zero. Dessa forma, se passarmos um "espaço" (" ") como valor ao parametro, a annotation irá considerar como um valor válido. Afinal um "espaço" não é nulo e possui tamanho maior que zero. Neste caso:

String teste = "";
@NotNull: true
@NotEmpty: true
@NotBlank: false

** Se quisermos ser ainda mais restritivos, podemos usar a anotação @NotEmpty em conjunto com @Size.
@NotEmpty(message = “O campo nome não pode ser vazio”)
@Size(min = 2, max = 32, message = “O campo nome deve ter entre 2 e 32 caracteres”)
private String nome;

### @NotBlank

{% highlight java %}
public class UsuarioNotBlank {

   @NotBlank(message = “O campo nome não pode estar em branco”)
   private String nome;

   // ...
}
{% endhighlight %}

A annotation @NotBlank faz a mesma verificação que NotNull e NotEmpty (se o objeto é diferente de null) , porém diferente da verificação feita por NotEmpty, aqui é utilizado o método trim() na verificação da String, apagando assim os espaços em branco na verificação do tamanho do valor. Podemos ver isso pelo método isValid() da classe NotBlankValidator.


{% highlight java %}
public Boolean isValid(CharSequence charSequence,
ConstrainValidatorContext constrainValidatorContext){
	If(charSequence == null){
		return object != null;
  	 }
	return charSequence.toString().trim().length() > 0;
}
{% endhighlight %}


Sendo assim espaços em branco não são levados em conta.
String nome = "Java Bahia";
@NotNull: true
@NotEmpty: true
@NotBlank: true

## Conclusão

Esse artigo mostrou que embora essas anotações aparentem ter a mesma finalidade, elas possuem propostas diferentes de verificação. Vamos resumir?
- @NotNull: Não permite um valor nulo, porém permite um valor vazio.
- @NotEmpty: Assim como  a @NotNull, não permite valor nulo e além disso seu tamanho deve ser maior que zero. Espaços em brancos são levados em conta na verificação de tamanho do valor.
- @NotBlank: Assim como a @NotEmpty, não permite valor nulo e o comprimento (sem considerar espaços em branco) deve ser maior que zero.

Sendo assim para validar um campo String de preenchimento obrigatório, não vazio, é indicado o uso de @NotBlank.

Montival Junior (Estudante Desenvolvimento Java):
- Github: https://github.com/MonthAlcantara
- Linkedin: https://www.linkedin.com/in/montivaljunior
- Page: https://monthalcantara.github.io/