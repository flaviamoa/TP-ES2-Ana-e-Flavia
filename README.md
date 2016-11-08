# Quill
![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/quill.png)

## Sumário
1. [Resumo](#resumo)
2. [Introdução](#introdução)
3. [Rich Text](#rich-text)
4. [Funcionalidades](#funcionalidades)
5. [Projeto Arquitetural](#projeto-arquitetural)
6. [Releases](#releases)
7. [Características do Produto](#características-do-produto)
8. [Começando a Usar](#começando-a-usar)
9. [Conclusão](#conclusão)
10. [Referências](#referências)
 

## Resumo

O Quill Rich Text Editor vem sendo desenvolvido há aproximadamente dois anos com o objetivo de ser um editor de texto de fácil uso e o melhor de sua classe, de forma a se tornar o mais utilizado em aplicações web. O programa possui a sua própria API de código aberto e disponível no GitHub para avaliações e possíveis novos colaboradores. Pode-se afirmar também que ele se destina a usuários com experiência intermediária em web.

[Topo](#sumário)

## Introdução

O Quill Rich Text Editor é um editor de texto que foi construído para possuir grande compatibilidade com os sistemas operacionais mais atuais (Windows, Linux, Android, por exemplo) e com vários navegadores (Edge, Chrome, Firefox), além disso ele pode ser facilmente adaptado a inclusões e alterações de requisitos. O objetivo desse aplicativo é ser uma alternativa para os editores de texto existentes até a presente data, e que seja de livre acesso aos usuários, possuindo constante colaboração de voluntários no seu desenvolvimento. 

É possível fazer o download do Quill em vários formatos, de forma que o usuário possa  usar a aplicação prontamente, também o código fonte completo é disponibilizado para fazer o download. Para fazer o download do Quill e/ou do código fonte basta acessar [GitHub -  Quill](https://github.com/quilljs/quill) ou o website do produto [Quill Download](https://quilljs.com/docs/download/) . Uma Rede de Fornecimento de Conteúdo (CDN) está disponível e possui o suporte da Amazon CloudFront, uma outra opção é adicionar o Quill como uma dependência NPM e adicioná-lo no próprio fluxo de trabalho de compilação.

O sistema possui uma barra de ferramentas que auxilia os usuários a formatarem o texto muito similar aos editores de texto comuns, como o Word e o Open Office, apresentando as opções para estilizar a fonte, como tipo, tamanho, negrito, itálico, sublinhado, cortado, cor, cor de preenchimento, lista numerada, lista com marcadores, alinhamento do parágrafo, inserção de links e imagens externos. 

Foram utilizadas principalmente as linguagens de programação Java e JavaScript para desenvolver este aplicativo. Este sistema foi criado por  Jason Chen, membro do programa de desenvolvedores, ele possui 53 estrelas e 94 seguidores no GitHub, além de possuir 9 repositórios. Um dos principais colaboradores é o Byron Milligan que possui 54 estrelas, 7 seguidores e 3 repositórios no GitHub. Não existe uma divisão clara de tarefas, mas é certo que o Jason é o desenvolvedor que realiza mais alterações no quill, de acordo com o número de commits realizados por ele dentro de um mês, como pode ser observado na imagem logo abaixo.

![](https://github.com/AnaCarolina86/TP-ES2-Ana-e-Flavia/blob/master/commits.jpg)

  Fonte: [GitHub - Quill Contributors](https://github.com/quilljs/quill/graphs/contributors)


Desde o surgimento da Web, a criação de conteúdo tornou-se imprescindível para uma boa edição de textos, e a proposta desse sistema é trazer soluções práticas para isso. O Quill foi construído baseado em texto natural, então quando ele quer saber se algo está em negrito, ele não precisa atravessar todo o DOM, basta chamar o método getFormat(5, 1) que recupera formatação comum de texto no intervalo dado. Métodos:

```javascript 
getFormat(range: Range = current): { [String]: any }
getFormat(index: Number, length: Number = 0): { [String]: any }
```

Exemplo de uso:

```javascript 
quill.setText('Hello World!');
quill.formatText(0, 2, 'bold', true);
quill.formatText(1, 2, 'italic', true);
quill.getFormat(0, 2);   // { bold: true }
quill.getFormat(1, 1);   // { bold: true, italic: true }
```

Isso é possível porque  todas as chamadas de API do núcleo permitem índices arbitrários e comprimentos de acesso ou modificação. O evento API também relata alterações em um formato JSON intuitivo, dessa forma não há necessidade de analisar o DOM. Como o ambiente web está se tornando cada vez mais rica e interativa, os editores de textos necessitam considerar esses casos de uso. Além disso, esse sistema suporta um número ilimitado de formatos de textos, e  expõe seu próprio modelo de documento, uma abstração poderosa sobre o DOM, permitindo a ampliação e personalização da edição. Vale destacar que essa aplicação permite que funcionalidades executem da mesma maneira em diversos sistemas operacionais e navegadores.

O produto recebe ainda o suporte de grandes organizações como o LinkedIn, Gannett, reedsy, Hubspot, buffer, entre várias outras e suas principais releases, notícias e atualizações podem ser encontrados no site: [Blog - Quill](https://quilljs.com/blog/)

[Topo](#sumário)

## Rich text


O Rich Text Format (RTF), como o próprio nome sugere, é um formato de texto mais elaborado e que permite transmitir ao trabalho características mais variadas e únicas, ao contrário do Plain Text, o texto simples de arquivos de extensão .txt, que não possui nenhuma opção de formatação além da tradicional. 

A preocupação com a variedades de formatação surgiu na década de 80 por membros do time de desenvolvimento da Microsoft e, desde então, vem sofrendo melhorias no sentido de incluir cada vez mais funcionalidades aos editores de texto.

O Quill possui sua própria biblioteca de rich text, que possui três módulos básicos: o delta.js, o op.js 	e o type.js. Os “ops” são os arrays de operações e os “deltas” são objetos com chaves “ops” para um array de operações.

[Topo](#sumário)

## Funcionalidades


Esta aplicação é capaz de editar um texto de formas variadas e únicas por um usuário comum, de forma simples e bastante familiar a este. Entre as mais novas funcionalidades do Quill podemos citar: blocos editáveis podem existir em linha com o restante do texto, fórmulas em LaTex podem ser inseridas no seu conteúdo, também muitos novos formatos foram adicionados, incluindo sobrescrito, subscrito, código inline, blocos de código, cabeçalhos, blockquotes, direção de texto, vídeos e listas aninhadas, estilos inline agora também podem usar as classes.

Além dessas funcionalidades, existem as básicas de um editor de texto, como a alteração de cor, tamanho e estilo do texto, alinhamento do texto, inserção de imagens e hiperlinks,  que podem ser observadas na imagem logo abaixo.

![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/play.png)

Esta imagem mostra uma versão no sistema on line para que o usuário experimente antes de fazer o download do sistema.

[Topo](#sumário)

## Projeto arquitetural:

Como já foi mencionado anteriormente, o desenvolvimento de todo este programa está disponibilizado na plataforma GitHub, desse modo é fácil perceber como o Quill está arquiteturado. Para a organização dos módulos do sistema, é utilizado o Webpack que agrupa os módulos com dependências e gera ativos estáticos que representam estes módulos. Além disso, o Quill apresenta como principais atributos de qualidade a portabilidade, já que é capaz de executar em Linux e Windows, a usabilidade, a manutenibilidade e desempenho. Pelo requisitos deste sistema, não há grandes restrições de desempenho e disponibilidade. Devido à complexidade do sistema, não foi possível determinar o diagrama de classes do mesmo.

Ao inspecionar o código em si do Quill, logo nota-se que é utilizado o paradigma de programação Orientação a Objetos, usando a linguagem Java e JavaScript. Exemplo de código:
 
 ![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/java.png)
 
Na página inicial do Quill no GitHub, é possível observar várias pastas de módulos e instruções de como se tornar um colaborador, entre outras informações. Pode-se considerar que a divisão do programa nessas pastas já é um tipo de modularização. Percebe-se que as principais pastas de módulos do sistema são: _develop, docs, formats, modules e test. As demais pastas estão relacionadas principalmente com questões de design e handler de eventos do programa. Cada uma dessas pastas citadas contêm outras pastas e/ou arquivos de códigos que auxiliam em uma melhor modularização desse sistema. Por exemplo, a pasta _develop contém a pasta scripts e os arquivos browsers.js, proxy.js, por exemplo.

A pasta _develop armazena arquivos que promovem a compatibilidade do quill com o sistema operacional e o navegador do usuário, fazem a configuração para realizar os testes unitários, além de configurarem o servidor proxy e o sistema para organizar os arquivos (Webpack).

Já a pasta docs é o local onde o sistema é documentado, possui inclusive informações sobre o website e o guia de uso do sistema. Sempre que algo é alterado, é realizada a documentação.

A pasta formats possui os códigos de especificação dos estilos usados no editor de texto, um exemplo disso, é o arquivo bold.js que confere a característica negrito ao texto, o código pode ser observado logo abaixo:

![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/estilo.png)

Já a pasta modules possui os módulos em si do sistema, como a barra de ferramentas,  o conteiner do aplicativo, e o espaço onde o texto será escrito o texto no editor, por exemplo.

Por último, a pasta test, como o próprio nome já diz, contém os códigos para a realização de testes e explicações de como reproduzi-los na sua própria máquina, sabendo-se que  Karma  e Protractor  são usados para os testes.

Como este é um sistema relativamente grande e complexo, justifica-se o uso de uma modularização eficiente e de uma programação orientada a objetos com a finalidade de tornar este sistema mais fácil de analisar e buscar erros no código.

[Topo](#sumário)

## Releases:

Até os tempos presentes, o quill já conta com 26 versões lançadas incluindo protótipos e versões betas.

A versão `0.20.0` trouxe como principais mudanças correções relativas à usabilidade no navegador Chrome e bugs com tags, além de acrescentar funcionalidades como o gerenciador de “colar” passar a aceitar conversão customizada de funções, entre outras.

A edição seguinte, a `0.20.1`, foi uma versão pré-beta na qual foram lançados mais correções de bugs e com a integração do modelo de documento “Parchment” ao Quill. A próxima versão a esta, foi a primeira versão beta, sem mudanças significativas.

A fase beta do Quill obteve 12 versões lançadas, até que surgisse a versão rc (release candidate). Essa fase prevaleceu por um período de aproximadamente um ano e foi responsável pelo aperfeiçoamento da API de teclado e sua customização. Foram adicionados também utilidades como ferramentas de inserção de fórmulas e videos, assim como a ferramenta de imagens foi melhorada para obter melhor desempenho.

Após 5 versões rc sem muitas alterações significativas, o Quill foi oficialmente lançado e se encontra atualmente na versão `1.0.6`.
Evolução do sistema:

![](https://github.com/AnaCarolina86/TP-ES2-Ana-e-Flavia/blob/master/evolucao.jpg)

Fonte: [Code Frequency](https://github.com/quilljs/quill/graphs/code-frequency)

[Topo](#sumário)

## Características do produto

Atualmente o Quill conta com três temas básicos que podem ser utilizados pelos usuários. São eles:
### Snow
![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/snow.png)

Esse tema é para os usuários que preferem contar apenas com os itens básicos de um editor de texto.

### Bubbles

![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/bubble.png)

Já o Bubbles foi planejado para usuários exigentes que não gostam de poluição visual na hora de colocar suas idéias no “papel”. O editor fica totalmente em uma tela branca e quando é necessário alguma ferramenta de formatação, o usuário precisa selecionar a parte do texto a ser formatada, dessa forma as opções de edição tornam-se visíveis ao usuário.

### Completo

![](https://github.com/flaviamoa/TP-ES2-Ana-e-Flavia/blob/master/complete.png)

Essa versão do editor já vem com todas as funcionalidades disponíveis para a escolha do usuário. 

Como o programa é de código aberto, os usuários que também forem desenvolvedores podem personalizar o seu próprio modelo de editor de texto com as ferramentas da API do Quill, o website deste explica como fazer isso.

[Topo](#sumário)

## Começando a usar

O Quill foi projetado para ser executado em navegadores, sendo assim, sua única restrição recai na versão do navegador do usuário. Assim como muitas outras bibliotecas Javascript, ele apoia apenas as últimas duas versões de cada navegador principal. Desta forma, uma certa quantidade de usuários serão privados do convívio como a ferramenta.

É possível baixar cada versão do editor de textos1 e instalá-las. Em um ambiente Linux é possível realizar a instalação de duas formas distintas. São elas:

- npm - npm install quill
- tar - https://github.com/quilljs/quill/releases

Após fazer o download, para que o usuário comece a utilizar o Quill, basta usar o seguinte código abaixo:
```
<!-- Include Quill stylesheet -->
<link href="https://cdn.quilljs.com/1.0.0/quill.snow.css" rel="stylesheet">

<!-- Create the toolbar container -->
<div id="toolbar">
  <button class="ql-bold">Bold</button>
  <button class="ql-italic">Italic</button>
</div>

<!-- Create the editor container -->
<div id="editor">
  <p>Hello World!</p>
</div>

<!-- Include the Quill library -->
<script src="https://cdn.quilljs.com/1.0.0/quill.js"></script>

<!-- Initialize Quill editor -->
<script>
  var editor = new Quill('#editor', {
    modules: { toolbar: '#toolbar' },
    theme: 'snow'
  });
</script>
```
[Topo](#sumário)

## Conclusão

Este editor de textos web foi projetado e está sendo desenvolvido para abordar uma parte dos usuários de editores online ainda muito pouco explorada. Seus criadores estão trilhando o caminho deste software para que ele se torne o melhor editor de textos ricos online. Ele já conta com a vantagem de ser desenvolvido em javascript, o que proporciona praticamente o mesmo alcance de um navegador, desde que o mesmo esteja atualizado. O software possui características que o diferenciam de seus poucos concorrentes no mercado, como por exemplo, o suporte ao LaTex e a possibilidade de poder editar até mesmo linhas de códigos, entre outras.

Sua versão mais recente foi liberada neste ano e o seu repositório no GitHub está entre os mais visitados. Ele recebe uma quantidade considerável de pull requests, o que acaba lhe ocasionando uma certa frequência maior de atualizações e correções de bugs.

Sua API foi inteiramente construída para o seu uso específico, fazendo com que suas ferramentas se tornem mais fluidas e menos complexas. Porém, ela pode ser utilizada em outras ferramentas, caso o projetista assim deseje, uma vez que ela é de código livre. Essa característica ajuda em muito em sua manutenção e melhoria de performance. Ela, é claro, não possui restrição quanto ao sistema operacional, mais uma das vantagens de ser projetada para vários navegadores.

O programa é relativamente novo, cerca de dois anos, e ainda pode e vai passar por muitas mudanças e adequações até que se torne indispensável em aplicações Web. Ele pode receber muitas novas ferramentas devido à ambição do seu projeto original de ser “o” melhor editor de rich text online.

[Topo](#sumário)

## Referências

1. https://quilljs.com/blog/announcing-quill-1-0/#new-features
2. https://webpack.github.io/ 
3. https://en.wikipedia.org/wiki/Rich_Text_Format
4. https://github.com/quilljs/quill/releases/tag/v1.0.6

[Topo](#sumário)


