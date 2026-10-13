# GLOSSÁRIO BÁSICO DE JAVASCRIPT

## Entrada e saída de dados
(*input and output*)

- Entrada de dados é usada para ler dados do usuário
- `prompt()` é usado para solicitar dados do usuário
- `console.log()` é usado para exibir dados no console

```js
const nome = prompt("Qual é o seu nome?")   // solicita o nome do usuário
console.log(nome)                           // exibe o nome do usuário
```

## Variáveis
(*variables*)
São "caixas" nomeadas que armazenam um valor na memória. 
Em JavaScript, declaram-se com `let`, `const` ou `var`.
- `let` é usado para declarar variáveis que podem ser alteradas.
- `const` é usado para declarar variáveis que não podem ser alteradas
- `var` caiu em desuso, mas ainda é suportado

```js
let idade = 30;      // pode ser alterada
const nome = "Walkyria";       // não pode ser reatribuída
console.log(`Seu nome é ${nome} e tem ${idade} anos.`) // Interpolação de variaveis em strings. Tamplete literal com `${}`
```
### Hoisting
O JavaScript é uma linguagem de *hoisting*, ou seja, o código é interpretado antes de ser executado. Isso significa que variáveis e funções são declaradas antes de serem usadas. Isso é útil para evitar problemas de escopo e garantir que as variáveis estejam disponíveis quando você as usa. 

### Escopo
(*scope*)
Escopo é a região do código onde uma variável (ou função) pode ser acessada. O escopo é definido pela ordem em que as declarações são executadas.
- **Escopo global**: variáveis e funções declaradas fora de qualquer função.
- **Escopo de função**: variáveis e funções declaradas dentro de uma função.
- **Escopo de bloco**: variáveis e funções declaradas dentro de um bloco de código (qualque trecho declarado entre chaves {}).

**Cadeia de escopo (Scope Chain)**: Cadeia de escopo é a ordem em que as declarações são executadas. Quando você usa uma variável, o JavaScript a procura primeiro no escopo atual; se não achar, sobe para o escopo de fora, e assim por diante até o global. Nunca o contrário: o escopo externo não enxerga o interno.

**Poluição de escopo (Scope Pollution)**: A poluição do escopo ocorre quando temos muitas variáveis no espaço de nomes global, ou quando reutilizamos variáveis em diferentes escopos. A poluição de escopo dificulta acompanhar nossas diferentes variáveis e nos prepara para possíveis acidentes.

**Bom exemplo de escopo (Good Scope Example)**: Devemos seguir as melhores práticas para delimitar o escopo de nossas variáveis ​​da forma mais restrita possível, utilizando escopo de bloco.
- Tornará o código mais legível, já que os blocos o organizarão em seções distintas.
- Torna o código mais compreensível, esclarecendo quais variáveis ​​estão associadas a diferentes partes do programa, em vez de ter que rastreá-las linha por linha!
- É mais fácil manter um código com escopo bem definido, pois ele será modular.
- Economiza memória porque as variáveis ​​com escopo de bloco deixarão de existir após a conclusão da execução do bloco.

## Tipos de dados

- String
- Number
- Boolean
- Array
- Object
- Null
- Undefined

Para descobrir o tipo de um valor, utilize o operador `typeof()`:

```js
const nome = "Walkyria";
const novaVariavel = True;

console.log(typeof nome);   // "string"
console.log(typeof novaVariavel); // "boolean"
```

## Operadores

| Operador | Descrição |
| -------- | --------- |
| + | adição |
| - | subtração |
| * | multiplicação |
| / | divisão |
| % | módulo |
| ++ | incrementa |
| -- | decrementa |
| = | atribuição |

## Operadores de comparação

| Operador | Descrição |
| -------- | --------- |
| == | is equal to |
| === | is equal to (strict) |
| !== | is not equal to |
| > | greater than |
| >= | greater than or equal to |
| < | less than |
| <= | less than or equal to |

## Operadores lógicos

| Operador | Descrição |
| -------- | --------- |
| && | e |
| \|\| | ou |
| ! | não, inverte |

## Condições / fluxo de controle
(*conditions* / *conditionals*)
Estruturas que fazem o programa tomar decisões: um trecho de código só executa se uma expressão for verdadeira (*true*).

```js
let isNightTime = true;

if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```

Em uma condição booleana, o JavaScript atribui o valor verdadeiro a uma variável se você usar o || operador `true` na sua atribuição:

```js
let username = '';
let defaultName = username || 'Stranger'; // username se verdadeiro, 'Stranger' se falso
```

### Operador ternário
É uma forma curta de escrever uma estrutura condicional if/else em uma única linha no JavaScript.
```js
// condicao ? valorSeVerdadeiro : valorSeFalso;
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

### Switch
- Uma estrutura de seleção de valores que executa um bloco de código para cada caso de valor.
- É uma alternativa mais simples e eficiente para o if...else.

```js
switch (expressao) {
  case valor1:
    // Código executado se expressao === valor1
    break;
  case valor2:
    // Código executado se expressao === valor2
    break;
  default:
    // Código executado se nenhum dos casos anteriores for verdadeiro
}
```
- *`expressao`* valor ou variável a ser testada.
- *`case valor`*: Uma opção de comparação. O JavaScript usa a comparação estrita (===), ou seja, o tipo do dado também precisa ser igual.
- *`break;`*: Uma palavra-chave crucial. Ela encerra a execução do switch. Se você esquecer o break, o código continuará executando os próximos casos automaticamente (comportamento chamado de fall-through).
- *`default`*:  É o caso padrão (opcional). Funciona como `else` final, sendo executado se nenhuma correspondência for encontrada.

## Funções
(*functions*)

São blocos de código reutilizáveis que executam uma tarefa, podendo receber valores (*parameters*) e devolver um resultado (*return*).
- ``Parametros` são tratados como variáveis dentro da função.
- `Return` é o valor que a função devolve.
- `Identificador` é o nome da função.
- `Argumentos` são os valores que são passados para a função quando ela é chamada.

Sintaxe:
```js
function calcularArea(largura, altura) { 
  console.log(largura * altura); // corpo da função - código a ser executado
}
calcularArea(5, 10); // argumentos como valores

const base = 10;
const comprimento = 5;
calcularArea(base, comprimento); // argumentos como variáveis
```

### Parametros padrão
(*default parameters*)
Permitem que os parâmetros tenham um valor pré-determinado caso nenhum argumento seja passado para a função ou se o argumento for indefinido quando chamado.
```js
function calcularArea(largura = 10, altura = 10) {
  console.log(largura * altura);
}
calcularArea(); // 100
calcularArea(5); // 50
calcularArea(6, 15); // 90
```

### Retorno
(*return*)
É usado para retornar um valor para o código que chamou a função. Por padrão, o valor resultante é indefinido.
-Para capturar o valor retornado, utilize a palavra-chave `return`. Sem a palavra-chave `return`, a função calculará o valor mas retornará o valor `indefinido`.
- Quando uma instrução de retorno é usada em um corpo de função, a execução da função é interrompida e o código que se segue não será executado.
- A palavra-chave de retorno é poderosa porque permite que funções produzam uma saída. Podemos então salvar a saída em uma variável para uso posterior.
```js
function calcularArea(largura, altura) {
  return = largura * altura;
  
}
const area = calcularArea(5, 10); // salva o valor retornado em uma variável
console.log(area); // 50
```

### Funções auxiliares
(*helper functions*)
Também podemos usar o valor de retorno de uma função dentro de outra função. Essas funções sendo chamadas dentro de outra função são frequentemente referidas como funções auxiliares.
```js
function multiplicaNovePorCinco(num) {
  return num * 9/5;
};

function celsiusToFahrenheit(celsius) {
  return multiplicaNovePorCinco(celsius) + 32;
};

celsiusToFahrenheit(0); // returns 32
```

### Expressões de função
(*function expressions*)
- Se você usa function expression, defina a função antes de chamá-la. Se usa function declaration, a ordem no arquivo não importa.
- Declare uma variável para fazer do nome da variável o nome, ou identificador, da função.
- Em uma expressão de função, o nome da função geralmente é omitido. Uma função sem nome é chamada de *função anônima*.
- Uma expressão de função é frequentemente armazenada em uma variável para ser referenciada.
```js
const soma = function(a, b) {
  return a + b;
};
console.log(soma(2, 3)); // 5
```

### Arrow Functions
(*arrow functions*)
São funções anônimas, que podem ser usadas em lugar de funções nomeadas. São úteis para criar funções de uma única expressão.
```js
const areaRetangulo = (larg, alt) => {
  let area = larg * alt;
  return area;
}

const soma = (a, b) => a + b;
```

Funções que aceitam apenas um parâmetro não precisam que esse parâmetro seja encerrado entre parênteses.
No entanto, se uma função recebe zero ou vários parâmetros, os parênteses são obrigatórios.
Um corpo de função composto por um bloco de linha única não precisa de chaves{}. Sem as chaves{}, tudo o que essa linha avaliar será automaticamente devolvido. O conteúdo do bloco deve seguir imediatamente a seta => e a palavra-chave de retorno pode ser removida. Isso é chamado de *retorno implícito*.
```js
//ZERO PARAMETERS
const functionName = () => { /* ... */ };
//ONE PARAMETER
const functionName = param => { /* ... */ };
//MULTIPLE PARAMETERS
const functionName = (param1, param2) => { /* ... */ };
```

### Refatoração de arrow functions
Se temos a função:
```js
const squareNum = (num) => {
  return num * num;
};
```

Podemos refatorar para:
```js
const squareNum = num => num * num;
```

## Arrays / listas
(*arrays*)
Uma lista é uma sequência ordenada de valores. Uma lista pode ser de qualquer tipo de dado, incluindo outras listas.
Arrays podem armazenar qualquer tipo de dado, incluindo outros arrays.
- Para criar um array, utilize a sintaxe `[]`.
- Cada item dentro de um array é chamado de *elemento*.
- Cada elemento é separado por vírgula.
- Arrays são indexados a partir de 0.
```js
const array1 = [1, 2, 3, 4, 5];
const array2 = ["um", "dois", "três"];
const array3 = [array1, array2];
```

### Acessando um elemento
Para acessar um elemento de um array, utilize o índice do elemento. 
O primeiro elemento do array tem índice 0, o segundo 1, e assim por diante.
```js
array1[0]; // 1
array1[1]; // 2
array1[2]; // 3
array1[3]; // 4
array1[4]; // 5
```
### Alterando Valor de um Elemento
Para alterar o valor de um elemento de um array, utilize o índice do elemento.


## Objetos
(*objects*)
São coleções de propriedades e métodos agrupados sob um mesmo nome. Representam "coisas" (um usuário, um produto, uma data).

```js
const carro = { marca: "Fiat", ano: 2024, ligar() { /* ... */ } };
```

## Propriedades (*properties*)
São valores associados a um objeto, no formato chave-valor. Descrevem características dele.

```js
const pessoa = { nome: "Ana", idade: 30 };
pessoa.nome; // "Ana" → "nome" é uma propriedade
```

## Métodos (*methods*)
São funções que pertencem a um objeto. Descrevem ações que ele pode executar.

```js
const pessoa = {
  nome: "Ana",
  saudar() { return `Olá, ${this.nome}!`; } // saudar é um método
};
pessoa.saudar();
```

## Instância (*instance*)
É um objeto concreto criado a partir de um molde (uma *class* ou uma função construtora). A classe define a estrutura (quais propriedades e métodos existem); a instância é uma "cópia" real dessa estrutura, com seus próprios valores. Cada instância é independente das outras.

Analogia: a classe é a planta de uma casa; cada casa construída a partir dela é uma instância.

```js
class Carro {
  constructor(marca, ano) {
    this.marca = marca;   // propriedade
    this.ano = ano;       // propriedade
  }
  ligar() {               // método
    return `${this.marca} ligado!`;
  }
}

const carro1 = new Carro("Fiat", 2024);   // carro1 é uma instância de Carro
const carro2 = new Carro("Ford", 2020);   // carro2 é outra instância

carro1.ligar(); // "Fiat ligado!"
carro2.ligar(); // "Ford ligado!"

carro1 instanceof Carro; // true
```

O verbo **instanciar** (*to instantiate*) significa criar uma instância, normalmente com a palavra-chave `new`.

## Loop (*loop*) ou laço de repetição
Estrutura que repete um bloco de código várias vezes, enquanto uma regra for atendida ou até percorrer todos os itens de uma coleção.

```js
for (let i = 0; i < 3; i++) {
  console.log(i); // 0, 1, 2
}
```

Outros tipos: `while`, `do...while`, `for...of`, `for...in`.



## Resumo

| Português | Inglês | Ideia central |
|---|---|---|
| Variável | *variable* | Guarda um valor |
| Função | *function* | Executa uma tarefa reutilizável |
| Objeto | *object* | Agrupa dados e ações |
| Propriedade | *property* | Um dado dentro do objeto |
| Método | *method* | Uma função dentro do objeto |
| Instância | *instance* | Um objeto concreto criado a partir de uma classe |
| Loop | *loop* | Repete código |
| Condição | *condition* | Decide se o código executa |