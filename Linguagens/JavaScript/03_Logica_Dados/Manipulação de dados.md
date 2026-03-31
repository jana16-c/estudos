## Manipulação de Dados

## Strings (split, replace, etc.)
## Como usar (sintaxe)
Strings são sequências de caracteres. O JavaScript oferece métodos para limpar, cortar e transformar esses textos.
```js
texto.trim();              // Remove espaços nas pontas
texto.split('\n');         // Transforma uma string em um Array separando por quebras de linha
texto.replace('A', 'B');   // Troca o primeiro 'A' por 'B' (ou todos se usar Regex /A/g)
texto.toUpperCase();       // Deixa tudo em MAIÚSCULO
```

## Exemplos
```js
const linha = "   01/01/2024 - Segunda   ";
const limpa = linha.trim(); // "01/01/2024 - Segunda"
const partes = limpa.split(" - "); // ["01/01/2024", "Segunda"]
```

## Onde usei no meu código
**1. Normalização de texto:**
```js
const normalizedText = text.replace(/\r/g, '').replace(/\u00A0/g, ' ');
// Usei para remover caracteres invisíveis que vêm do PDF e quebram a busca.
```
**2. Limpeza de nomes:**
```js
let raw = mName[2].trim().replace(/^\d+\s*-\s*/, '').trim();
// Remove o número da matrícula e espaços extras do nome do funcionário.
```

## Expressões Regulares (Regex básico)
## Como usar (sintaxe)
Regex são padrões usados para encontrar combinações de caracteres em strings. São declaradas entre barras `/padrão/`.
```js
/abc/.test(texto);    // Retorna true ou false
texto.match(/abc/g);  // Retorna um array com todas as ocorrências
```

## Exemplos
```js
const temHora = /\d{2}:\d{2}/.test("Entrada às 08:00"); // true
const soNumeros = "Nota 10".match(/\d+/); // ["10"]
```

## Onde usei no meu código
**1. Captura de períodos:**
```js
const rgPeriod = /Per[ií]odo\s*de\s*(\d{2})\.(\d{2})\.(\d{4})/i;
// Identifica a data de início da apuração no cabeçalho do PDF.
```
**2. Extração de horários de batida:**
```js
const allTimes = l.match(/\d{2}:\d{2}/g) || [];
// Pega todos os formatos de hora (ex: 08:00, 12:00) presentes em uma linha.
```

## Loops (for, for...of, forEach)
## Como usar (sintaxe)
Estruturas de repetição para percorrer listas de dados.
```js
for (let i = 0; i < arr.length; i++) { ... } // Tradicional (controle total)
for (const item of arr) { ... }              // Mais limpo para ler itens
arr.forEach(item => { ... });                // Executa uma função para cada item
```

## Exemplos
```js
const lista = ["Página 1", "Página 2"];
for (const p of lista) {
    console.log(p);
}
```

## Onde usei no meu código
**1. Percorrendo linhas do texto:**
```js
for (const rawLine of lines) {
    const l = rawLine.trim();
    if (!l) continue; // Pula linhas vazias
}
```

## JSON (parse, stringify)
## Como usar (sintaxe)
Formato de intercâmbio de dados. `parse` transforma texto em objeto, `stringify` transforma objeto em texto.
```js
const objeto = JSON.parse(textoJSON);
const texto = JSON.stringify(objeto);
```

## Exemplos
```js
const config = '{"tema": "dark"}';
const obj = JSON.parse(config);
console.log(obj.tema); // "dark"
```

## Onde usei no meu código
*Nota: No momento o projeto usa objetos em memória, mas o JSON será essencial para implementar a funcionalidade de "Salvar Configurações" ou "Exportar Relatório" no futuro.*

## Datas (Date, manipulação de horários)
## Como usar (sintaxe)
O objeto `Date` lida com momentos no tempo. Lembre-se: meses no JS começam em **0** (Janeiro).
```js
new Date(ano, mes, dia);
data.getTime(); // Retorna o tempo em milissegundos (ótimo para comparar)
```

## Exemplos
```js
const hoje = new Date(2024, 0, 1); // 1º de Jan de 2024
const amanha = new Date(hoje.getTime() + 86400000); // Soma 24h em ms
```

## Onde usei no meu código
**1. Criação de datas para o modelo:**
```js
const entryDate = new Date(realYear, realMonth - 1, day);
// Converte os números extraídos do PDF em um objeto Date real.
```
**2. Cálculo de "virada de dia" (Meia-noite):**
```js
if (adjustedFirstTomorrowMin < (lastTodayMin % 1440)) {
    adjustedFirstTomorrowMin += 1440;
}
// Lógica para entender que 01:00 após as 23:00 pertence ao turno anterior.
```

## Tratamento de erro (try/catch)
## Como usar (sintaxe)
Evita que o programa pare de funcionar se algo der errado.
```js
try {
    // código perigoso
} catch (error) {
    // o que fazer se der erro
}
```

## Exemplos
```js
try {
    processarArquivo();
} catch (e) {
    console.error("Falha ao abrir: " + e.message);
}
```

## Onde usei no meu código
**1. No processamento do PDF:**
```js
try {
    const pdf = await pdfjsLib.getDocument({ data: arrayBuffer }).promise;
} catch (e) {
    showError('Erro ao processar arquivo: ' + e.message);
}
// Garante que se o PDF estiver corrompido, o usuário receba um aviso em vez da tela travar.
```