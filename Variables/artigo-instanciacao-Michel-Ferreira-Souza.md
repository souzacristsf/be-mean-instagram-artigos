# Artigo - Instancia��o
**Autor**: [Michel Ferreira Souza] (https://github.com/souzacristsf)
**Data**: 22/12/2015

## Hoisting
Hoisting � o procedimento do JavaScript que move declara��es para o topo de seus escopos atuais. 

**exemplo 1**
```
var texto = 'Ol�';
function initBoasVindas(){
    console.log(texto);
    var texto = 'Ol� WebSchool';
}
initBoasVindas();
//undefined

```
Ent�o, isso significa quem mesmo que sua declara��o esteja no meio do codigo e todas as variaveis declaradas com o termo var, 
ganhar� o valor de undefined e as fun��es t�m o seu conteudo compilado. Ap�s cada linha ser analisada, entramos em RunTime, todas as 
linhas s�o executadas, incluindo as atribui��es.

Explicando o **exemplo 1**, anterior:

Compile Time
Come�ando o Compile Time e finalizando o c�digo virtualmente fica dessa forma:

```
// var texto; (escopo global)
function initBoasVindas(){
    // var texto; (escopo local)
   3� console.log(texto);
   4� texto = 'Ol� WebSchool';
}
1� texto = 'Ol�';
2� initBoasVindas();
```

Depois do processo do Compile Time � iniciado o modo de execu��o RunTime, pulando as declara��es o processo executa os passos 
conforme a ordem, 1�, 2�, 3�, 4� no exemplo acima, e � claro respeitando o seu escopo.

## Closure

Closure ocorre quando uma fun��o interior referencias variaveis locais da fun�o exterio, ou seja, uma fun��o dentro da outra.
Sendo assim, closure tem acesso as vari�veis do proprio escopo, fun��o exterior e variaveis globais.

**exemplo 2**

```
function monstrarNome(primeiroNome, segundoNome) { 

var msgBoasVindas= "Seja bem vindo ";

//esta fun��o tem acesso as vari�veis da fun��o exterior e tamb�m acesso aos par�metros
function juntaMsgNome() {
    return msgBoasVindas + primeiroNome + " " + segundoNome + "!!!";
}

	return juntaMsgNome();
}

monstrarNome("Michel", "Souza"); 
//Seja bem vindo Michel Souza!!!

```

## Vari�vel Global

Vari�vel Global s�o variaveis definidas fora do escopo de uma fun��o, podendo ser modificada em qualquer parte do programa.

**exemplo 3**

### Vari�vel global

```
var a, b, c;

function val(){
//variavel escopo local da fun��o 
   var a, b, c;
}

``` 


**exemplo 4**
vari�vel global

```
var a = 4;
console.log(a); // 4

function val(){
//variavel escopo local da fun��o 
   console.log(a); // 4
//setando um novo valor a variavel global a	
   a = 5;
   console.log(a); // 5
}
val();
console.log(a); // 5

```

## Vari�vel por par�metro

Vari�vel por par�metro, quando passado para um fun��o ela ser� utilizada somente dentro da fun��o, podendo ser alterada a mesma. 
Nesse caso chamado de escopo local.

**exemplo 5**

```
function meuNome(nome){
	console.log(nome);
	nome = "Mudei o nome";
	console.log(nome);
}

meuNome("Passei o nome");

```

## Instancia��o usando uma IIFE

IIFE (Immediately Invoked Function Expression - Fun��o An�nima Auto Execut�vel)
s�o fun��es que nascem, executam e morrem sem deixar muitos rastros para o escopo global. 
Elas basicamente n�o s�o diferentes das fun��es convencionais, com o diferencial de serem executadas imediatamente ap�s serem lidas pelo interpretador.



Sintaxe de uma IIFE:

```
   (function(){
    ...
   })();
```

**Encapsulamento!** - Fiquem ligados que variaveis em javascript t�m como escopo a fun��o pela qual elas foram definidas  (podem ser acessadas somente dentro da fun��o, jamais fora).

**exemplo 5**
```

var adder = (function() 
{
 var myPhrase = "";
 return function(x) 
 { 
  return myPhrase = 
  !!myPhrase ? myPhrase.concat(" ", x) : myPhrase.concat(x);
 }
})();

adder("Ol�"); // "Ol�"
adder("Mundo!"); // "Ol� Mundo!"

myPhrase; // myPhrase is not defined
```


## Refer�ncias

1. [Sobre fun��es imediatas JavaScript (IIFE)](http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/) - Acesso em 22 de Novembro de 2015;<br/>
2. [Padroniza��o com IIFE](http://www.devmedia.com.br/padronizacao-com-iife-amd-e-requirejs/31031) - Acesso em 22 de Novembro de 2015;<br/>
3. [Escopo vari�vel (JavaScript)](https://msdn.microsoft.com/pt-br/library/bzt2dkta(v=vs.94).aspx) - Acesso em 22 de Novembro de 2015;<br/>
4. [Closure (computer programming)](https://en.wikipedia.org/wiki/Closure_(computer_programming) - Acesso em 22 de Novembro de 2015;<br/>
5. [Closure em Javascript](https://javiani.wordpress.com/2009/11/07/closure-em-javascript/) - Acesso em 22 de Novembro de 2015;<br/>
6. [JSHint](http://jshint.com/) - Acesso em 22 de Novembro de 2015;<br/>
7. [Entendendo escopo e hoisting no JavaScript](https://www.hugobessa.com.br/posts/entendendo-escopo-e-hoisting-no-javascript/) - Acesso em 22 de Novembro de 2015;<br/>
8. [JS Funcional] (https://github.com/Webschool-io/workshop-js-funcional-free#IIFE) - Acesso em 22 de Novembro de 2015;<br/>

