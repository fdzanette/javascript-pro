# # Package Managers
Plugins, pacotes, módulos… Dificilmente criamos um projeto sem usar algum código de terceiro. Gerenciar e organizar esse código é trabalho do  **Package Manager (Gerenciador de Pacotes)**  ou Gerenciador de Dependências.

É comum cada linguagem ter seu próprio  _gerenciador_, as vezes existem mais de um, este é o caso do JavaScript.  
Como vimos no post anterior sobre  [plataformas](https://blog.codecasts.com.br/ecossistema-javascript-parte-01-plataformas-7a611608b58)  o JavaScript possui duas principais plataformas, o Node.js e os Navegadores. Para as dependências do Node.js usamos o  [NPM (Node Package Manager)](https://www.npmjs.com/)  e para os navegadores usamos (ou usávamos) o  [Bower](https://bower.io/).

### Módulos

Oficialmente o JavaScript não tinha uma especificação para módulos, por isso o Node.js implementa o  [CommonJS](http://www.commonjs.org/)  como  _especificação_  para seus módulos.

Só  [recentemente](http://www.2ality.com/2014/09/es6-modules-final.html)  o  [ES Modules](https://tc39.github.io/ecma262/#sec-modules)  passou a ser uma especificação o  [TC39](https://github.com/tc39).

Com a versão ES2015 do JavaScript o Node.js (através da v8) passou a suportar aos poucos as novas features do JavaScript, chegando a  [99% de compatibilidade](http://node.green/)  na versão 6.8.1+

Atualmente sintaxe de módulos do ES2015 é suportada pelo babel, porém o que ele faz é uma “tradução” para CommonJS/AMD. Ainda existem coisas que precisam ser  [ajustadas](https://github.com/tc39/proposal-dynamic-import)  para que o  [Node.js](https://nodesource.com/blog/es-modules-and-node-js-hard-choices/) e os  [navegadores](https://blog.whatwg.org/js-modules)  passem a suportar ES Modules .

Para entender um pouco mais sobre módulos:

-   [Trabalhando com serviços no JavaScript](https://medium.com/by-vinicius-reis/trabalhando-com-servicos-no-javascript-864310cf386c)
-   [Node.js — #2 — Sistema de Módulos — Rodrigo Branas](https://youtu.be/SrVDq1824E4)

### NPM

![](https://cdn-images-1.medium.com/max/800/1*DVki0FvyhmyFCkcPPuhMCw.png)

NPM é o gerenciador de pacotes padrão do Node.js, porém hoje ele é aceito como o padrão para o JavaScript.

NPM é utilizado para diversas coisas. Com a popularização do  [browserify](http://browserify.org/)  e  [webpack](https://webpack.github.io/)  ele passou a ser utilizado também para dependências  _front-end_  não se limitando a dependências de projetos Node.JS

> Não é raro ver projetos PHP, Python, Ruby… com um  _package.json_ em algum local do projeto.

Simples de instalar e usar ele é uma ferramenta extremamente útil, porém tem seus problemas. A evolução dele, por motivos de compatibilidade, é um pouco lenta. Além disso, ele pode ser um pouco demorado pois mesmo que ele seja eficiente no seu trabalho, ele não faz isso da maneira mais inteligente possível.

#### Obrigatório

Atualmente NPM é algo obrigatório para projetos web. Seja lá qual for o projeto, se ele é web e você deseja incluir um  _workflow_  moderno nele usando coisas como  [gulp](http://gulpjs.com/),  [grunt](http://gruntjs.com/),  [webpack](https://webpack.github.io/),  [stylus](http://stylus-lang.com/)… Você precisa usar ele.

Ele não é complicado, algumas dicas simples já te permite fazer bom uso dele.

### Bower

![](https://cdn-images-1.medium.com/max/800/1*8i7UYjwKHjHJc-1uHwukvQ.png)

[Bower](https://bower.io/)  é um gerenciador de pacotes para front-end.  
Chega a ser mais simples que o NPM, seu objetivo é organizar dependências para projetos front-end, ele faz um bom trabalho em sua simplicidade.

Porém, devido a natureza do ambiente ele não usa uma especificação como o  _CommonJS_. Ele gerencia pacotes de JavaScript, Imagens, CSS, Fontes…

Lembra do processo de baixar um pacote e colar ele em uma pasta do projeto? É isso que o bower faz, de maneira automática e recursiva.  
Diferente do NPM ele não permite  [dependências duplicadas](https://docs.npmjs.com/how-npm-works/npm3-dupe)  no projeto.

O fluxo dele é instalar as dependências e você  _lincar_  elas no documento HTML.

Essa simplicidade tem perdido um pouco de espaço para o NPM, pois ferramentas de  _bundler_  como o  _webpack_  e  _browserify_  usam os pacotes NPM como referencia, sendo incompatíveis com o Bower.

**Ele depende do NPM para ser instalado.**

### Yarn

![](https://cdn-images-1.medium.com/max/800/1*7OzNeoQDL3kgFUjvBVqTug.jpeg)

[Yarn](https://yarnpkg.com/)  é a  [mais nova opção](https://medium.com/yarn-a-evolu%C3%A7%C3%A3o-do-npm/yarn-a-evolu%C3%A7%C3%A3o-do-npm-e2a8fd8bf75c)  em  _package managers_, idealizado pelo  [Facebook](https://code.facebook.com/posts/1840075619545360).

Ele vem como alternativa ao NPM, sendo mais **rápido e inteligente**  que o NPM. Ele é compatível com projetos que usam NPM, isso significa que na maioria das vezes você pode trocar o NPM por ele sem problemas.

Apesar de ser compatível, ele tem alguns  [bugs](https://github.com/yarnpkg/yarn/issues?q=is%3Aissue+is%3Aopen+label%3Abug), eles são isolados e até mesmo raros, porém podem trazer alguma dor de cabeça.

Ele usa os registros de pacotes do próprio NPM para resolver as dependências, com isso mesmo que você opte por usar ele o NPM não é 100% descartado, você em algum momento ainda vai precisar dele.

Muitos desenvolvedores já estão usando ele no lugar do NPM, pois é muito fácil começar a usar ele. Seus comandos, apesar de lembrarem os do NPM, são mais intuitivos e óbvios, ele possui um potencial imenso.

Referência [Ecossistema JavaScript — Parte 02: Package Managers](https://blog.codecasts.com.br/ecossistema-javascript-parte-02-package-manager-68fd19a1fad3) 