# Artigo - Instanciação
**Autor**: [Michel Ferreira Souza] (https://github.com/souzacristsf)
**Data**: 22/12/2015

## Hoisting
Hoisting é o procedimento do JavaScript que move declarações para o topo de seus escopos atuais. 

**exemplo 1**
```
var texto = 'Olá';
function initBoasVindas(){
    console.log(texto);
    var texto = 'Olá WebSchool';
}
initBoasVindas();
//undefined

```
Então, isso significa quem mesmo que sua declaração esteja no meio do codigo e todas as variaveis declaradas com o termo var, 
ganhará o valor de undefined e as funções têm o seu conteudo compilado. Após cada linha ser analisada, entramos em RunTime, todas as 
linhas são executadas, incluindo as atribuições.

Explicando o **exemplo 1**, anterior:

Compile Time
Começando o Compile Time e finalizando o código virtualmente fica dessa forma:

```
// var texto; (escopo global)
function initBoasVindas(){
    // var texto; (escopo local)
   3° console.log(texto);
   4° texto = 'Olá WebSchool';
}
1° texto = 'Olá';
2° initBoasVindas();
```

Depois do processo do Compile Time é iniciado o modo de execução RunTime, pulando as declarações o processo executa os passos 
conforme a ordem, 1°, 2°, 3°, 4° no exemplo acima, e é claro respeitando o seu escopo.

## Closure

Closure ocorre quando uma função interior referencias variaveis locais da funão exterio, ou seja, uma função dentro da outra.
Sendo assim, closure tem acesso as variáveis do proprio escopo, função exterior e variaveis globais.

**exemplo 2**

```
function monstrarNome(primeiroNome, segundoNome) { 

var msgBoasVindas= "Seja bem vindo ";

//esta função tem acesso as variáveis da função exterior e também acesso aos parâmetros
function juntaMsgNome() {
    return msgBoasVindas + primeiroNome + " " + segundoNome + "!!!";
}

	return juntaMsgNome();
}

monstrarNome("Michel", "Souza"); 
//Seja bem vindo Michel Souza!!!

```

## Variável Global

Variável Global são variaveis definidas fora do escopo de uma função, podendo ser modificada em qualquer parte do programa.

**exemplo 3**

### Variável global

```
var a, b, c;

function val(){
//variavel escopo local da função 
   var a, b, c;
}

``` 


**exemplo 4**
variável global

```
var a = 4;
console.log(a); // 4

function val(){
//variavel escopo local da função 
   console.log(a); // 4
//setando um novo valor a variavel global a	
   a = 5;
   console.log(a); // 5
}
val();
console.log(a); // 5

```

## Variável por parâmetro

Variável por parâmetro, quando passado para um função ela será utilizada somente dentro da função, podendo ser alterada a mesma. 
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

## Instanciação usando uma IIFE

IIFE (Immediately Invoked Function Expression - Função Anônima Auto Executável)
são funções que nascem, executam e morrem sem deixar muitos rastros para o escopo global. 
Elas basicamente não são diferentes das funções convencionais, com o diferencial de serem executadas imediatamente após serem lidas pelo interpretador.



Sintaxe de uma IIFE:

```
   (function(){
    ...
   })();
```

**Encapsulamento!** - Fiquem ligados que variaveis em javascript têm como escopo a função pela qual elas foram definidas  (podem ser acessadas somente dentro da função, jamais fora).

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

adder("Olá"); // "Olá"
adder("Mundo!"); // "Olá Mundo!"

myPhrase; // myPhrase is not defined
```


## Referências

1. [Sobre funções imediatas JavaScript (IIFE)](http://imasters.com.br/front-end/javascript/sobre-funcoes-imediatas-javascript-iife/) - Acesso em 22 de Novembro de 2015;<br/>
2. [Padronização com IIFE](http://www.devmedia.com.br/padronizacao-com-iife-amd-e-requirejs/31031) - Acesso em 22 de Novembro de 2015;<br/>
3. [Escopo variável (JavaScript)](https://msdn.microsoft.com/pt-br/library/bzt2dkta(v=vs.94).aspx) - Acesso em 22 de Novembro de 2015;<br/>
4. [Closure (computer programming)](https://en.wikipedia.org/wiki/Closure_(computer_programming) - Acesso em 22 de Novembro de 2015;<br/>
5. [Closure em Javascript](https://javiani.wordpress.com/2009/11/07/closure-em-javascript/) - Acesso em 22 de Novembro de 2015;<br/>
6. [JSHint](http://jshint.com/) - Acesso em 22 de Novembro de 2015;<br/>
7. [Entendendo escopo e hoisting no JavaScript](https://www.hugobessa.com.br/posts/entendendo-escopo-e-hoisting-no-javascript/) - Acesso em 22 de Novembro de 2015;<br/>
8. [JS Funcional] (https://github.com/Webschool-io/workshop-js-funcional-free#IIFE) - Acesso em 22 de Novembro de 2015;<br/>

