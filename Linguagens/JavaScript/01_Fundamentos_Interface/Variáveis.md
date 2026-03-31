## Variavéis

## O que são?

Variáveis são espaços na memória do computador onde você guarda um valor e o acessa pelo nome.

Pense como uma caixa com etiqueta:

No código:
```js
let nome = "Ana";   // cria a caixa "nome" com o valor "Ana"
let idade = 25;     // cria a caixa "idade" com o valor 25

console.log(nome);  // "Ana"
console.log(idade); // 25
```
O programa pode consultar ou alterar esse valor a qualquer momento pelo identificador (o nome da variável) — sem precisar saber onde exatamente está na memória.

## Para que servem?

Variáveis servem para armazenar e reutilizar valores ao longo do código. Com elas você pode:

- Guardar dados do usuário (nome, idade, email)
- Armazenar resultados de cálculos
- Controlar o estado da aplicação (ex: usuário logado ou não)
- Passar informações entre diferentes partes do código
---
## Como usar (sintaxe)

Em JavaScript há três formas de declarar variáveis:

- `let` — valor pode mudar
- `const` — valor não pode ser reatribuído
- `var` — forma antiga (evitar em código moderno)

Regra prática: use `const` por padrão. Se precisar reatribuir, use `let`. Evite var.

## Exemplos

Regras de nomenclatura (identificadores)

- Deve começar com letra, `_` ou `$`
- Pode conter letras, números, `_` e `$`
- Não pode conter espaço
- Não pode começar com número
- É case-sensitive: nome ≠ Nome

Outros exemplos 
```js
// Texto (string)
const cidade = "São Paulo";
const saudacao = "Olá, mundo!";

// Número
let placar = 0;
placar = placar + 1; // agora vale 1

// Verdadeiro ou falso (boolean)
const estaLogado = true;
const temDesconto = false;

// Reutilizando em uma frase
const nome = "Lucas";
const idade = 20;
console.log(nome + " tem " + idade + " anos.");
// → "Lucas tem 20 anos."

// Resultado de cálculo
const preco = 10;
const quantidade = 3;
const total = preco * quantidade;
console.log(total); // → 30
```

## Onde usei no meu codigo

Lembrando que 

`let`- o valor muda ao longo do código

`const`- valor não muda após ser definido

**1. `let` — acumulando texto página a página:**
```js
let extractedText = '';
// começa vazia

extractedText += pageText + '\n\n';
// a cada página lida do PDF, o texto é adicionado à variável
```

**2. `let` — valor corrigido após ser definido:**
```js
let startPage = parseInt(document.getElementById('pageStart').value) || 1;
// guarda a página inicial que o usuário digitou no campo

if (startPage < 1) startPage = 1;
// se digitou um número inválido (ex: 0 ou negativo), corrige para 1
```

**3. `const` — guardando resultado de cálculo:**
```js
const totalPages = endPage - startPage + 1;
// guarda o total de páginas a processar
// usado depois para calcular o % da barra de progresso
```