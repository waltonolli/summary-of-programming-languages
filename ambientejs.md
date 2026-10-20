# JavaScript Runtime Environments(ambientes de execução)

O ambiente de execução é onde seu programa será executado. Ele determina quais objetos globais seu programa pode acessar e também pode impactar a forma como ele é executado.

## Ambiente de execução de um navegador (Chrome, Firefox, Safari, Opera, etc.)
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

## Ambiente de execução do Node.js
Em 2009, o ambiente de execução Node.js foi criado com o objetivo de executar código JavaScript sem um navegador, permitindo assim que os programadores criassem aplicações completas (front-end e back-end) usando apenas a linguagem JavaScript. O Node.js é executado no servidor e não no navegador.  
O ambiente de execução do Node.js oferece aos aplicativos de back-end acesso a uma variedade de recursos indisponíveis em um navegador, como acesso ao sistema de arquivos, banco de dados e rede do servidor.

## Módulos
Módulos são trechos de código reutilizáveis ​​em um arquivo que podem ser exportados e importados para uso em outro arquivo. Um programa modular é aquele cujos componentes podem ser separados, usados ​​individualmente e recombinados para criar um sistema complexo.  
<img src="https://static-assets.codecademy.com/Courses/Learn-JavaScript/Modules/modular-program-diagram.svg" alt="diagrama de um módulo" width="300">


