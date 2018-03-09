# Task Runners

**_Task Runners_**  são automatizadores de tarefas. Eles tem a capacidade de fazer muita coisa, facilitam muito o  _workflow_  de projetos seja no desenvolvimento,  _build_  ou  _deploy_.

Quem esta começando com o desenvolvimento web tem dificuldades para entender do que se trata um automatizador de tarefas, a maior parte do problema esta na inexperiência dele com projetos. Um desenvolvedor mais experiente tem uma boa noção do que seriam essas tarefas e o quanto isso pode ajuda-lo.

### Workflow

De maneira bem resumida e objetiva, um projeto web precisa passar por algumas otimizações antes de ir para produção. Otimizações como minificação de CSS, otimização de imagens, unificação e/ou ofuscação de scripts…

Tais coisas são importantes para melhorar o ranking ([SEO](http://tableless.com.br/dicas-de-seo-para-front-end/)) do site em  [motores de busca](https://pt.wikipedia.org/wiki/Motor_de_busca), entre algumas métricas a velocidade de carregamento do site conta muito, e essas ações ajudam.

Porém você não escreve CSS ou JavaScript minificado, não recebe as imagens já otimizadas… existem  [sites](https://kraken.io/)  que te podem fazer isso para você, porém imagine ter que fazer isso com mais de 50 imagens.

Também há a necessidade de usar um  [pré-processador de CSS](http://tableless.com.br/sass-vs-less-vs-stylus-batalha-dos-pre-processadores/)  como  [Sass](http://sass-lang.com/)  ou  [Less](http://lesscss.org/), ou um  [_transpiler_](https://en.wikipedia.org/wiki/Source-to-source_compiler)  de JavaScript como  [Babel](https://babeljs.io/)  ou  [CoffeeScript](http://coffeescript.org/).  
Nesse caso você vai querer que sempre que algum arquivo for salvo eles sejam transformados sem que você precise tomar alguma ação manualmente.

As possibilidades são inúmeras, é para isso que os  _Task Runners_  foram criados.

### Grunt

![](https://cdn-images-1.medium.com/max/800/1*MzHSB-cU8HFPEBuXTbPV6A.png)

[Grunt](http://gruntjs.com/)  foi o primeiro  _task runner_  a ganhar tração na comunidade JavaScript.

Ele é muito simples, as tarefas são definidas em um arquivo de configuração. Essa simplicidade também pode incomodar um pouco quando você quer criar algum fluxo complexo.

A lista de  [_plugins_](http://gruntjs.com/plugins)  é gigantesca enquanto escrevo esse artigo são  **6,012**, tem  _plugin_  para quase tudo que você puder maginar.

### Gulp

![](https://cdn-images-1.medium.com/max/800/1*dCqLeREmPWn4ApHPmzdxdQ.png)

[Gulp](http://gulpjs.com/)  não é uma ferramenta nova, porém ganhou destaque nos últimos anos, passando o Grunt, porém não tem a mesma quantidade de  [_plugins_](http://gulpjs.com/plugins/)  que o Grunt, no momento são  **2760**.

Existem dois grandes diferenciais entre o Grunt e o gulp: a definição das tasks e como elas são executadas.

> O Gulp se anuncia como “_the streaming build system”_, isso porque os arquivos envolvidos nas tarefas (sources) são carregados em memória, na forma de [stream](https://nodejs.org/api/stream.html).

As tarefas são executadas de modo  _async_  e em memória, tornando ele mais  [rápido que o Grunt](http://tech.tmw.co.uk/2014/01/speedtesting-gulp-and-grunt/).

Além disso, as tarefas são definidas como código, você programa as tarefas. Isso dá um poder e flexibilidade muito grande, porém pode não ser simples para quem não esta  _acostumado a programar (?!)_.

### NPM Scripts

Eles não chegam a ser uma novidade, porém estão se tornando um padrão em muitos projetos. No lugar de arquivos de definição de  _tasks_  esta sendo adotado o simples uso de comandos no terminal, são como  _alias_ (atalhos/apelidos) para outros comandos.

[NPM Scripts](https://docs.npmjs.com/misc/scripts)  são simples e escaláveis, algumas vezes limitados, mas tem se mostrado uma solução eficiente para muitos problemas.  
Como muitas ferramentas como  [webpack](https://webpack.github.io/)  e  [browserify](http://browserify.org/)  já são acessíveis pelo terminal, NPM Scripts passou a ser uma solução simples. Até mesmo quando Grunt e Gulp estão no projeto, pois eles estabelecem um padrão simples que pode ser compartilhado e modificado sem problemas.

```sh
npm run start  
npm run dev  
npm run build  
npm run deploy
```

Você não precisa saber exatamente o que esta sendo executado por baixo dos panos, e se algum comando mudar não vai impactar o fluxo de trabalho de ninguém.

### Alternativas

Essas são as principais ferramentas quando falamos de  _task runners_, porém se tratando do ecossistema JavaScript sempre há outras opções.

[Broccoli.js](http://broccolijs.com/)  e  [Brunch.io](http://brunch.io/)  são algumas dessas opções, além de opções muito recente, que pouquíssimas pessoas usam ou já ouviram falar, como o  [flyjs](https://github.com/flyjs/fly).

Referencia - [Ecossistema JavaScript — Parte 03: Task Runners](https://blog.codecasts.com.br/ecossistema-javascript-parte-03-task-runners-5acedba9f072)