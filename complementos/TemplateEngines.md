# Template Engines


[HTML](https://pt.wikipedia.org/wiki/HTML)  é a linguagem de marcação utilizada pelos navegadores para ser construir páginas da  _web_. Pode não parecer mas escrever HTML não é sempre uma tarefa simples ou produtiva.

A falta de reaproveitamento e facilidade na manutenção podem tornar o trabalho com HTML algo bem improdutivo.  _Template Engines_  foram criadas para resolver esses problemas.

Alguns sistemas de  _templating_  apenas fornecem uma sintaxe mais agradável para o HTML, enquanto outros fornecem muitos recursos a mais, que podem ser usados de diversas formas e para inúmeros fins.

No final os sistemas de  _templating_  são alternativas para se escrever HTML de modo mais eficiente.

----------

### {{ mustache }}

[Mustache](http://mustache.github.io/)  talvez seja o sistema de  _templating_  mais antigo para JavaScript. Originalmente um  _port_  do  [CTemplate](https://github.com/OlafvdSpek/ctemplate)  para  [Ruby](https://github.com/mustache/mustache), ganhou  _ports_  para  [JavaScript](https://github.com/janl/mustache.js),  [Python](https://github.com/defunkt/pystache),  [Erlang](https://github.com/mojombo/mustache.erl),  [Lua](https://github.com/Olivine-Labs/lustache),  [PHP](https://github.com/bobthecow/mustache.php)  e várias outras linguagens.

Atualmente não há muitos projetos que usem ele, porém é visível sua influencia nas ferramentas que vieram depois dele.

### Handlebars.js

![](https://cdn-images-1.medium.com/max/800/1*bZPiDpkT44-FPCSfjutlhg.jpeg)

[Handlebars](http://handlebarsjs.com/)  também é um dos mais antigos sistema de  _templating_  feitos em JavaScript. Foi destaque por um bom tempo.

Por ser agnóstico (a maioria é) foi implementado em várias ferramentas, como  [Ember](https://guides.emberjs.com/v2.10.0/templates/handlebars-basics/)  e  [Express.js](https://github.com/ericf/express-handlebars)

Não há muito o que dizer sobre ele, é uma ferramenta sólida, porém carece de alguns recursos que já existem em outras ferramentas do gênero.

### Pug/Jade

![](https://cdn-images-1.medium.com/max/800/0*vAevCpR3F-p2T9NB.)

Atualmente  [Pug](https://pugjs.org/)  é o sistema de  _templating_  mais popular no JavaScript. Anteriormente conhecido como  [Jade](http://jadelang.net/)  mudou seu nome para  [Pug](https://github.com/pugjs/pug/issues/2184).

Simples, poderoso, versátil e popular, ele é quase uma ferramenta oficial para aplicações Node.

----------

### Sistemas de  _templating_  “embarcados”

Algumas ferramentas optam por não usar uma solução agnóstica para  _templating_  e criam suas próprias soluções.

[Angular](https://angular.io/docs/ts/latest/guide/template-syntax.html),  [Vue.js](https://vuejs.org/v2/guide/syntax.html),  [Aurelia](http://aurelia.io/hub.html#/doc/article/aurelia/templating/latest/templating-basics)  entre outros, possuem seus próprios sistemas com sintaxes e características próprias.

[Vue.js](https://vuejs.org/)  tem a particularidade de aceitar outros sistemas de  _templating_  dentro de seus  [_single-file-components_](https://vuejs.org/v2/guide/single-file-components.html) _a_ceitando até mesmo  [JSX](https://github.com/vuejs/babel-plugin-transform-vue-jsx).


Referencia - [Ecossistema JavaScript — Parte 06: Template Engines](https://blog.codecasts.com.br/ecossistema-javascript-parte-06-template-engines-b41a41178dce)