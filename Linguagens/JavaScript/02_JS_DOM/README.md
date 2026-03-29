# Fase 2: JavaScript básico e ponte com a interface (DOM)

## Objetivo
Tornar a página interativa, lendo entradas e reagindo a ações do usuário.

## Conteúdo

### Sintaxe e variáveis
- Diferença entre `let` e `const`.
- Escopo de bloco.
- Controle de fluxo com `if/else`.
- Tratamento de erros com `try/catch`.
- Iteração com `for...of` e `for...in`.

### Manipulação do DOM
- Seleção de elementos:
  - `document.getElementById()`
  - `document.querySelector()`
- Leitura de valores:
  - `element.value`
  - `input.files`
- Alterações de interface:
  - `element.textContent`
  - `element.style.display`
  - ativar/desativar botões.

### Eventos
- Clique com `addEventListener('click', ...)`.
- Mudança em inputs com `addEventListener('change', ...)`.
- Organização de handlers em funções pequenas e reutilizáveis.

## Checklist
- [ ] Capturar todos os elementos de interface por `id`/`querySelector`
- [ ] Implementar leitura de valores digitados
- [ ] Implementar leitura de arquivo selecionado
- [ ] Exibir mensagens de status na tela
- [ ] Criar validações simples (campos obrigatórios)
- [ ] Tratar erros de forma clara com `try/catch`
- [ ] Conectar botões a funções por eventos

## Entregável da fase
Tela interativa com validações e fluxo de entrada funcionando, pronta para receber o motor de dados.
