## Módulos (import/export)

## O que são
Módulos são uma forma de dividir o código JavaScript em arquivos separados. Cada arquivo é um "módulo" independente que pode exportar funcionalidades (variáveis, funções, classes) para outros arquivos utilizarem.

## Para que servem
Servem para manter o projeto organizado, evitar conflitos de nomes de variáveis globais e permitir o reaproveitamento de lógica em diferentes partes da aplicação sem duplicar código.

## Como usar
No arquivo que envia (origem): `export const minhaFuncao = ...`  
No arquivo que recebe (destino): `import { minhaFuncao } from './caminho/arquivo.js'`  
*Nota: O HTML precisa declarar o script com `type="module"`.*

## Exemplos
```js
// Arquivo: mathUtils.js
// O 'export' torna esta função visível para outros arquivos
export const somar = (a, b) => a + b;

// Arquivo: app.js
// O 'import' traz a funcionalidade específica que precisamos
import { somar } from './mathUtils.js';

console.log(somar(10, 5)); // 15
```

## Onde usei no meu código
**1. Separação da lógica de extração:**
```js
// No arquivo 'parser.js', exporto a função principal de leitura
export async function extrairDadosDoPDF(pdf) { ... }

// No arquivo 'main.js', importo para usar no evento de clique
import { extrairDadosDoPDF } from './parser.js';
```


## Separação de tarefas

## O que são
É o princípio de design de software conhecido como **Separation of Concerns (SoC)**. Consiste em dividir o programa em seções distintas, onde cada seção aborda uma preocupação/responsabilidade específica.

## Para que servem
Facilita a manutenção (se o erro está no visual, você mexe na UI; se o erro está no cálculo, você mexe no Processamento) e torna o código muito mais fácil de testar.

## Como usar
Divida sua lógica em três camadas principais:
1. **UI/Eventos:** Lida com cliques e manipulação do DOM.
2. **Processamento (Business Logic):** Lida com cálculos e limpeza de dados.
3. **Utilidades:** Funções genéricas de apoio.

## Exemplos
```js
// Responsabilidade 1: Capturar dados da tela (UI)
const obterValorInput = () => document.getElementById('entrada').value;

// Responsabilidade 2: Processar lógica (Negócio)
const calcularDesconto = (valor) => valor * 0.10;

// Responsabilidade 3: Mostrar resultado (UI)
const mostrarNaTela = (res) => document.getElementById('saida').innerText = res;
```

## Onde usei no meu código
No projeto do PDF, separei assim:
- **Função A:** Apenas lê o arquivo binário (FileReader).
- **Função B:** Apenas percorre as páginas do PDF (Iteração).
- **Função C:** Apenas limpa o texto bruto usando Regex (Parsing).
- **Função D:** Apenas cria as linhas da tabela HTML (Renderização).


## Funções reutilizáveis

## O que são
São funções "puras" ou genéricas que realizam uma tarefa comum e não dependem de variáveis globais ou do estado específico de uma tela para funcionar.

## Para que servem
Evitar a repetição de código (princípio **DRY - Don't Repeat Yourself**). Se você precisa formatar uma data em três lugares diferentes, cria uma função única para isso.

## Como usar
Crie uma pasta `utils/` e coloque funções que recebem uma entrada e retornam uma saída previsível.

## Exemplos
```js
// Uma função que limpa espaços extras de qualquer string
const limparTexto = (texto) => texto.trim().replace(/\s+/g, ' ');

// Pode ser usada para nomes de usuários, endereços ou conteúdo de PDF
const nomeLimpo = limparTexto("  João   Silva  "); 
```

## Onde usei no meu código
**1. Conversão de horas:**
```js
function toMin(str) {
    // Esta função é usada em vários pontos do processamento de ponto
    // para transformar "08:30" em 510 minutos para cálculos matemáticos.
    if (!str) return 0;
    const [horas, minutos] = str.split(':').map(Number);
    return (horas * 60) + minutos;
}
```


## Estrutura do projeto

## O que são
É a organização física (pastas e arquivos) do seu ambiente de trabalho.

## Para que servem
Permite que qualquer desenvolvedor (ou você mesmo no futuro) entenda onde encontrar cada parte do código rapidamente, além de facilitar o deploy e a escalabilidade.

## Como usar
Siga um padrão de pastas lógico, separando arquivos de estilo, lógica e bibliotecas externas.

## Exemplos
```text
projeto-pdf/
├── index.html          # Entrada principal
├── css/
│   └── styles.css      # Estilização
├── js/
│   ├── main.js         # Orquestrador (liga UI ao Parser)
│   ├── parser.js       # Lógica de extração do PDF
│   ├── ui.js           # Manipulação de DOM/Tabelas
│   └── utils/
│       └── dateHelper.js # Funções de tempo e data
└── vendor/             # Bibliotecas (ex: pdf.js)
```

## Onde usei no meu código
Apliquei essa estrutura para garantir que o arquivo `main.js` não ficasse com mais de 500 linhas, movendo a lógica pesada de Regex para o `parser.js`.
