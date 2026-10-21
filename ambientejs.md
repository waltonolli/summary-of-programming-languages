# JavaScript Runtime Environments(ambientes de execução)

O ambiente de execução é onde seu programa será executado. Ele determina quais objetos globais seu programa pode acessar e também pode impactar a forma como ele é executado.  
  
Módulos são trechos de código reutilizáveis ​​em um arquivo que podem ser exportados e importados para uso em outro arquivo. Um programa modular é aquele cujos componentes podem ser separados, usados ​​individualmente e recombinados para criar um sistema complexo.  
<img src="https://static-assets.codecademy.com/Courses/Learn-JavaScript/Modules/modular-program-diagram.svg" alt="diagrama de um módulo" width="300">

## DOM (Document Object Model)
O *Document Object Model (DOM)* é um modelo lógico que estrutura o documento HTML como um objeto. O DOM é uma API implementado por navegadores para permitir que o JavaScript *acesse, modifique e atualize* a estrutura de uma página web em HTML de forma organizada.

## Ambiente de execução de um navegador (módulo ES6)
O Ambiente mais comum onde o JavaScript é executado é no navegador. O JavaScript é interpretado pelo navegador, o que significa que ele é executado na memória do navegador. Salve um arquivo com a extensão `.html`, insira o código JavaScript no corpo do arquivo e salve o arquivo. Abra o arquivo no navegador para ver o resultado.
- o conteúdo javascript é colocado dentro de um elemento `<script>` no arquivo html.
- o arquivo html é carregado e interpreato pelo navegador.
Exemplo: meu_site.html
```html
<!-- my_website.html -->
<html>
  <body>
    <h1> My Website </h1>
    <script> window.alert('Hello World'); </script>
  </body>
</html>
```

## Implementando módulos ES6 no Browser (navegador)
O módulo ES6 é um recurso que permite que você escreva código JavaScript que pode ser usado em diferentes arquivos. Ao criar um site, é preciso criar um *arquivo HTML*, um *arquivo CSS* e um *arquivo JavaScript*. O arquivo HTML é usado para criar a estrutura da página, o arquivo CSS é usado para estilizar a página e o arquivo JavaScript é usado para adicionar interatividade e comportamento à página.  
```html
<!-- secret-messages.html --> 
<html>
  <head>
    <title>Secret Messages</title>
  </head>
  <body>
    <button id="secret-button"> Press me... if you dare </button>
    <p id="secret-p" style="display: none"> Modules are fancy! </p>
    <script type="module" src="./secret-messages.js"> </script>
  </body>
</html>
```
- A adição do atributo `type='module'` ao elemento `<script>` é importante. A omissão desse atributo pode fazer com que alguns navegadores exibam um erro. 
- `secret-messages.html` renderiza um `<button>`elemento e um elemento de parágrafo `<p>` oculto (de `<display: none>`). Em seguida ele carrega o script secret-messages.js usando o caminho do arquivo "./secret-messages.js". 

### Sintaxe de Exportação Nomeada do ES6
Um módulo deve estar inteiramente contido dentro de um arquivo para que possa ser importado. Para exportar um módulo, deve-se utilizar a sintaxe de exportação nomeada do ES6: `export { nome1, nome2, nome3 };`, o nome do módulo é o nome do arquivo. 
```js
/* dom-functions.js */
const toggleHiddenElement = (domElement) => {
  if (domElement.style.display === 'none') {
    domElement.style.display = 'block';
  } else {
    domElement.style.display = 'none';
  }
}

const changeToFunkyColor = (domElement) => {
  const r = Math.random() * 255;
  const g = Math.random() * 255;
  const b = Math.random() * 255;
        
  domElement.style.background = `rgb(${r}, ${g}, ${b})`;
}

export { toggleHiddenElement, changeToFunkyColor };
```
### Sintaxe de importação nomeada do ES6
A sintaxe ES6 para **importar** recursos nomeados de módulos é semelhante à seguinte `export` sintaxe: `import { nome1, nome2, nome3 } from "./nome-do-arquivo.js";`.  
```js
/* secret-messages.js */
import { toggleHiddenElement, changeToFunkyColor } from '../modules/dom-functions.js';

const buttonElement = document.getElementById('secret-button');
const pElement = document.getElementById('secret-p');

buttonElement.addEventListener('click', () => {
  toggleHiddenElement(pElement);
  changeToFunkyColor(buttonElement);
});
```
- Em `secret-messages.js`, as funções `toggleHiddenElement` e `changeToFunkyColor` são importadas do módulo `dom-functions.js` usando o `import` e o nome do módulo.
- Usando DOM API, objetos DOM (Document Object Model) são criados para referenciar o botão e o parágrafo via `document`. Esses objetos são armazenados nas variáveis `buttonElement` e `pElement`.
- Um `event listener` é adicionado ao `buttonElement` para "ouvir" os eventos de `'click'` e responder chamando `toggleHiddenElement()` com `pElement` como argumento.
- Em `dom-functions.js` a função `toggleHiddenElement` é declarada. Aceita um elemento DOM `domElement`como entrada e irá mostrar ou ocultar esse elemento dependendo do seu valor atual em de `style.display`.
- A função `changeToFunkyColor` é declarada. Aceita um elemento DOM `domElement`como entrada e irá alterar o valor de `style.background` para um valor aleatório. 
Além da sintaxe acima, na qual todas as *exportações nomeadas* são listadas juntas, **valores individuais** podem ser exportados como *exportações nomeadas* simplesmente colocando a palavra-chave `export` antes da declaração da variável. Como no exemplo abaixo:
```js
/* dom-functions.js */
export const toggleHiddenElement = (domElement) => {
  // logic omitted...
}

export const changeToFunkyColor = (domElement) => {
  // logic omitted...
}
``` 
  
## Ambiente de execução do Node.js (módulos CommonJS)
Em 2009, o ambiente de execução Node.js foi criado com o objetivo de executar código JavaScript sem um navegador, permitindo assim que os programadores criassem aplicações completas (front-end e back-end) usando apenas a linguagem JavaScript. O Node.js é executado no servidor e não no navegador.  
O ambiente de execução do Node.js oferece aos aplicativos de back-end acesso a uma variedade de recursos indisponíveis em um navegador, como acesso ao sistema de arquivos, banco de dados e rede do servidor.

### Para exportar módulos
Para criar um módulo, basta criar um novo arquivo onde as variáveis ​​e funções possam ser declaradas. Em seguida, para disponibilizar essas funções para outros arquivos, adicione-as como propriedades ao `module.exports` objeto integrado
```js
/* converters.js */

/* DECLARAÇÃO DA FUNÇÃO*/
function celsiusToFahrenheit(celsius) {
  return celsius * (9/5) + 32;
}

/* ABORDAGEM #1 PARA EXPORTAR FUNÇÃO DE MÓDULO: função já definida é atribuida a module.exports */
module.exports.celsiusToFahrenheit = celsiusToFahrenheit;

/* ABORDAGEM #2 PARA EXPORTAR FUNÇÃO DE MÓDULO: Uma nova expressão de função é declarada e atribuída a module.exports */
module.exports.fahrenheitToCelsius = function(fahrenheit) {
  return (fahrenheit - 32) * (5/9);
};
```

### Para importar módulos
O `module.exports` é um objeto integrado ao ambiente de execução do Node.js. Agora outros arquivos podem *importar* esse objeto e usar essas funções utilizando outro recurso integrado ao ambiente de execução do Node.js, o `require()`.
O `require()`função aceita uma string como argumento. Essa string fornece o caminho do arquivo para o módulo que você deseja importar.
```js
/* water-limits.js */
const converters = require('./converters.js');

const freezingPointC = 0;
const boilingPointC = 100;

const freezingPointF = converters.celsiusToFahrenheit(freezingPointC);
const boilingPointF = converters.celsiusToFahrenheit(boilingPointC);

console.log(`The freezing point of water in Fahrenheit is ${freezingPointF}`);
console.log(`The boiling point of water in Fahrenheit is ${boilingPointF}`);
```
No exemplo acima, `./` é um caminho relativo que indica que `converters.js` está armazenado no mesmo diretório que `water-limits.js`. Quando você usa `require()`, todo o objeto `module.exports` é devolvido e armazenado na variável *converters*. Isso significa que ambos, `.celsiusToFahrenheit()` e `.fahrenheitToCelsius()` métodos podem ser usados neste programa.

### Usando desestruturação de objetos (Object Destructuring)
Em muitos casos, os módulos irão exportar um grande número de dados e funções, mas apenas um ou dois deles são necessários em um determinado arquivo. Você pode usar a *desestruturação de objetos (object destructuring)* para importar apenas os dados ou funções que você precisa.
```js
/* celsius-to-fahrenheit.js */
const { celsiusToFahrenheit } = require('./converters.js');

const celsiusInput = process.argv[2]; 
const fahrenheitValue = celsiusToFahrenheit(celsiusInput);

console.log(`${celsiusInput} degrees Celsius = ${fahrenheitValue} degrees Fahrenheit`);
```
Acima, extraimos somente o objeto `celsiusToFahrenheit` do módulo `converters.js`. 

> O `process.argv` no Node.js é um array que guarda os argumentos passados pela linha de comando quando você executa um script. Ele permite que seu programa em JavaScript receba dados externos (como nomes, caminhos ou opções) direto do terminal. `process.argv[0]`: O caminho do executável do Node.js (ex: /usr/bin/node). `process.argv[1]`: O caminho do arquivo JavaScript que está sendo executado (ex: app.js). `process.argv[2+]`: Quaisquer argumentos ou parâmetros extras digitados por você.

