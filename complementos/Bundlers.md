# Bundlers (Builders)

Demandas mais complexas, projetos mais complexos. JavaScript há muito tempo deixou de ser considerado uma [toy-language](http://pt.slideshare.net/kmstechnology/javascript-no-longer-a-toy-language-60109230), hoje é a linguagem de programação  [mais popular do Github](https://octoverse.github.com/).

Usar módulos no JavaScript se tornou algo de extrema importância. Soluções como  [_RequireJS_](http://requirejs.org/)  foram criadas para facilitar a escrita de um código modular com JavaScript.

Com a popularização do  [Node](https://blog.codecasts.com.br/ecossistema-javascript-parte-01-plataformas-7a611608b58)  e do  [NPM](https://blog.codecasts.com.br/ecossistema-javascript-parte-02-package-manager-68fd19a1fad3)  a solução proposta pelo  _RequireJS_passou a ser menos  _amigável_. Surgem então ferramentas para trazer a comodidade dos módulos NPM para códigos que são executados nos navegadores.


### Require no navegador

Em resumo, um  _bundler_  é uma ferramenta que permite que a função require funcione no navegador. Assim você carregaria um módulo da mesma forma que um código para Node.

Para tornar isso possível o  _bundler_  faz uma análise no código, gerando um novo arquivo, com todas as dependências necessárias para ele funcionar.
```js
const **_** = **require**('lodash')  
const numbers = \[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12\]  
const lists = **_**.chunk(numbers, 3)   
// \[\[1, 2, 3\], \[4, 5, 6\], \[7, 8, 9\], \[10, 11, 12\]\]

lists.map(list => list.reduce((acc, value) => acc * value, 1))  
// \[6, 120, 504, 1320\]
```

Este é um exemplo de código bem bobo, na primeira linha a variável  **___**  é criada a partir do resultado de  **_require(‘lodash’)_**.

[Lodash](https://lodash.com/)  é um módulo instalado via  [NPM](https://www.npmjs.com/)  no projeto, ao executar este código no Node ele vai funcionar perfeitamente, porém isso não vai acontecer no navegador. O navegador não possui a função  _require_  e nem saberia onde “pegar” o módulo.

Um  _bundler/builder_  vai pegar o arquivo (_entry point_) desse código e vai gerar um novo arquivo (_artefato_), ele faz isso de forma recursiva, resolvendo as dependências das dependências.  
O arquivo final vai conter o código original, somado ao código das dependências. Este arquivo pode ser executado no navegador sem nenhum problema.

> Durante o processo de  _builder_  o código pode passar por várias transformações, como  [Babel](https://babeljs.io/),  [CoffeeScript](http://coffeescript.org/),  [TypeScript](https://www.typescriptlang.org/),  [Flow](https://flowtype.org/), etc.

----------

### Browserify

![](https://cdn-images-1.medium.com/max/800/1*lTG9HcDDN5HqzAUEaaPE2g.png)

[Browserify](http://browserify.org/)  foi uma das primeiras ferramentas a fazer este tipo de trabalho.  
No site dele há a seguinte frase:

> Browserify lets you require(‘modules’) in the browser by bundling up all of your dependencies.

É exatamente isso que ele se propõe a fazer, tornar o  _require_  funcional no navegador. Extremamente simples ele pode ser usado sozinho ou em conjunto com  [Gulp](https://github.com/gulpjs/gulp/blob/v3.9.1/docs/recipes/browserify-uglify-sourcemap.md)/[Grunt](https://github.com/jmreidy/grunt-browserify).

Para projetos sem muitas dependências ou desenvolvedores que estão começando com Gulp/Grunt ele é uma excelente opção, se ajusta facilmente ao seu fluxo de trabalho.

Durante o processo de  _building_  você pode aplicar transformações como o  [babelify](https://github.com/babel/babelify)  ou  [vueify](https://github.com/vuejs/vueify).

### webpack

![](https://cdn-images-1.medium.com/max/800/1*exBOygnWZfP7yRGhA5mOsQ.png)

[Webpack](https://webpack.js.org/)  é bem mais que um  _bundler_  para arquivos JavaScript, com seu sistema de  [_loaders_](https://webpack.js.org/concepts/loaders/)  ele é capaz de gerar  _bundlers_  de (basicamente) qualquer tipo de  _asset_, sejam  [imagens](https://github.com/tcoopman/image-webpack-loader),  [css](https://github.com/webpack/css-loader),  [html](https://github.com/webpack/html-loader),  [sass](https://github.com/jtangelder/sass-loader),  [less](https://github.com/webpack/less-loader)… Essa característica fez muitas pessoas deixarem de usar  _grunt_  e  _gulp_  para usar somente o  _webpack_.

Ele é bem mais poderoso que o  _Browserify_, ao mesmo tempo que pode assustar os mais  _novatos_.

Em sua versão  [1.x](http://webpack.github.io/docs/)  ele sempre foi conhecido por possuir uma documentação bem ruim, sem muitas explicações ou exemplos práticos. Porém agora em sua versão 2.0 isso mudou radicalmente. Com uma nova documentação mais agradável e eficiente ficou bem simples de entender e usar ele.

É difícil dizer em tipo de projeto  _webpack_  é recomendado, mesmo assim ele tem se tornado um padrão em várias ferramentas, como  [React](https://github.com/facebookincubator/create-react-app)  e  [Vue.js](https://github.com/vuejs-templates/webpack).

Entre as muitas possibilidades que ele fornece, é possível gerar  _bundlers_  mais eficientes, usando  [arquivos separados (spliting)](https://webpack.js.org/guides/code-splitting/)  e  [carregamento-preguiçoso (lazy-loading)](http://router.vuejs.org/en/advanced/lazy-loading.html).

### rollup.js

![](https://cdn-images-1.medium.com/max/800/1*1VP-QyiZ0zCIb9IULGLZOw.png)

[rollup.js](http://rollupjs.org/)  é a ferramenta mais nova da lista, em seu site esta escrito:

> the next-generation JavaScript module bundler

Isso porque ele vem preparado com uma nova técnica de  _bundler_  para arquivos JavaScript:  [**_Tree-shaking_**](https://blog.engineyard.com/2016/tree-shaking)

Mesmo ele sendo um,  _novato_  muitas ferramentas ([Vue](https://github.com/vuejs/vue/blob/v2.1.4/package.json#L103-L109)/[Angular](https://github.com/angular/angular/blob/2.3.0/package.json#L73-L74)) e projetos já estão usando ele. Sua simplicidade lembra muito o  [_Browserify_](http://browserify.org/).

Assim como  _browserify_  e  _webpack_  ele permite transformações no código antes de gerar o artefato final, é muito comum ver ele sendo usado em conjunto com o  [buble](https://buble.surge.sh/)  (uma alternativa ao Babel).

#### Tree-shaking

Normalmente algumas porções de código inúteis vão para o artefato final. Isso por que você pode não ter usado todas as funções de um determinado módulo.

A especificação de módulos JavaScript  [_CommonJS_](http://www.commonjs.org/)  não é capaz de lidar com isso, o JavaScript não era capaz de lidar com isso. Porém com a chegada do  [**ES Modules**](http://exploringjs.com/es6/ch_modules.html)  é possível importar apenas uma parte do módulo.

Vejamos nosso exemplo anterior usando  _ES Modules_:

```js
**import { chunk } from 'lodash'**  
const numbers = \[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12\]  
const lists = **chunk**(numbers, 3)   
// \[\[1, 2, 3\], \[4, 5, 6\], \[7, 8, 9\], \[10, 11, 12\]\]

lists.map(list => list.reduce((acc, value) => acc * value, 1))  
// \[6, 120, 504, 1320\]
```

Com uma pequena mudança nosso código agora diz que precisa apenas de  **_chunk_**  do módulo  [**_lodash_**](https://lodash.com/).

Antes para se obter só uma “porção” do módulo, eram criado módulo específicos para essas porções, como o próprio  [_lodash_](https://www.npmjs.com/package/lodash.chunk)  faz:

```js
**const chunk = require('lodash.chunk')**  
const numbers = \[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12\]  
const lists = chunk(numbers, 3)   
// \[\[1, 2, 3\], \[4, 5, 6\], \[7, 8, 9\], \[10, 11, 12\]\]

lists.map(list => list.reduce((acc, value) => acc * value, 1))  
// \[6, 120, 504, 1320\]
```

Porém é necessário que o  _bundler_  tenha suporte a essa técnica, o  _rollup.js_  é projetado sobre essa premissa, enquanto somente o  [_webpack2_](http://www.2ality.com/2015/12/webpack-tree-shaking.html)  tem esse suporte.

----------

### Bundlers são realmente necessários?

Existe uma discussão sobre a necessidade de ferramentas do gênero, afinal algumas ferramentas como o  _webpack_  não só  _empacotam_  como  **isolam**  o código JavaScript, isso pode ser inconveniente em alguns momentos.

#### Complexo

Também pode parecer muito mágico o que essas ferramentas fazem, mas a grosso modo não é. Elas fazem uma  **_analise de texto_**  e processam coisas a partir dessa analise. Trata-se apenas de um  _parse_.

Há também alguns bits extras para que a coisa toda funcione no navegador.

#### Modular

É importante parar um momento e refletir sobre isso tudo. O ecossistema JavaScript é modular, ferramentas dependem umas das outras. Elas são projetadas para serem plugáveis e escaláveis.  
Basta ver como Browserify e Webpack fazem a transformação de  _ES2015_  para  _ES5_.

Todas elas usam o Babel, oque fazem é criar uma “casca” sobre o Babel para que ele funcione nas devidas ferramentas. É assim que o ecossistema JavaScript evolui.

#### Conclusão

Não existe uma resposta clara sobre a necessidade ou não de  _bundlers_, porém uma coisa é certa: Eles ajudam muito o trabalho de desenvolvimento de software.

> Comece devagar, você não precisa conhecer ou usar todos eles, em geral use o que sua ferramenta recomenda, provavelmente há um motivo para essas escolhas.


Referencia: [Ecossistema JavaScript — Parte 05: Bundlers (Builders)](https://blog.codecasts.com.br/ecossistema-javascript-parte-05-bundlers-builders-6809b17ddcf8)