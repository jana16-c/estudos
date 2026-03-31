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


## Operadores (+, -, ===, !==, etc.)

## O que são?

Operadores são símbolos especiais que usamos para executar operações em variáveis e valores. Eles permitem realizar cálculos matemáticos, comparar dados, atribuir valores e criar lógicas condicionais.

Pense neles como os "verbos" ou "ações" que conectam os seus dados (substantivos).


## Para que servem?
Eles são essenciais para:
- **Aritmética:** Calcular valores (soma, subtração, etc).
- **Atribuição:** Guardar valores dentro de variáveis.
- **Comparação:** Verificar se valores são iguais, diferentes, maiores ou menores.
- **Lógica:** Combinar múltiplas condições (ex: "se o usuário está logado e tem permissão").
- **Manipulação de Strings:** Unir textos.


## Como usar (sintaxe)
A maioria dos operadores fica entre dois valores (operandos):
```js
let soma = 10 + 5; // O '+' é o operador, 10 e 5 são operandos.
```

### Principais Categorias:

1. **Aritméticos:** `+`, `-`, `*`, `/`, `%` (resto), `**` (potência).
2. **Atribuição:** `=`, `+=`, `-=`, `*=`.
3. **Comparação:** 
   - `===` Igualdade estrita (valor e tipo).
   - `!==` Desigualdade estrita.
   - `>`, `<`, `>=`, `<=`.
4. **Lógicos:** `&&` (E), `||` (OU), `!` (NÃO/Negação).
5. **Modernos/Avançados:**
   - `? :` Ternário (Condicional compacta).
   - `??` Nullish Coalescing (Tratamento de nulos).
   - `?.` Optional Chaining (Acesso seguro a objetos).
   - `&&=` / `||=` Atribuição lógica.


## Exemplos

```js
// Aritmética e Atribuição
let total = 10;
total += 5; // Mesma coisa que total = total + 5 (Resultado: 15)
```

```js
// Comparação Estrita (Sempre prefira === e !==)
console.log(10 === "10"); // false (tipos diferentes: número vs string)
console.log(10 == "10");  // true (evite isso, o JS tenta converter os tipos sozinho)
```
```js
// Lógicos
const temIdade = true;
const temDocumento = false;
const podeEntrar = temIdade && temDocumento; // false
```

---

## Características importantes

- **Precedência:** Assim como na matemática, a multiplicação `*` e divisão `/` acontecem antes da soma `+` e subtração `-`. Use parênteses `()` para forçar a ordem desejada.
- **Coerção de Tipo:** O operador `+` se comporta de forma diferente com textos. `5 + 5` é `10`, mas `"5" + 5` é `"55"` (ele concatena os valores como texto).
- **Operadores de Curto-circuito:** O operador `||` (OU) pode ser usado para definir valores padrão. Se o primeiro valor for "falso" (null, undefined, 0), ele pega o segundo.

---

## Onde usei no meu código

**1. Operadores Aritméticos (Cálculo de intervalo):**
```js
const totalPages = endPage - startPage + 1;
// Usado para descobrir a quantidade de páginas a partir do range fornecido.
```

**2. Operador de Curto-circuito (Valor padrão):**
```js
let startPage = parseInt(document.getElementById('pageStart').value) || 1;
// Se o campo estiver vazio ou o resultado for NaN, o operador || garante que startPage seja 1.
```

**3. Comparação Estrita e Resto da Divisão (Lógica de batidas):**
```js
const todayOdd = today.times.length % 2 !== 0;
// % 2 pega o resto da divisão por 2. 
// !== 0 verifica se é diferente de zero (ou seja, ímpar).
```

**4. Atribuição Composta (Acumular texto):**
```js
extractedText += pageText + '\n\n';
// += adiciona o conteúdo da nova página ao que já existia na variável.
```

**5. Operadores Lógicos em Regex:**
```js
const isOffDay = /FOLGA|DSR|FERIADO/i.test(l);
// Embora seja uma Regex, o símbolo | funciona logicamente como um "OU" dentro do padrão de busca.
```
## Condicionais (if, else, switch)

## O que são?

Condicionais são estruturas de controle que permitem ao seu programa tomar decisões. Elas avaliam se uma expressão é verdadeira (`true`) ou falsa (`false`) e, com base nisso, executam blocos de código diferentes. 

É o famoso "Se acontecer isso, faça aquilo".


## Para que servem?
Servem para criar lógica e inteligência no software. Sem condicionais, o código seria apenas uma lista linear de instruções. Com elas, você pode:
- **Validar dados:** Impedir que o programa continue se o usuário não selecionou um arquivo.
- **Tratar exceções:** Evitar erros se uma página do PDF estiver em branco.
- **Alternar comportamentos:** Escolher entre o Motor V1 ou V2 baseado na escolha do usuário.
- **Personalizar a interface:** Mudar cores ou textos dependendo do estado do processamento.


## Como usar (sintaxe)

### Principais Categorias:

**1. `if` / `else if` / `else`**
A forma mais comum para testar condições variadas.
```js
if (condicao) {
  // executa se for true
} else if (outraCondicao) {
  // executa se a primeira for false e esta for true
} else {
  // executa se nenhuma for true
}
```

**2. `switch`**
Ideal para comparar uma única variável com vários valores fixos.
```js
switch (opcao) {
  case 'v1': /* código */ break;
  case 'v2': /* código */ break;
  default:   /* caso padrão */
}
```

**3. Operador Ternário**
Uma forma curta de escrever um `if/else` para atribuição de valores.
```js
const status = (media >= 7) ? "Aprovado" : "Reprovado";
```

## Exemplos

```js
const temperatura = 30;

if (temperatura > 35) {
    console.log("Muito quente!");
} else if (temperatura > 20) {
    console.log("Agradável.");
} else {
    console.log("Frio.");
}
```


## Características importantes
- **Falsy Values:** No JavaScript, valores como `0`, `""` (string vazia), `null`, `undefined` e `NaN` são considerados `false` em uma condicional.
- **Curto-circuito:** Se você usar `if (A || B)`, e o `A` for verdadeiro, o JavaScript nem olha o `B`.
- **Escopo:** Variáveis criadas com `let` ou `const` dentro de um `if` só existem dentro dele.


## Onde usei no meu código

**1. Validação de segurança (`if` simples):**
```js
if (!file) {
    showError('Selecione o arquivo PDF do espelho de ponto para processar.');
    return; // O return interrompe a função se a condição for verdadeira
}
```

**2. Alternância de Interface (`if / else`):**
```js
if (mode === 'v2') {
    titleEl.textContent = 'Processador de ponto - Usiminas (V2)';
} else {
    titleEl.textContent = 'Processador de ponto - Usiminas (Padrão)';
}
```

**3. Lógica de extração (Operador Ternário):**
```js
const dataMap = (mode === 'v1') ? parseInputV1(rawData) : parseInputV2(rawData);
// Define qual função de "parse" chamar dependendo do modo ativo.
```

**4. Controle de UI durante o Loop:**
```js
if ((i - startPage) % 5 === 0) {
    await new Promise(r => setTimeout(r, 0));
}
// "Se o resto da divisão por 5 for zero (a cada 5 páginas), faça uma pequena pausa". 
// Isso evita que o navegador trave a interface durante a leitura do PDF.
```

**5. Verificação de batidas ímpares:**
```js
if (isOdd) tr.classList.add('row-odd');
// Se o dia tiver batidas faltando (ímpar), adiciona uma classe CSS de alerta.
```
## Funções (tradicionais e arrow functions)

## O que são?
Funções são blocos de construção fundamentais no JavaScript. Elas são conjuntos de instruções que executam uma tarefa específica ou calculam um valor. Você "empacota" um trecho de código para que ele possa ser executado sempre que você precisar, chamando-o pelo nome.

## Para que servem?
- **Reutilização:** Escreva a lógica uma vez (ex: converter horas em minutos) e use-a em vários lugares.
- **Organização:** Divide um problema complexo em partes menores e fáceis de gerenciar (modularização).
- **Abstração:** Permite que você use um código sabendo *o que* ele faz, sem precisar se preocupar com o *como* ele faz internamente o tempo todo.

## Como usar (sintaxe)

### 1. Função Tradicional (Declaração)
```js
function nomeDaFuncao(parametro1, parametro2) {
    // código a ser executado
    return resultado; // opcional
}
```

### 2. Arrow Functions (Seta)
Uma forma mais curta e moderna de escrever funções, muito comum no código atual.
```js
const minhaFuncao = (parametro) => {
    return parametro * 2;
};
// Se tiver apenas uma linha e um retorno, pode ser ainda mais curta:
const dobro = n => n * 2;
```

## Exemplos
```js
// Função simples com retorno
function saudar(nome) {
    return `Olá, ${nome}!`;
}

const mensagem = saudar("Colaborador"); // "Olá, Colaborador!"
```

---

## Características importantes
- **Parâmetros e Argumentos:** Parâmetros são os nomes na definição da função. Argumentos são os valores reais que você passa ao chamá-la.
- **Escopo:** Variáveis criadas dentro de uma função são "privadas" a ela.
- **Retorno (`return`):** É o valor que a função "entrega" de volta. Se não houver um `return`, a função retorna `undefined`.
- **Async/Await:** Funções marcadas com `async` permitem lidar com processos que demoram (como ler arquivos) sem travar o navegador.

## Onde usei no meu codigo

**1. Função Tradicional de Utilidade (Lógica):**
```js
function toMin(str) {
    if (!str) return 0;
    const parts = str.split(':');
    return parseInt(parts[0], 10) * 60 + parseInt(parts[1], 10);
}
// Aqui, 'str' é o parâmetro. A função transforma texto em números para cálculos.
```

**2. Função Assíncrona (`async`):**
```js
async function processPDF() {
    const arrayBuffer = await file.arrayBuffer();
    const pdf = await pdfjsLib.getDocument({ data: arrayBuffer }).promise;
    // Usamos 'async' porque a leitura do PDF não é instantânea.
}
```

**3. Arrow Function como Callback (Eventos):**
```js
btn.addEventListener('click', async () => {
    try { await navigator.clipboard.writeText(tsv); }
    catch(e) { /* tratamento de erro */ }
});
// A arrow function anônima () => { ... } é executada apenas quando o botão é clicado.
```

**4. Funções chamando outras funções:**
```js
function updateMode() {
    const mode = document.querySelector(...).value;
    processTextData(globalExtractedText, mode, mealIntervalStr);
}
// updateMode organiza a interface e delega o processamento pesado para processTextData.
```