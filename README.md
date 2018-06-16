Glossario Programação Orientada a Objetos.
========
Revisão de conceitos de programação orientada à objetos.

Sumário
========
* [Construtor](#construtor)
* [Instanciação](#instanciação)
* [Palavra reservada new](#palavra-reservada-new)
* [Palavra reservada instanciof](#palavra-reservada-instanciof)
* [Encapsulamento](#encapsulamento)
* [Palavra reservada this](#palavra-reservada-this)
* [Getters e Setters](#getters-e-setters)
* [Palavra reservada public e private](#palavra-reservada-public-e-private)
* [Assinatura de metodo](#assinatura-de-metodo)
* [Escopo de classe](#escopo-de-classe)
* [Escopo de objeto](#escopo-de-objeto)
* [Palavra reservada final](#palavra-reservada-final)
* [Relacionamento de Dependência](#relacionamento-de-dependência)
* [Relacionamento de Agregação](#relacionamento-de-agregação)
* [Relacionamento de Composição](#relacionamento-de-composição)
* [Referências](#referências)


Construtor
========


Construtor é um metodo especial que é chamado sempre que é criado um objeto.

1 - O construtor tem sempre o mesmo nome da classe. <p>
2 - Ele so sera chamado quando for criado o objeto da classe, e não mais.<p><p><p><p>
3 - Ele nao tem tipo de retorno. Nem mesmo void!<p><p><p>
4 - Caso voce nao esteja certo a respeito do tipo de argumento, voce pode criar varios construtores, lembrando que o que muda é os argumentos e suas ordens.<p><p>
5 - Mesmo que voce nao esteja criando um construtor, por padrao, o Java tem um construtor vazio. 

##### Exemplo:

```java
class Pessoa {
   String tipo = "";
   public Pessoa(String tipo){
      this.tipo = tipo; //Aqui, o this.tipo representa a variavel que esta fora do escopo, ou seja, o que recebemos como argumento
                             //é passado para a variavel de instancia.
   }
   public String getTipo(){
      return tipo;
   }
}
```


Instanciação
========


Quando você instancia a classe, você cria um objeto na memória, do tipo da classe.


##### Exemplo:

````java
Livro livro = new Livro();
````

Palavra reservada new
========


O operador new tem o propósito de criar um novo objeto, o new faz:

1 - instancia a classe através da atribuição de memória para um novo objeto;

2 - retorna uma referência à memória alocada;

3 - chama o construtor do objeto.


##### Exemplo:


````java
Point p1 = new Point();
Point p2 = p1;
p2.x = 2;
p2.y = 3;
// p1 e p2 representam o ponto (2,3)
````



Palavra reservada instanciof
========


Determina se um objeto é uma instância de determinada classe, superclasse ou interface


##### Exemplo:


````java
Carro c = new Subaru();
        if (c instanceof Subaru){
            System.out.println("True");
        }else{
            System.out.println("false");
        }
// verifica se o seu carro é um subaru e neste caso é true
````



Encapsulamento
========


O encapsulamento é um conceito da Programação Orientada a Objetos onde o estado de objetos (as variáveis da classe) e seus comportamentos (os métodos da classe) são agrupados em conjuntos segundo o seu grau de relação.

Para isso, utilizamos os modificadores de acesso existentes em java. Estes modificadores funcionam da seguinte forma:

 - public: Qualquer objeto pode acessar o membro;<br>
 - default: Qualquer objeto do mesmo pacote pode acessar o membro e subclasses de outros pacotes;<br>
 - protected: O membro é acessível apenas por objetos do mesmo pacote;<br>
 - private: O membro é acessível apenas internamente (próprio objeto);<br>

##### Exemplo:

````java
class Conta { 
           
    private double salario; 
    private String nome;
  
}
````

Palavra reservada this
========

A palavra reservada this representa o objeto em execução. Para ficar mais claro vai um simples exemplo


##### Exemplo:


````java
class MinhaClasse{

private int numero;

MinhaClasse(int numero){ //sombreamento da variável de instancia.

  this.numero = numero; // se você não colocar o this o compilador não sabe quem é quem
}
}
````




Getters e Setters
========


1 - GET é quando vc quer pegar um valor;<br>
2 - SET é quando vc deseja setar ou enviar algo, algum valor.


##### Exemplo:


````java
class Conta {
  private double limite;
  private double saldo;
   
  public double getSaldo() {
    return saldo;
  }
   
  public void setSaldo(double saldo) {
    this.saldo = saldo;
  }
   
  public double getLimite() {
    return limite;
  }
   
  public void setLimite(double limite) {
    this.limite = limite;
  }
}
````




Palavra reservada public e private
========

Modificador de acesso public<br>
A instrução public indica que a classe, método ou variável assim declarada possa ser acessada em qualquer lugar e a qualquer momento da execução do programa.

##### Exemplo

<img src="https://www.java-made-easy.com/images/xcubed-root-circumference-area-in-java.jpg.pagespeed.ic.WWuBUcZs17.jpg"/>



Modificador de acesso private<br>
O modificador de acesso "private" quando aplicado a um atributo ou a um método indica que os mesmos só podem ser acessados de dentro da classe que os criou (encapsulamento). Uma classe que herde de uma superclasse com atributos declarados como "private" só poderá ter acesso a eles através dos métodos públicos da própria superclasse, caso contrário, não haverá acesso a estes atributos.

##### Exemplo

````java
class Circulo
{    
    private float raio;
    Circulo()
       {
          super();
          setRaio( 3.0 );
       }
    void setRaio( float r )
       {
          raio = r
       }
}
class Pneu extends Circulo
{
    Pneu p = new Pneu();
    p.raio = 10.0; //Erro de compilação. O Atributo raio é privado da classe Circulo
    p.setRaio(10.0); //Correto, pois a classe Pneu está utilizando os métodos definidos na classe Circulo para fazer
                     //acesso ao atributo privado raio
````


Assinatura de metodo
========


A assinatura é uma combinação do nome do método, tipos e ordem dos seus parâmetros.


##### Exemplo:


Declaração: 
````java
public void facaAlgo (int Valor, String st)
````

Assinatura: 
````java
facaAlgo(int, String)
````

Sobrecarga de método
========


A sobrecarga de métodos (overload) é um conceito do polimorfismo que consiste basicamente em criar variações de um mesmo método, ou seja, a criação de dois ou mais métodos com nomes totalmente iguais em uma classe. A Sobrecarga permite que utilizemos o mesmo nome em mais de um método contanto que suas listas de argumentos sejam diferentes para que seja feita a separação dos mesmos.


##### Exemplo:

````java
class Adder{  
static int add(int a,int b)
{return a+b;}  
static int add(int a,int b,int c)
{return a+b+c;}  
}  
class TestOverloading1{  
public static void main(String[] args){  
System.out.println(Adder.add(11,11));  
System.out.println(Adder.add(11,11,11));  
}} 
````




Escopo de classe
========


Escopo de classe se refere-se à vida e acessibilidade de uma variável. Quão grande é o alcance depende de onde uma variável é declarada. Por exemplo, se uma variável é declarada na parte superior de uma classe, ela será acessível a todos os métodos de classe. Se for declarada num método, em seguida, só pode ser utilizada em tal método.


##### Exemplo:


````java
public class Planetas {
 
 // Variavel da classe é compartilhada por todos
 public static long numeroDePlanetas;
 
 // Variavel de intancias
 private double x, y;
 private double massa;
 public String apelido;
 
      // Construtor
      //  x e y são  variaveis instanciadas,
      //  mas newX and newY são variaveis locais
      //  O construtor incrementa o valor
    public  Planetas(double novoX, double novoY, double novaMassa)
    {
       x = novoX;
       y = novoY;
 
       massa = novaMassa;
       numeroDePlanetas++;
    }
}
````




Escopo de objeto
========


VARIÁVEL GLOBAL – Existem durante a execução de todo o programa e podem ser utilizadas por qualquer função. Elas devem ser declaradas fora de qualquer função, inclusive do main(), e no início de um programa.

VARIÁVEL LOCAL – Só pode ser utilizada pela função ou bloco que a declarou. Ela não é reconhecida por outras funções e só pode ser usada dentro do bloco de função onde está declarada. Uma variável local é criada quando a função começa a ser executada e destruída no final da execução dessa função.

VARIÁVEL DE PARÂMETRO – Inicializadas no momento da chamada da função. Eles também só existem dentro da função onde foram declarados. Embora sejam utilizadas como inicialização da função, elas podem ser utilizadas normalmente como uma variável local dentro do bloco de função onde estão.

##### Exemplo:

````java
public class Empresa {
// variavel global
int a;
public static void main(String [ ] args) {
````

````java 
//variavel local
int x, y, z;
// …
}
````

````java 
//variavel parâmetro
public static int parceiros(int x, y) {
int w;
// …
}
}
````




Palavra reservada final
========


Modificador final<br>
A instrução final indica que a classe, método ou variável assim declarada têm uma única atribuição que se mantém constante, ou seja, não pode ser alterada no decorrer do processamento.
Além de não admitir a criação de classes filhas.
Este modificador declara o que chamamos, em programação, de constante.


##### Exemplo:


````java
public class MyClass {
 
    private final int teste;
 
    public MyClass() {
        teste = 10; // Ok, pois inicializamos o valor no construtor.
    }
 
    public void foo() {
        teste++; // Não é permitido...
    }
}
````




Relacionamento de Dependência
========


Tipo menos comum de relacionamento
Identifica uma ligação fraca entre objetos de duas classes

1 - Representado por uma reta tracejada entre duas classes<br>
2 - Uma seta na extremidade indica o dependente<br>

Quando uma classe recebe um objeto de outra classe como parâmetro, uma classe acessa o objeto global da outra. Nesse caso existe uma dependência entre estas duas classes, apesar de não ser explícita.



##### Exemplo:


<img src = "http://www.linhadecodigo.com.br/artigos/img_artigos/admilson_nogueira/uml_dependencia.jpg"/>




Relacionamento de Agregação
========


Tipo especial de associação<br>
Demonstra que as informações de um objeto precisam ser complementadas por um objeto de outra classe<br>
Associações:<br> 
1 - Todo-Parte<br>
2 - Objeto-Todo<br>
3 - Objeto-Parte<br>


##### Exemplo:


<img src="http://www.dsc.ufcg.edu.br/~jacques/cursos/map/html/uml/diagramas/classes/images/agregacao.GIF"/>

````java
public class A {
    private B b;
    public A( ){
    }
    public void setB( B b ){
         this.b = b;
    }
    public B getB( ) {
        return b; 
    }
}
````
````java

public class B {
    public B( ){
    }
}
````




Relacionamento de Composição
========


Uma variação do tipo agregação<br>
1 - Representa um vínculo mais forte entre objetos-todo e objetos-parte<br>
2 - Objetos-parte têm que pertencer ao objeto-todo<br>
3 - O todo não existe (ou não faz sentido) sem as partes<br>
Ou, as partes não existem sem o todo<br>



##### Exemplo:


<img src="http://www.dsc.ufcg.edu.br/~jacques/cursos/map/html/uml/diagramas/classes/images/composicao.GIF"/>

````java 
public class A {
    private B b;
    public A( ){
        b = new B();
    }
}
````
````java

public class B {
    public B( ){
    }
}
````




Referências
========

* http://www.guj.com.br/t/o-que-e-construtor/70766<br>
* http://respostas.guj.com.br/4712-iniciante-com-java-o-que-significa-instanciar-um-classe<br>
* http://respostas.guj.com.br/40560-palavra-reservada-new<br>
* https://webserver2.tecgraf.puc-rio.br/~marcio/cursos/dloads/prog3_JAVA/ReviewOO1.pdf<br>
* http://www.guj.com.br/t/quando-usar-o-instanceof/183227/4<br>
* http://aprendendojavajuntos.blogspot.com/2012/02/encapsulamento.html<br>
* http://www.guj.com.br/t/a-palavra-reservada-this/51211<br>
* http://www.guj.com.br/t/getters-e-setters/36510/2<br>
* https://pt.wikibooks.org/wiki/Java/Modificadores<br>
* https://www.devmedia.com.br/forum/uso-da-palavra-reservada-final/565425<br>
* https://www.java-made-easy.com/java-access-modifiers.html<br>
* https://www.javatpoint.com/method-overloading-in-java<br>
* https://desenvolvimentoaberto.org/2014/02/14/classes-escopos-java-c-e-c/<br>
* https://www.devmedia.com.br/trabalhando-com-metodos-em-java/25917<br>
* https://pooperrotti.wikispaces.com/Assinatura+de+métodos<br>
* http://homepages.dcc.ufmg.br/~figueiredo/disciplinas/aulas/uml-diagrama-classes-relacionamentos_v01.pdf<br>
* http://www.dsc.ufcg.edu.br/~jacques/cursos/map/html/uml/diagramas/classes/classes3.htm<br>
* http://www.linhadecodigo.com.br/artigo/943/uml-unified-modeling-language-generalizacao-agregacao-composicao-e-dependencia.aspx<br>
* https://conceitospoo.wordpress.com/2013/07/01/escopo-de-variavel/
