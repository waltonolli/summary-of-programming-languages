# DOM e JavaScript

O HTML define a estrutura de uma página web usando elementos como blocos de construção. No entanto, o HTML por si só não consegue produzir interatividade. Se HTML e CSS fornecem estrutura e estilo para a página, o JavaScript formece interatividade. O elemento `<script>` permite adicionar código JavaScript a um arquivo HTML.  

A Vinculação de código é preferível devido a um conceito chamado "Separação de Responsabilidades" (Separation of Concerns (SoC)). Em vez de ter um código desorganizado e todo no mesmo arquivo, os desenvolvedores web separam seu código em arquivos diferentes, tornando cada "responsabilidade" mais fácil de entender e mais conveniente quando alterações precisam ser feitas.  

Sendo assim, cria-se um arquivo JavaScript separado e vincula-se esse arquivo ao HTML usando o elemento `script` no final do elemento `body` e usando o atributo `src` para referenciar o arquivo JavaScript.

```html
<body>
    <h1>Hello World</h1>
    <p>This is a paragraph.</p>
    <script src="script.js"></script>
</body>
```

Os navegadores vêm equipados com analisadores HTML que ajudam os navegadores a renderizar os elementos de acordo. Os elementos, incluindo o elemento `<script>`, são analisados por padrão na ordem em que aparecem no arquivo HTML. Quando o analisador de HTML encontra um elemento `<script>`, ele carrega o script e executa seu conteúdo *antes* de analisar o restante do HTML.  

- O analisador HTML NÃO processa o próximo elemento no arquivo HTML até que o elemento `<script>` seja carregado e executado.
- Os scripts são carregados sequencialmente, portanto, se um script depende de outro, eles devem ser colocados exatamente nessa ordem dentro do arquivo HTML.
- O HTML4 introduziu os atributos `defer` e `async` para o elemenbto `<script>`para lidar com o tempo de espera do usuário no site, com base em diferentes cenários.
- O atributo `defer` especifica que os scripts devem ser *executados* após a análise completa do arquivo HTML. Quando o analisador HTML encontra um elemento `<script>` com esse `defer` atributo, ele *carrega o script*, mas *adia a execução* do JavaScript até que termine de analisar os demais elementos do arquivo HTML. Quando um script contém funcionalidades que exigem interação com o DOM, o `defer` atributo é a melhor opção.

```html
<script src="script.js" defer></script>
```
-  O atributo `async` carrega e executa o script de forma assíncrona com o restante da página web. O analisador HTML continuará analisando o HTML enquanto o script é baixado em segundo plano e executado imediatamento após o download. Se não importa exatamente em que ponto o arquivo de script é executado, o carregamento assíncrono é a opção mais adequada, pois otimiza o tempo de carregamento da página da web.
```html
<script src="script.js" async></script>
```


## DOM - Document Object Model

O **_Document Object Model (DOM)_** é um modelo lógico que estrutura o documento HTML como um objeto. O DOM é uma árvore de *"nós"* que representa uma página HTML. Quando uma página da web é carregada, o navegador cria uma representação de árvore do documento HTML. O DOM é implementado pelos navegadores para permitir que o JavaScript *acesse, modifique e atualize* a estrutura de uma página web HTML de forma organizada.

Saiba mais sobre a [anatomia do DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Anatomy_of_the_DOM) 

- Um *nó pai* é qualquer nó que seja um ancestral direto de outro nó.
- Um *nó filho* é um descendente direto de outro nó, chamado de nó pai.
- Existem quatro tipos de nós:
  - Nós de texto: são nós que contêm *texto*.
  - Nós de elemento: são nós que contêm *elementos*. Ex: `<p>`
  - Nós de atributo: são nós que contêm *atributos*. Ex: `<p id="my-paragraph">`
  - Nós de nó: são nós que contêm outros nós.

<img src="./img/dom.png" alt="diagrama do">  


## Métodos e Propriedades da Interface DOM

**`document`** - É o nó raiz da árvore DOM. Antes de acessar um elemento específico na página, é necessário acessar a própria estrutura do documento. `document` permite que os script acessem e manipulem os *elementos filhos* da página.  

Ao usar o DOM no seu script para acessar um elemento HTML, você também tem acesso a todas as *propriedades* desse elemento. Isso inclui a capacidade de *modificar o conteúdo do elemento*, bem como seus *atributos* e *propriedades*, que podem variar desde a modificação do texto dentro de um `<p>` elemento até a atribuição de uma nova cor de fundo para um `<div>`.  

O exemplo abaixo altera o conteúdo do elemento `<h1>` para "Hello World".
```js
document.body.innerHTML = '<h1>Hello World</h1>';
```

[métodos fundamentais de nível DOM 1 e como usá-los a partir do JavaScript.](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Building_and_updating_the_DOM_tree)

## Seletores CSS

Com `document.body` acessamos o elemento `<body>` com a palavra-chave `document`. Mas para acessar um elemento específico sem acessar todo o elemento `<body>`? O DOM nos permite usar *seletores CSS* para selecionar elementos específicos.

*Seletores CSS* definem os elementos aos quais um conjunto de regras CSS se aplica, mas também podemos usar esses mesmos seletores para acessar elementos DOM com JavaScript! Os seletores podem incluir um *nome de tag*, uma *classe* ou um *ID*.

JavaScript possui *métodos* que selecionam elementos com base em sua *classe*, *id* ou *nome de tag*.

- Para selecionar um elemento com base em seu nome de tag, use o método `getElementByTagName()`.
- Para selecionar um elemento com base em sua classe, use o método `getElementsByClassName()`.
- Para selecionar um elemento com base em seu ID, use o método `getElementById()`.
- `querySelector()` nos permite especificar um seletor CSS como uma *string* e retorna o *primeiro elemento* que corresponde a esse seletor.  

Exemplos: 
```js
document.querySelector('h1').innerHTML = "Most popular Harry Potter characters";
document.getElementById('bio').innerHTML = 'The description';
// Set first element of .student class as 'Not yet registered'
document.getElementsByClassName('student')[0].innerHTML = 'Not yet registered';
// Set second <li> tag as 'Cedric Diggory'
document.getElementsByTagName('li')[1].innerHTML = 'Cedric Diggory`;
```

## Estilizando Elementos

Para estilizar um elemento, precisamos acessar o seu *atributo* `style`. O atributo `.style` de um elemento DOM fornece acesso ao estilo inline dessa tag HTML. A sintaxe segue um formato `element.style.property`, com a propriedade representando uma propriedade CSS. Diferente do CSS, a propriedade DOM `.style` não implementa um *hífen (-)*, como `background-color`, mas sim uma *notação camelCase*, `backgroundColor`. Confira mais em [W3 Reference on the HTML DOM style object](https://www.w3schools.com/jsref/dom_obj_style.asp).  

Exemplo:
```js
// seleciona o primeiro elemento com a classe blue.
let blueElement = document.querySelector('.blue'); 

// atribui a cor azul como cor de fundo.
blueElement.style.backgroundColor = 'blue'; 
```


## Percorrendo o DOM

Um nó pai é qualquer nó que seja ancestral direto de outro nó. Um nó filho é um descendente direto de outro nó, chamado nó pai. Essas relações seguem a estrutura hierárquica do código HTML. Elementos aninhados dentro de um elemento HTML são filhos desse elemento pai.  

Cada elemento possui uma propriedade `.parentNode` que retorna o elemento pai especificado na hierarquia DOM, e uma propriedade `.children` que retorna um array dos filhos do elemento especificado. Se o elemento não tiver filhos, ele retornará `null`. `document` é o nó raiz, então `.parentNode` retorna `null`.

Exemplo:
```html
<ul id='groceries'>
  <li id='must-have'>Toilet Paper</li>
  <li>Apples</li>
  <li>Chocolate</li>
  <li>Dumplings</li>
</ul>
```
```js
let parentElement = document.getElementById('must-have').parentNode; // returns <ul> element
let childElements = document.getElementById('groceries').children; // returns an array of <li> elements
```


## Criando e Inserindo Elementos

Para criar um elemento HTML, precisamos usar o método `createElement()`. Este método retorna um novo elemento com base na *tag* passada nele como *argumento*. No exemplo abaixo, `createElement()` toma `p` como seu argumento que cria um elemento `<p>` vazio e o armazena como a *variável* `paragraph`.  

```js
let paragraph = document.createElement('p');

paragraph.id = 'info'; 
paragraph.innerHTML = 'The text inside the paragraph';

document.body.appendChild(paragraph);
```

Podemos atribuir valores às propriedades do elemento recém-criado, como fizemos anteriormente com elementos existentes. Acima, usamos a propriedade `.id` para atribuir `'info'` como ID e a propriedade `.innerHTML` para definir `'The text inside the paragraph'` como o conteúdo do elemento `<p>`.  

Para criar um elemento e adicioná-lo à página da web, você deve atribuí-lo como filho de um elemento que já existe no DOM, referido como o elemento pai. Chamamos esse processo de *appending*. O método `appendChild()` adiciona um elemento filho ao elemento pai especificado. No exemplo acima, o método `.appendChild()` não substitui o conteúdo dentro do pai. Em vez disso, *ele adiciona o novo elemento como o último filho desse pai*.


## Removendo ou Escondendo Elementos

Para remover um elemento do DOM, você pode usar o método `removeChild()`. Este método remove um elemento filho do elemento pai especificado.
```js
let paragraph = document.querySelector('p');
document.body.removeChild(paragraph);
```

Se você quiser ocultar um elemento em vez de excluí-lo completamente, a propriedade `.hidden` permite que você a oculte definindo a propriedade como `true` ou `false`:
```js
document.getElementById('sign').hidden = true;
```






