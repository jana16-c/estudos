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
