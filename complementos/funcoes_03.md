
# Javascript - o método call() e apply()

Todas as funções do  **javascript**  possuem alguns métodos como toString(), call() e apply(). Antes de explicar o método function.call() vou exemplificar o funcionamento das funções e escopos, que acredito que isso facilite o entendimento.

Exemplo de código:

    var url = 'andafter.org';  
    function f(){  
    console.log(this);  
    console.log(this.url);  
    }  
    f();

Nesse código eu seto uma variável global url, e quando chamo a função f dou um log em "this" (é a window), então quando chamo this.url o retorno é a variável instanciada fora da função.

## O método call()

O método function.call() permite você dizer em qual escopo (essa é a nomenclatura certa? comentem suas opiniões) uma função deve ser executada.

Voltando ao exemplo de código anterior:

var url = 'andafter.org';  
var site = { url : 'odesenvolvedor.com.br' };  
function f(){  
console.log(this.url);  
}  
f.call(site);

O function.call() define o que será o "this" dentro da função, e este deve ser passado como parâmetro para o método call.

## Método call com parâmetros

No exemplo anterior não fizemos uso de parâmetros, apenas do "this". Mas o método call pode receber a partir do segundo parâmeto (o primeiro sempre será o escopo que será atribuído ao this) os parâmetros que serão passados para a função.

    var url = 'andafter.org';  
    var site = { url : 'odesenvolvedor.com.br' };  
    function f(p1, p2){  
    console.log(this.url + ' - ' + p1 + ' - ' + p2);  
    }  
    f('aprendendo javascript', 'no andafter!');  
    f.call(site, 'estudando códigos', 'no desenvolvedor');

## O método function.apply()

O método function.apply() tem o mesmo funcionamento do function.call() com uma diferença na forma dos parâmetros, o segundo parâmetro sempre deverá ser um array, contendo todos os parâmetros que serão enviados para a função.

O primeiro parâmetro continua sendo o escopo onde sua função será executada.

    var url = 'andafter.org';  
    var site = { url : 'odesenvolvedor.com.br' };  
    function f(p1, p2){  
    console.log(this.url + ' - ' + p1 + ' ' + p2);  
    }  
    f('aprendendo javascript', 'no andafter!');  
    f.apply(site, ['estudando códigos', 'no desenvolvedor']);`

Agora você já sabe como definir em qual escopo uma função será executada, e também tem um facilitador para funções que chamam funções.