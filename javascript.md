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

// Interpolação de variáveis em strings. Tamplete literal com `${}`
console.log(`Seu nome é ${nome} e tem ${idade} anos.`) 
```
### Hoisting
O JavaScript é uma linguagem de *hoisting*, ou seja, o código é interpretado antes de ser executado. Isso significa que variáveis e funções são declaradas antes de serem usadas. Isso é útil para evitar problemas de escopo e garantir que as variáveis estejam disponíveis quando você as usa. 

### Escopo
(*scope*)
Escopo é a região do código onde uma variável (ou função) pode ser acessada. O escopo é definido pela ordem em que as declarações são executadas.
- **Escopo global**: variáveis e funções declaradas fora de qualquer função.
- **Escopo de função**: variáveis e funções declaradas dentro de uma função.
- **Escopo de bloco**: variáveis e funções declaradas dentro de um bloco de código (qualque trecho declarado entre chaves {}).

**Cadeia de escopo (Scope Chain)**:  
Cadeia de escopo é a ordem em que as declarações são executadas. Quando você usa uma variável, o JavaScript a procura primeiro no escopo atual; se não achar, sobe para o escopo de fora, e assim por diante até o global. Nunca o contrário: o escopo externo não enxerga o interno.

**Poluição de escopo (Scope Pollution)**:  
A poluição do escopo ocorre quando temos muitas variáveis no espaço de nomes global, ou quando reutilizamos variáveis em diferentes escopos. A poluição de escopo dificulta acompanhar nossas diferentes variáveis e nos prepara para possíveis acidentes.

**Bom exemplo de escopo (Good Scope Example)**:  
Devemos seguir as melhores práticas para delimitar o escopo de nossas variáveis ​​da forma mais restrita possível, utilizando escopo de bloco.
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
- Objects

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
Uma estrutura de seleção de valores que executa um bloco de código para cada caso de valor.
É uma alternativa mais simples e eficiente para o if...else.

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

Funções são blocos de código reutilizáveis que executam uma tarefa, podendo receber valores (*parameters*) e devolver um resultado (*return*). São um tipo de objeto, elas possuem propriedades e métodos.Também são especiais porque podemos invocá-las, mas ainda assim podemos tratá-las como qualquer outro tipo de dado.
- `Parametros` são tratados como variáveis dentro da função.
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
- Arrays podem ser aninhados, ou seja, podem conter outros arrays dentro deles.
```js
const array1 = [1, 2, 3, 4, 5];
const array2 = ["um", "dois", "três"];
const array3 = [array1, array2]; // array aninhado
const nestedArr = [1, 2, [3, 4]]; // array aninhado
```

### Acessando um elemento
Para acessar um elemento de um array, utilize o índice do elemento. 
O primeiro elemento do array tem índice 0, o segundo 1, e assim por diante.
Para acessar um elemento, usamos o nome do array seguido do índice do elemento entre colchetes[].
```js
array1[0]; // 1
array2[1]; // dois
array3[1]; // ["um", "dois", "três"]
array1[3]; // 4
```
Podemos acessar os elementos dentro do array aninhado encadeando(_chaining_), adicionando mais notações entre colchetes com valores de índice.
```js
array3[1][2]; // três 
```
Também podemos acessar caracteres individuais em uma string, utilizando o índice do caractere.
```js
const hello = 'Hello World';
hello[0]; // 'H'
hello[5]; // 'W'
```

### Alterando Valor de um Elemento
Com acesso a um elemento em um array, também podemos atualizar seu valor.
```js
let seasons = ['Spring', 'Summer', 'Fall', 'Winter'];
seasons[0] = 'Autumn'; // atualiza o valor do primeiro elemento, substituindo o valor original.
console.log(seasons); // ['Autumn', 'Summer', 'Fall', 'Winter']
```

Variáveis declaradas com a palavra-chave `const` não podem ser reatribuídas. No entanto, **elementos** em um array declarado com `const` permanecem **mutáveis**. Isso significa que podemos alterar o conteúdo de um `const` array, *mas não podemos reatribuir um novo array ou um valor diferente.*
```js
let condimentos = ["Ketchup", "Mostarda", "Pimenta", "Sal"]
const utensilios = ["Faca", "Garfo", "Colher", "Colherinha"]
condimentos[0] = "Salsa"; // Altera valor do primeiro elemento
condimentos = ["Salsa"]; // Reatribui a array condimentos
utensilios[0] = "Forno"; // Altera valor do primeiro elemento
utensilios = ["Forno"]; // erro (não pode ser reatribuído porque é uma variavel const)
```

### A propridade length`
Uma das propriedades incorporadas de um array é o length, e retorna o número de itens no array. Acessamos a propriedade `.length` assim como fazemos com strings.
```js
const metas = ["Manter um diário", "Fazer aulas de ingles", "Ler 2 livros ao mês"];
const novaMeta = "Terminar faculdade";
console.log(metas.length); // 3
console.log(novaMeta.length); // 21
```
### O método push()
O método `push()` adiciona um elemento ao final de um array.
```js
const metas = ["Manter um diário", "Fazer aulas de ingles", "Ler 2 livros ao mês"];
metas.push("Terminar faculdade");
console.log(metas); // ["Manter um diário", "Fazer aulas de ingles", "Ler 2 livros ao mês", "Terminar faculdade"]
```
### O método pop()
O método `pop()` remove o último elemento de um array.
```js
const metas = ["Manter um diário", "Fazer aulas de ingles", "Ler 2 livros ao mês", "Terminar faculdade"]; 
metas.pop();
console.log(metas); // ["Manter um diário", "Fazer aulas de ingles", "Ler 2 livros ao mês"]
```
### Outros métodos de Array
`.pop()` e `.push()` aleram o array no qual eles são chamados. No entanto, há momentos em que não queremos mutar o array original, e podemos usar *métodos de array sem mutação*. Certifique-se de verificar os Docs para entender o comportamento do método antes de usá-lo.
- .join() - Concatena todos os elementos do array em uma string.
- .slice() - Retorna um novo array com os elementos selecionados.
- .splice() - Remove elementos do array.
- .shift() - Remove o primeiro elemento do array.
- .unshift() - Adiciona um elemento no início do array.
- .concat() -  Retorna um novo array com os elem. do array original e os elem. passados como argumento.
- .indexOf() - Busca o índice do primeiro elemento que corresponde ao valor buscado.

### Arrays e Funções
Arrays podem ser usados como parâmetros para funções.
Quando passamos um array em uma função, se o array é mutado dentro da função, essa mudança também será mantida fora da função.
**_pass-by-reference_** quando passamos para a função uma referência ao local onde a variável está armazenada na memória e alterando os dados lá.
```js
const conceito = ["Arrays", "podem", "ser", "mutados"];
function alterarArr(arr) {
  arr[3] = "MUTADOS";
}
alterarArr(conceito);
console.log(conceito); // ["Arrays", "podem", "ser", "MUTADOS"]
```


## Loop (*loop*) ou Laço de Repetição
Um *loop* é uma estrutura que repete um bloco de código (um conjunto de instruções), até que uma condição especificada, chamada condição de parada, seja atingida.
- Você pode ouvir o termo genérico iterar (*iterate*) ao se referir a loops; iterar simplesmente significa "repetir".

### O Loop For
A for loop contém três expressões separadas por ; dentro dos parênteses:
- Inicialização (*initialization*): inicia o loop e também pode ser usado para declarar variáveis.
- Condição (*condition*): verifica se o loop deve continuar. Condição em relação à qual a variável iteradora é avaliada. Se falsa o loop é encerrado.
- Incremento (*increment/afterthought*): instrução de iteração usada para atualizar a variável iteradora em cada iteração do loop.
```js
for (let contador = 0; contador <= 10; contador++) {
  console.log(contador); // 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
}
```
### Decremento (Looping Reverse)
Defina a *variável iterador* para o **valor mais alto** desejado na expressão de inicialização. Em seguida, use o operador `--` para decrementar o valor da variável.
```js
for (let contador = 10; contador >= 0; contador--) {
  console.log(contador); // 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0
}
```

### Loop Através de um Array
Um loop `for` pode ser usado para iterar sobre um array.
- A *variável iteradora* é o *índice* do array.
- Para percorrer cada elemento em um array, deve-se usar a propriedade `.length` do array em sua *condição*.
```js
const array = ["One", "Two", "Three", "Four", "Five"];
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}
```

### Loops for Aninhados
Usado para comparar valores em arrays.
```js
const array1 = [1, 2, 3, 4, 5];
const array2 = [6, 7, 8, 9, 10];
for (let i = 0; i < array1.length; i++) {
  for (let j = 0; j < array2.length; j++) {
    if (array1[i] === array2[j]) {
      console.log(`Ambos os arrays contêm o valor ${array1[i]}`);
    }
  }
}
```

### O Loop While
A sintaxe do loo `while` é ideal quando *não sabemos* com antecedência quantas vezes o loop deve ser executado.
Uma instrução `while` executa suas instruções enquanto uma condição é avaliada como verdadeira.
- A *variável contadora* é declarada antes do loop.
- `while (condição) {instrução com incremento ou decremento}`
- O *incremento* ou *decremento* da variável é feito dentro do loop. Sem isso criamos um *loop infinito*.
```js
let contadorDois = 1;
while (contadorDois <4) {
  console.log(contadorDois);
  contadorDois++;
}
```

### O Loop Do...While
Quando precisamos que o loop execute *pelo menos uma vez* antes da condição ser verificada, o loop `do...while` é mais adequado.
A `do... while` instrução diz para fazer uma tarefa uma vez e depois continuar fazendo até que uma condição especificada não seja mais atendida.
- `do...while` será executado pelo menos uma vez, independentemente de a condição ser avaliada como verdadeira ou não.
- A variável contadora é declarada antes do loop.
- O *incremento* ou *decremento* da variável é feito dentro do loop. Sem isso criamos um *loop infinito*.
```js
let contarString = "";
let i = 0;
do {
  contarString = contarString + i;
  i++;
} while (i < 5);
console.log(contarString); // 01234
```

## Break (*break*) palavra-chave
A palavra-chave `break` é usada para interromper um loop *antes* de ele terminar.
A instrução `break` pode ser útil em loops por grandes estruturas de dados! Com *breaks*, podemos adicionar condições de testes além da condição de parada e sair do loop quando foram atendidas.
```js
for (let i = 0; i < 99; i++) {
  if (i > 2 ) {
     break;
  }
  console.log('Banana.');
}
console.log('Laranja! Eu quebrei o loop.');
```

Outros tipos: `for...of`, `for...in`.

## Funções de Ordem Superior

### Funções como parâmetros
Parâmetro é um espaço reservado para os dados que são passados para uma função. Uma função de ordem superior (*higher-order functions*) é uma função que aceita outras funções como parâmetros, retorna uma função ou ambos. São úteis para escrever código mais legível e reutilizável.  
- Chamamos as funções que são passadas como parâmetros de *funções de retorno* (*callback functions*).
- Ao invocar uma função de ordem superior e passar outra função como argumento, passamos a própria função digitando o nome dela sem os parenteses.

```js
const funcaoDeOrdemSuperior = param => {
  param();
  return `Eu invoquei ${param} como uma função de retorno!`;
}

const outraFuncao = () => {
  return "Estou sendo invocado pela função de ordem superior!";
}

funcaoDeOrdemSuperior(outraFuncao); 
```

### Funções como dados
Podemos atribuir funções a *variáveis*. O valor atribuido é o *nome da função sem parenteses*. Queremos atribuir o valor da própria função, não o valor que ela retorna quando invocada.
```js
const digaQueEstouFazendoUmImportanteTrabalho = () => {
    console.log("I’m doing very important work!");
};
const ocupado = digaQueEstouFazendoUmImportanteTrabalho;
```


## Objetos
(*objects*)
São coleções de propriedades e métodos agrupados sob um mesmo nome. Representam "coisas" (um usuário, um produto, uma data). Usamos objetos para modelar coisas do mundo real, ou para construir as estruturas de dados que tornam a web possível.
- Objetos literais são criados escrevendo o conteúdo entre chaves `{}`.
- Objetos literais são *atribuidos (assigned)* a variáveis usadas para criar objetos.
```js
const carro = { 
  marca: "Fiat",
  ano: 2024,
  "Tipo de combustivel": "Gasolina"
};
```

### Propriedades (*properties*)
São o par `key: value` de um objeto, descrevem características dele.
```js
const pessoa = { 
  nome: "Ana", // propriedade1 key = nome value = Ana
  idade: 30.   // propriedade2 key = idade value = 30
};
```

### Acessando Propriedades
Para acessar propriedades de um objeto, usamos o `.` ou `[]` para acessar o valor de uma propriedade.
Devemos usar `[]` ao acessar chaves que *não são nomes de identificador válidos* (por exemplo, chaves que começam com um número ou contêm espaços ou caracteres especiais). Sem a notação entre parênteses nessas situações, nosso código lançaria um erro.
```js
pessoa.nome; // objeto.propriedade 
carro["Tipo de Combustivel"]; // objeto["propriedade"]
```
Com a notação entre colchetes `[]`, você também pode usar uma "variável" dentro dos `[]` para selecionar as chaves de um objeto. Isso pode ser especialmente útil ao trabalhar com funções:
```js
let retornaUmaPropriedade = (obj, prop) => obj[prop];
retornaUmaPropriedade(pessoa, "nome"); 
```

### Modificando Propriedades (*proerties assignment*)
Objetos são *mutáveis*. Mas não se pode reatribuir um objeto com variável `const`. Podemos usar a notação `.`ou `[]` junto com o operador `=` para atribuir um novo valor a uma propriedade. Se a propriedade já existir no objeto, o valor será atualizado. Caso contrário, uma nova propriedade será criada.
```js
pessoa.nome = "Ana Maria";
carro["Tipo de Combustivel"] = "Diesel";

const novaPessoa = {nome: "Ana Maria"};
novaPessoa = {nome: "Joana"}; // TypeError: Assignment to constant variable.
```

### Deletando Propriedades (*properties deletion*)
Para deletar uma propriedade de um objeto, usamos o operador `delete`.
```js
delete pessoa.nome;
delete carro["Tipo de Combustivel"];
```

### Acessando Propriedades de Objetos
Para acessar propriedades de um objeto, usamos o `.` ou `[]` para acessar o valor de uma propriedade.

## Métodos (*methods*)
Quando os dados armazenados em um objeto são uma função, chamamos isso de método.  
Uma `propriedade` é o que um objeto *tem*, enquanto um `método` é o que um objeto *faz*.  
Por exemplo: `console` é um objeto JavaScript global e `.log()` é um método nesse objeto. `Math`é objeto global e `.floor()`é o método.
Podemos incluir métodos em objetos literais usando a notação `key: value` comum. Ou podemos usar a notação `key() {/*corpo do método*/}` para criar métodos.
```js
const naveEspacial = {
  invade: function() { // notação com chave e valor
    console.log("Viemos dominar o planeta...");
  }
};
```
```js 
const naveEspacial = {
  invade() { // motação com a chave sendo a função
    console.log("Viemos dominar o planeta...");
  }
};

// chamando o método do objeto
naveEspacial.invade();
```

## Objetos aninhados
Objetos são frequentemente aninhados. Um objeto pode ter outro objeto como uma propriedade, que por sua vez pode ter uma propriedade que é um array de ainda mais objetos!
EXEMPLO:
```js
const naveEspacial = {
  telescopio: { 
    anoConstrucao: 2018,
    modelo: '91031-XLT',
    distanciaFocal: 2032
  },
  tripulacao: {
    capitao: {
      nome: "Sandra",
      formacao: "Engenharia de Computadores",
      incentivarTeam() { console.log("Nós ganhamos esse trabalho!"); }
    },
  },
  motor: {
    modelo: "Nimbus2000"
  },
  nanoelectronica: {
    computador: {
      terabytes: 100,
      monitores: "HD"
    },
    "back-up": {
      bateria: "Lithium",
      terabytes: 50
    }
  }
};
```
Podemos encadear operadores para acessar propriedades aninhadas:
```js
naveEspacial.nanoelectronica.["back-up"].bateria;
```

### Passando Objetos como Referência (*Pass By Reference*)
**Modificando Objetos com funções**  
*Quando objetos são passados por referência*. Uma `variável atribuída` a um objeto em uma função como `argumento`, o computador interpreta o nome do `parâmetro` como apontando para o espaço na memória que contém esse objeto. Como resultado, funções que alteram propriedades do objeto realmente mudam o objeto permanentemente (*mesmo quando o objeto é atribuído a uma variável `const`*).
```js
const naveEspacial = {
  planetaCasa: "Terra",
  cor: "prata"
};

let pintarPlaneta = obj => {
  obj.cor = "dourado glorioso"
};

pintarPlaneta(naveEspacial); // altera o objeto permanentemente
naveEspacial.cor;
```

### Reatribuindo Objetos (*reassigning objects*)
É possível reatribuir um objeto de uma variável `let`.
```js
let naveEspacial = {
  planetaCasa: "Terra",
  cor: "prata"
};

naveEspacial = {
    identificador: false,
    "tipo transporte": "voo"
} // Reatribuição regular - funciona
```
*Mas não é possível reatribuir um objeto através de uma função, **passando o objeto como parâmetro***. Quando passamos um objeto para uma função, o parâmetro recebe uma cópia do “endereço” onde o objeto está guardado na memória. Assim, *o parâmetro e a variável original são duas variáveis diferentes*, mas apontam para o mesmo objeto. Por isso, se a função alterar o conteúdo do objeto, a mudança aparece também fora da função. Mas se a função trocar o parâmetro por um objeto novo, isso não afeta a variável original, que continua apontando para o objeto antigo.
```js
let naveEspacial = {
  planetaCasa: "Terra",
  cor: "prata"
};

let pintarPlaneta = obj => {
  obj = {
    identificador: false,
    "tipo transporte": "voo"
  }
};

pintarPlaneta(naveEspacial); // A tentativa de reatribuição não funciona.
console.log(naveEspacial); // {planetaCasa: "Terra", cor: "prata"}
```

### Percorrendo Objetos em loop
Laços (loops) são ferramentas de programação que repetem um bloco de código até que uma condição seja satisfeita. Iteramos através de arrays usando sua indexação numérica, mas os pares chaves-valor em objetos não são ordenados. Para iterar sobre objetos o JavaScreipt oferece a sintaxe `for...in`.  
`for...in` executará um dado bloco de código para cada propriedade em um objeto.
Sintaxe:
```js
for (let propriedade in objeto) {
  // código a ser executado
};
```
EXEMPLO:
```js
const naveEspacial = {
  tripulacao: {
    capitao: {
      nome: "Sandra",
      formacao: "Engenharia de Computadores",
      incentivarTeam() { console.log("Nós ganhamos esse trabalho!"); }
    },
    engenheiro: {
      nome: "João",
      formacao: "Engenharia de Computadores",
      incentivarTeam() { console.log("Nós ganhamos esse trabalho!"); }
    },
    piloto: {
      nome: "Maria",
      formacao: "Engenharia de Computadores",
      incentivarTeam() { console.log("Nós ganhamos esse trabalho!"); }
    }
  }
};

for (let pessoa in naveEspacial.tripulacao) {
  console.log(`${pessoa}: ${naveEspacial.tripulacao[pessoa].nome}`);
}
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