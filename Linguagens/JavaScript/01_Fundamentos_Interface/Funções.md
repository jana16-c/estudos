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