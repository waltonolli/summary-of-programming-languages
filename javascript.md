# Glossário básico de JavaScript

## Entrada e saída de dados

- Entrada de dados é usada para ler dados do usuário
- prompt é usado para solicitar dados do usuário
- console.log é usado para exibir dados no console

```js
const nome = prompt("Qual é o seu nome?")   // solicita o nome do usuário
console.log(nome)                           // exibe o nome do usuário
```

## Variáveis (*variables*)
São "caixas" nomeadas que armazenam um valor na memória. 
Em JavaScript, declaram-se com `let`, `const` ou `var`.
- let é usado para declarar variáveis que podem ser alteradas.
- const é usado para declarar variáveis que não podem ser alteradas
- var caiu em desuso, mas ainda é suportado

```js
let idade = 30;      // pode ser alterada
const nome = "Walkyria";       // não pode ser reatribuída
console.log(`Seu nome é ${nome} e tem ${idade} anos.`) // Interpolação de variaveis em strings. Tamplete literal com `${}`
```

## Tipos de dados

- String
- Number
- Boolean
- Array
- Object
- Null
- Undefined

Para descobrir o tipo de um valor, utilize o operador `typeof`:

```js
const nome = "Walkyria";
const idade = 30;
const pessoa = { nome: "Ana", idade: 30 };
const novaVariavel = True;

console.log(typeof nome);   // "string"
console.log(typeof idade);  // "number"
console.log(typeof pessoa); // "object"
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

## Funções (*functions*)
São blocos de código reutilizáveis que executam uma tarefa, podendo receber valores (*parameters*) e devolver um resultado (*return*).

```js
function somar(a, b) {
  return a + b;
}
somar(2, 3); // 5
```

## Objetos (*objects*)
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

## Condições (*conditions* / *conditionals*)
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

Operador ternário (`condição ? a : b`)

```js
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

Switch:
- Uma estrutura de seleção de valores que executa um bloco de código para cada caso de valor.
- É uma alternativa mais simples e eficiente para o if...else.

```
switch (valor) {
  case 1:
    // código a ser executado se valor for 1
    break
  case 2:
    // código a ser executado se valor for 2
    break
  default:
    // código a ser executado se valor não for 1 ou 2
}
```

---

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