
# Entenda de uma vez por todas o que é React.JS, Angular 2, Aurelia e Vue.JS

Todas essas quatro ferramentas são baseadas em  **web-components**, então vamos do começo.

### Web Components

Em primeiro lugar,  **web-components não é uma novidade**. Mesmo antes do primeiro  [_draft_  da especificação em 2012](https://www.w3.org/TR/2012/WD-components-intro-20120522/)  já se falava e estudava tais possibilidades.

O objetivo do post é ser direto então vamos a explicação.  
É a capacidade de criar  _custom tags html_  que encapsulam  **estrutura**  (_html_),  **estilo**  (_css_) e  **comportamento**  (_javascript_). Entenda como  _trechos de html reaproveitáveis_.  
Sem entrar em detalhes técnicos, isso é algo  **oficial**, e  **padronizado pela w3c_._**

Mesmo sendo algo padronizado, não é uma tarefa simples. Existem ferramentas que tentam facilitar sua criação. E outras que usam o conceito, porém não como está na especificação, em alguns momentos aproveitando apenas o conceito e em outras usando técnicas possibilitadas pela especificação. É nesse contexto que entram  **Vue.JS**,  **React, Angular 2, Aurelia** e qualquer outra ferramenta com o propósito de criar web-components.

----------

### ReactJS

Será o primeiro a ser falado porque foi o primeiro a popularizar-se.

React é uma ferramenta somente para  **criar componentes**. Criada pela equipe do  **instagram**  (isso mesmo, antes do facebook comprar) entrou para o  _“guarda chuva”_  de projetos open-source do  [facebook](https://code.facebook.com/projects/), impulsionando mais ainda sua adoção. O  **grande “boom”**  do React é o Virtual-DOM.

#### Virtual-DOM

v-dom é uma técnica simples e complexa ao mesmo tempo. Simples no conceito e complexa na aplicação.  
Simples porque ela é apenas uma representação em  **javascript puro**(memória) do DOM “real”. Se você sabe o que é DOM, sabe que a manipulação dele não é algo “produtivo”, é extremamente lento e causa vários problemas a sua aplicação.

Então com v-dom você passa a manipular esse objeto e não o DOM de verdade. Quando o objeto v-dom é atualizado um algorítimo calcula a diferença entre o v-dom e o DOM real, alterando então pedaços de DOM.

Sempre foi de conhecimento comum que é mais produtivo você criar os elementos DOM no javascript, processar eles e “aplicar eles de uma vez” na Arvore DOM do navegador. React veio entre outras coisas e um delas é facilitar isso.

#### JSX

O herói e o vilão da história. Amado por uns, odiado por muitos (?).  
Na verdade JSX é uma  [especificação de sintaxe](https://facebook.github.io/jsx/)  para escrever javascript como se estivéssemos escrevendo XML
```js
var Hello = React.createClass({
render: function() {
return <div>Hello {this.props.name}</div>;
}
});

ReactDOM.render(
<Hello name="World" />,
document.getElementById('container')
);
```

Sem ele o código ficaria assim:
```js
var Hello = React.createClass({
  displayName: 'Hello',
  render: function() {
    return React.createElement("div", null, "Hello ", this.props.name);
  }
});

ReactDOM.render(
  React.createElement(Hello, {name: "World"}),
  document.getElementById('container')
);
```
Então o trabalho dele é ajudar. Eu sei isso, é muito estranho!

#### Afinal o que é ReactJS?

Como eu disse, coloquei ele como primeiro da lista porque é ele que é o precursor de uma nova  _tendencia_ e entendendo ele você vai entender as outras ferramentas.

Por definição React é uma  **biblioteca para criar interfaces**.  
Isso é ótimo, ele vai  _resolver_  toda aquele amontoado de código com  **jQuery**que tínhamos para manipular o DOM. Agora podemos criar coisas performáticas e reutilizáveis de verdade.  
Ele vai bem em várias situações e tipos de projetos, independente do tamanho.

Agora você vai argumentar:  _mas como eu posso criar um projeto “grande” com react se ele é só uma biblioteca?_

A resposta é:  **não pode**. Isso mesmo, React sozinho não é capaz de te ajudar a criar um projeto SPA complexo. Para isso ele possui um  [**ecossistema**](https://github.com/reactjs)  de ferramentas para te auxiliar com esse trabalho.

#### Micro Libs Javascript

Novamente, isso não é uma “_módinha_” e sim uma realidade.  
_A era da internet veio para ficar_. E com ela novas demandas, basicamente tudo precisa de uma versão web (ou apenas web), sites agora são sistemas complexos, robustos e poderosos.  
A linguagem oficial da web é o  **javascript**, se torna necessário que os projetos tenham velocidade e facilidade, tudo precisa funcionar bem e  **mudar rápido**. Acredito que a velocidade como as coisas mudam nunca foi tão grande.

Uma piada recorrente para quem trabalha com javascript é:  _Qual será o novo framework da semana?_

Com isso é muito fácil se tornar obsoleto, e se você tentar se manter atualizado de mais pode arriscar a  **qualidade do software**. Um conceito  **não novo**  que tem aparecido em destaque nos últimos anos são os micro-serviços. Coisas  **_pequenas_**  e  **especializadas**, que podem parar de funcionar ou serem trocadas com um impacto muito pequeno ou nulo na aplicação.

O mesmo vale para o javascript, quanto menor e mais especializado for o módulo que você esta usando ou criando, melhor. Trocar ele ou reutilizá-lo será uma tarefá simples,  _web-components_  também compartilham dessa filosofia.

É assim que o ecossistema ReactJS funciona, você compõe sua aplicação com outras bibliotecas especializadas.

As mais comuns são  [react-router](https://github.com/reactjs/react-router)  e  [react-redux](https://github.com/reactjs/react-redux), com apenas essa duas você já é capaz de criar uma projeto SPA complexo. Porém, o  _boilerplate_  de tais aplicações pode não ser agradável, afinal estamos falando de algo que não segue um  _“padrão oficial”_  que pode ser feito de dezenas de maneiras diferentes.  
Nesse momento o ecossistema se mostra novamente útil. A comunidade possui vários start-kits com várias implementações prontas, tornando o trabalho de criar um projeto novo algo muito simples, criando com basicamente tudo que você vai precisar. Você terá apenas o trabalho de criar seus componentes.

#### Liberdade e facilidade

Liberdade é algo lindo, porém muitos não estão prontos para ela. É necessário maturidade para saber o que fazer com sua liberdade, essa é a maior dificuldade que React ou similares que trazem ao desenvolvedor.

Verdade seja dita, eu chuto que 65% dos  _devs_  que usam essas ferramentas,  **não sabem javascript**  de verdade. Muitos estão apenas “quebrando um galho”, resolvendo demandas que simplesmente caíram no colo deles. E com isso tem muitas dificuldade em resolver problemas simples.

Outros estão acostumados de mais com  _muletas_  proporcionadas por ferramentas mais  _completas_ porém restritivas e danosas demais para seus projetos, e com sua falta de maturidade não consegue ver isso.  
Para esses eu digo:  **Corram atrás do prejuízo, a web caminha para um momento onde não se poderá mais fingir saber javascript**.

----------

A parte do React ficou bem grande, porém se faz necessário para as outras libs, que bebem diretamente dessa fonte.

----------

### Angular 2

Da água para o vinho, do fogo para água. Saindo de React temos agora o  **NG2**. Ele é o segundo da lista pelo legado que possui (um baita legado). Mas não deixe o nome dele te enganar, esta é uma ferramenta completamente diferente do seu antecessor.

#### Legado

Devemos muito ao Angular. Entre inovações e problemas sérios, angular é um  _acidente que deu certo_. Projetado para ser uma lib para criar formulários acabou se tornando o  **framework javascript mais utilizado do mundo**. Muito por seu mérito, muito por seu nome, ou melhor pelo nome por trás dele, Google.

Nem tudo eram flores, ele tinha (tem?) vários problemas. E não estava pronto para a revolução que o React e os web-components estavam trazendo. Por isso foi decidido que ele precisava ser refeito, do zero.  
Na verdade até seu nome mudou, passou de  **AngularJS**  para  **Angular**.

Seu código, filosofia e sua linguagem mudaram completamente. Esqueça tudo que você sabia sobre Angular.

### Transição

O  [anúncio](http://angularjs.blogspot.com.br/2014/03/angular-20.html)  de uma V2 em  **2014**  foi recebido com muita alegria pela comunidade. Porém de lá para cá as coisas tem se tornado  **muito confusas**.  
Passaram a existir dois sites em paralelo, a primeira proposta mudou completamente do que temos hoje (e continua mudando mesmo estando no seu  [**5º Release Candidate**](https://github.com/angular/angular/releases/tag/2.0.0-rc.5))

Foi adotado a utilização do  [TypeScript](https://www.typescriptlang.org/)  para a escrita do código fonte e dos projetos que utilizariam o framework. Mesmo que seja possível usar NG2 sem usar o TS, no momento não há  _documentação suficiente_ que mostre como fazer isso.

Além disso possui um foco muito forte no uso de  _OO “Clássico”_, algo que divide muitas opiniões. Enquanto pode parecer mais atraente para desenvolvedores back-end, devido ao uso do TS e OO, desenvolvedores que usam javascript a mais tempo  [_condenam_](https://vimeo.com/69255635)  essa prática até mesmo a  [tipagem](https://medium.com/javascript-scene/the-shocking-secret-about-static-types-514d39bf30a3).  
-  [Goodbye, Object Oriented Programming](https://medium.com/@cscalfani/goodbye-object-oriented-programming-a59cda4c0e53).  
-  [A Simple Challenge to Classical Inheritance Fans](https://medium.com/javascript-scene/a-simple-challenge-to-classical-inheritance-fans-e78c2cf5eead)  
-  [Stop Bringing Type Safety To JavaScript](https://medium.freecodecamp.com/stop-bringing-strong-typing-to-javascript-4da0666cba6e)

O depreciamento de ferramentas, sem elas nunca terem entrado em produção, um ecossistema ainda fraco, a inconsistência da documentação, exemplos e a total  _incompatibilidade_  com o que foi feito para NG1, pouco a pouco mina a confiança da comunidade.

A verdade é que não se sabe o real futuro do Angular 2, mesmo ele também sendo baseado em componentes ele se difere, e muito, das alternativas como React e Vue.js.

#### Plataforma fullstack

Não há muito o que dizer sobre o NG2 em seu estado atual, mas há coisas bem claras que posso listar aqui.

Se antes o AngularJS era um  **framework fullstack** agora ele quer ser uma  **plataforma fullstack**. Isso é algo realmente difícil de entender, porém tudo indica que ele quer operar em todas as esferas do projeto, não epenas no front-end.

Infelizmente não há muito que se possa dizer, mas é claro que ele não se vê como uma lib. Então carregará todas as “facilidades” e problemas de uma ferramenta desse porte. Mas é como eu disse, tudo ainda está muito estranho, ele não é uma lib, mas ao mesmo tempo é  _componetizado_, sendo necessário outras libs para fazer determinadas tarefas.

Por exemplo, ele não é  _“naturalmente reativo”_ (na verdade o  _2-way data-bind_foi removido) e usa outras libs como  **RxJS**  para ter coisas como, por exemplo, a  **arquitetura flux.** (_não colocarei links pois basicamente todos os exemplos disponíveis não funcionam mais devido aos breaking changes na V2.0-RC5_)

Isso é legal e estranho ao mesmo tempo. Legal por ver que ele consegue se adaptar e estranho por isso não ser algo  _oficial_.

### Promessas

Mesmo com um nome como a Google por trás dele, seu futuro está completamente incerto. Uns ainda apostam em sua  **(re)ascensão**, outros já o abandonaram completamente e muitos só observam sem saber o que fazer.

Eu pessoalmente já desisti dele, trabalhei e trabalho diariamente com Angular V1, já apostando e migrando para outras ferramentas como Vue.JS, espero sinceramente que toda essa confusão seja resolvida. É loucura pensar que um projeto que conta atualmente com  [64 pessoas no github](https://github.com/orgs/angular/people)  possa estar  **completamente sem rumo**.

----------

### Aurelia

Falando em confusão… Para quem não sabe o criador do  [Aurelia](http://aurelia.io/index.html)  é criador do  [Durandal](http://durandaljs.com/), que passou para o  [core-team do angular](http://eisenbergeffect.bluespire.com/angular-and-durandal-converge/), afim de alavancar o projeto, porém depois de algum tempo ele  [saiu do projeto](http://eisenbergeffect.bluespire.com/leaving-angular/)  e criou o Aurelia.

Como eu disse antes, todo esse processo do NG2 está sendo bem conturbado. E sendo o Aurelia um filho bastardo do Angular ele é nossa terceira ferramenta da lista.

#### Framework progressivo

A proposta do Aurelia é no mínimo inovadora de tão simples: Tornar sua aplicação o mais “pura” possível com o passar do tempo.

Quem trabalha com javascript já esta acostumado com uma  _baita_  sopa de palavras: Babel, webpack, browserify, npm, ES6, ES7, ES-NEXT…

Tudo de mais novo e moderno no que diz respeito as especificações Ecma você encontrará no Aurelia, isso obviamente implica no uso de  _transpiladores de código._ Porém por se tratar da especificação Ecma inevitavelmente se tornará suportada pelos navegadores, eliminando ou diminuindo a necessidade dessas ferramentas.

Ele foca nas especificações W3C, então mais uma vez ferramentas de suporte podem ser removidas gradativamente, assim no lugar de ficar defasado ele seria a ferramenta mais atualizada do mercado.  
Isso tem seu preço, já que muita coisa será “nativa”, sendo mais complexo do que muitos gostariam.

Fora isso ele tem suporte ES2015, TypeScript e ESNext, e com uma doc bem completa.

#### Aurelia Snow

Como eu disse, ele possui fortes influências do Angular. Boas influências, o que torna ele uma escolha produtiva para as pessoas que ainda preferem o  _angular way_  sem toda essa confusão que está sendo o NG2.  
Com sua documentação bem completa ele vai fazer você esquecer facilmente todos os problemas que as documentações angular possuem.

Recentemente saiu sua  [versão 1](http://blog.durandal.io/2016/07/27/aurelia-1-0-is-here/)  então ele é uma opção completamente viável para projetos  _não pessoais_.

----------

### Vue.JS

Vue.JS está por último por ser a  _sensação do verão_. Brincadeiras a parte, Vue é a ferramenta que tem mostrado grande potencial, conquistando todos que a testaram. Vem criando uma comunidade bem  [dedicada no Brasil](http://www.vuejs-brasil.com.br/)  e no  [mundo](https://vuejsfeed.com/).

#### Biblioteca para criar componentes

Vue e React possuem  **muitas** semelhanças, a principal é o foco, ambas são para criar  _web-components_, sendo assim Vue é leve, objetivo e componetizado.

Sendo uma  _lib_  ele não faz todo o trabalho  _sozinho_  e, assim como React, possui um ecossistema que te ajuda a construir vários tipos de projetos.  
Há o  [vue-router](https://github.com/vuejs/vue-router)  e  [vuex](https://github.com/vuejs/vuex), ferramentas indispensáveis na criação de projetos SPA.

#### Vue.JS != React

Eles podem ter muitas semelhanças, porém possuem muitas diferenças também. A sintaxe de um componente React é extremamente livre e pura, podendo ser confusa para muito desenvolvedores. Isso não é algo ruim, porém essa liberdade pode gerar conflitos em equipes e elevar a curva de aprendizado dele.

Vue.JS também é extremamente livre, porém ele possui um estilo de desenvolvimento mais intuitivo e organizado. É muito fácil ler um código feito com ele, os componentes são criados com objetos de configuração, sendo fácil identificar o que são eventos, ações, propriedades…

Outra grande diferença é como o “html” do componente é feito. Vue.JS pode ser escrito 100% em javascript puro, porém ele disponibiliza ferramentas que ampliam e melhoram o seu  _workflow_. Ele possui um recurso chamado  [**Single File Components**](http://vuejs.org/guide/application.html#Single-File-Components).

![](https://cdn-images-1.medium.com/max/800/1*5sl767kW5FuMTv6_iO9tHQ.png)

my-component.vue

Além disso, a template é escrita em  _html,_ sendo simples a sua adaptação para desenvolvedores novos.

#### Vue e V-DOM

Vue.JS está em franca evolução e  [adoção](http://www.vuejs-brasil.com.br/como-e-a-popularidade-do-vue-js-no-mercado/). A partir da versão 2 ele passa a ter suporte a Virtual-DOM assim como o React, e com isso passa a ser  [2x a 4x mais rápido que a versão 1](https://vuejs.org/2016/04/27/announcing-2.0/).

Para os que estão preocupados (ou traumatizados) com  _major versions_ dessas ferramentas, fique tranquilo pois Vue v2 terá uma das migrações mais suaves já relatadas, quase tudo da sintaxe de  _template_  foi mantido, e tudo está muito bem documentado e listado  [aqui](http://www.vuejs-brasil.com.br/vue-js-2-o-que-mudou/)  e  [aqui](https://github.com/vuejs/vue/issues/2873).  
E com a  [nova documentação](http://rc.vuejs.org/)  que está sendo feita, tudo indica que o potencial do Vue está apenas no começo.

Vue vai manter a maneira como você escreve suas  _templates_, além de disponibilizar mais duas maneiras de escrever elas, com  **javascript puro**  ou  **JSX**. Isso mesmo, Vue tem suporte a JSX e o melhor de tudo:  **opcional**.

#### Vue.JS e a comunidade

Como dito antes Vue é um concorrente  _recente_. Apesar do projeto já existir a alguns anos, sua  [versão 1](https://github.com/vuejs/vue/releases/tag/1.0.0)  saiu em Outubro de 2015, e é diferente das outras ferramentas, não possui uma grande empresa apoiando ele.

Porém, ele possui algo  _mais forte_  que uma empresa, possui uma comunidade. Em março de 2016  [Evan You](https://twitter.com/youyuxi), criador do Vue.JS, criou uma campanha no  [Patreon](https://www.patreon.com/evanyou). O objetivo era ficar  _fulltime_  no projeto. E com isso ele passou a arrecadar  **\+ de 8 mil dólares**  mensalmente para se manter e focar exclusivamente no projeto.

![](https://cdn-images-1.medium.com/max/800/1*ykeoWuSrQRkvXhv4lCxbeQ.png)

Pessoalmente acredito muito no potencial do Vue.JS, pois ele é uma ferramenta projetada para desenvolvedores por desenvolvedores.

Ele não veio para reinventar a roda, ele inova em pegar todos os bons conceitos que já possuímos e consolidá-los em uma  _lib_  de fácil acesso à todos os níveis de  _devs_. Na comunidade  [**vuejs-brasil**](http://slack.vuejs-brasil.com.br/)  costumamos dizer que  _as pessoas tem mais dúvidas sobre javascript do que sobre Vue.JS._

----------

### F.A.Q.

#### O que é Flux, Redux e Vuex?

Redux e Vuex são implementações do Flux. Flux é um modelo de arquitetura para aplicações  _component-based_. Em aplicações desse tipo é muito fácil cair em algo chamado  **event-hell**, esse modelo visa resolver isso.  
Não possui nenhuma ligação com back-end.

#### TypeScript

TypeScript ou TS é um  _superset_  do javascript. Ele estende a linguagem adicionando novas funcionalidade a ela. Entre eles o suporte a  **_tipos_**.

#### Router

Aplicações SPA precisam de uma maneira de “trocar de página” chamamos isso de rotas, e o Router é o responsável por isso. Em aplicações component-based as rotas são ligadas a componentes.  
Não possui nenhuma ligação com sistemas de rotas do back-end.

#### ES6 e/ou ES2015. O que é EcmaScript?

EcmaScript pode ser considerado o nome oficial do Javascript. São as especificações Ecma que definem como o javascript deve funcionar em sua sintaxe e funcionalidades.  
ES6 era o nome dado a nova versão do EcmaScript, porém com releases anuais o nome correto passou a ser ES2015.


Referencia - [Entenda de uma vez por todas o que é React.JS, Angular 2, Aurelia e Vue.JS](https://medium.com/by-vinicius-reis/o-que-e-react-ng2-auleria-vue-e34b0c77b5a1)