## Tipos de dados (string, number, boolean, null, undefined)

## O que são?

Em JavaScript, tipo de dado é a categoria do valor que uma variável guarda. Cada tipo se comporta de forma diferente.

- `string`- texto : qualquer valor entre aspas
- `number`- número: inteiros, decimais, positivos e negativos
- `boolean`- verdadeiro ou falso: só tem dois valores possiveis
- `null`- ausência intencional de valor: definimos como `null`quando quer dizer "aqui não tem nada, de proposito"
- `undefined`- valor não definido: aparece quando uma variável foi criada mas nunca recebeu um valor
```js
let resultado;
console.log(resultado); // undefined
```

## Para que servem?
Cada tipo existe porque o computador precisa saber o que pode fazer com aquele valor: 
- `string`: juntar textos, exibir mensagens, capturar o que o usuário digitou
- `number`: fazer calculos, somar, multiplicar, comparar
- `boolean`: tomar decisões ("se logado, mostrar painel")
- `null` : indicar que algo ainda não foi preenchido/escolhido 
- `undefined`: sinalizar que uma variável ainda não tem valor
## Como usar (sintaxe)

```js
// string — use aspas (simples, duplas ou crase)
const nome = "Ana";
const sobrenome = 'Silva';
const frase = `Olá, ${nome}`; // crase permite inserir variáveis

// number — só escrever o número, sem aspas
const idade = 25;
const preco = 9.99;

// boolean — só true ou false, sem aspas
const ativo = true;
const bloqueado = false;

// null — atribuir explicitamente
let usuarioSelecionado = null;

// undefined — declarar sem atribuir valor
let resultado;
```

> Use `typeof` para descobrir o tipo de qualquer variável:
> ```js
> typeof "Ana"     // "string"
> typeof 25        // "number"
> typeof true      // "boolean"
> typeof null      // "object" ← peculiaridade histórica do JS
> typeof undefined // "undefined"
> ```

## Exemplos

### `string`
```js
const nome = "Ana";
const sobrenome = 'Silva';
const frase = `Olá, ${nome} ${sobrenome}!`;
// → "Olá, Ana Silva!"
```

### `number`
```js
const idade = 25;
const preco = 9.99;
const total = preco * 3;
// → 29.97
```

### `boolean`
```js
const estaLogado = true;
const temDesconto = false;

if (estaLogado) {
    console.log("Bem vindo!"); // executa porque é true
}
```

### `null`
```js
let usuarioSelecionado = null;
// ainda não escolheu nenhum usuário

usuarioSelecionado = "Ana";
// agora tem um valor
```

### `undefined`
```js
let desconto;
console.log(desconto); // undefined — nunca recebeu valor

desconto = 10;
console.log(desconto); // 10
```

## Onde usei no meu codigo

### `string` — texto
```js
let globalExtractedText = '';
// string vazia, depois recebe o texto do PDF

const mode = document.querySelector('input[name="mode"]:checked').value;
// guarda "v1" ou "v2" — texto vindo do HTML

lbl.textContent = 'Carregando documento...';
// string usada para exibir mensagem na tela
```

### `number` — número
```js
const totalPages = endPage - startPage + 1;
// resultado de cálculo numérico

let startPage = parseInt(document.getElementById('pageStart').value) || 1;
// converte o texto do input para número
```

### `boolean` — verdadeiro ou falso
```js
const isOffDay = /FOLGA|DSR|FERIADO/i.test(l);
// true se o dia for folga, false se não for

const todayOdd = today.times.length % 2 !== 0;
// true se o dia tiver batida ímpar (falta saída)

btnProcess.disabled = true;
// true = botão bloqueado durante o processamento
```

### `null` — ausência intencional de valor
```js
let bestPeriod = null;
// ainda não encontrou o melhor período — definido como null de propósito

let lastY = null;
// ainda não leu nenhuma linha do PDF
```

### `undefined` — aparece sozinho sem valor
```js
// Não aparece diretamente, mas ocorreria se tentasse acessar
// uma propriedade que não existe, ex:
fileInput.files[0]
// se nenhum arquivo foi selecionado, retorna undefined
```


