# Roteiro de Estudos em JavaScript

## Como estudar cada tópico

Para cada item abaixo, documentar seguindo este padrão:

- O que é
- Para que serve
- Como usar (sintaxe básica)
- Exemplos simples
- Características importantes
- Onde usei no meu código (projeto real)

---

## 1. Fundamentos

- [ ] Variáveis (`let`, `const`, `var`)
  - Por quê: controlar armazenamento de dados corretamente evita bugs e confusão de escopo.

- [ ] Tipos de dados (string, number, boolean, null, undefined)
  - Por quê: entender tipos evita erros de comparação e manipulação.

- [ ] Operadores (`+`, `-`, `===`, `!==`, etc.)
  - Por quê: base de qualquer lógica e comparação.

- [ ] Condicionais (`if`, `else`, `switch`)
  - Por quê: controlar decisões no código.

- [ ] Funções (tradicionais e arrow functions)
  - Por quê: organizar lógica e reutilizar código.

---

## 2. Estruturas de Dados

- [ ] Arrays (`map`, `filter`, `reduce`, `find`)
  - Por quê: manipular listas de dados (essencial para qualquer projeto).

- [ ] Objetos (acesso, modificação, destructuring)
  - Por quê: representar dados estruturados.

---

## 3. Manipulação de Dados

- [ ] Strings (`split`, `replace`, etc.)
  - Por quê: extrair e limpar dados (muito importante para parsing).

- [ ] Expressões Regulares (Regex básico)
  - Por quê: encontrar padrões em textos complexos.

- [ ] Loops (`for`, `for...of`, `forEach`)
  - Por quê: percorrer dados e aplicar regras.

- [ ] JSON (`parse`, `stringify`)
  - Por quê: trabalhar com dados estruturados.

- [ ] Datas (`Date`, manipulação de horários)
  - Por quê: essencial para sistemas com tempo.

- [ ] Tratamento de erro (`try/catch`)
  - Por quê: evitar que o sistema quebre silenciosamente.

---

## 4. Assincronismo

- [ ] Promises (`then`, `catch`)
  - Por quê: lidar com operações que demoram.

- [ ] `async/await`
  - Por quê: escrever código assíncrono de forma mais clara.

- [ ] Requisições HTTP (`fetch`)
  - Por quê: acessar APIs externas.

---

## 5. Organização de Código

- [ ] Módulos (`import` / `export`)
  - Por quê: dividir código em partes reutilizáveis.

- [ ] Separação de responsabilidades
  - Por quê: manter código organizado.

- [ ] Funções reutilizáveis
  - Por quê: evitar repetição.

- [ ] Estrutura de projeto
  - Por quê: facilitar crescimento do sistema.

---

## 6. Node.js

- [ ] Leitura de arquivos (`fs`)
  - Por quê: trabalhar com arquivos locais.

- [ ] Scripts automatizados
  - Por quê: automatizar tarefas repetitivas.

---

## 7. DOM

- [ ] Seleção de elementos (`querySelector`)
  - Por quê: acessar elementos da página.

- [ ] Eventos (`click`, `input`)
  - Por quê: interagir com o usuário.

- [ ] Manipulação de conteúdo
  - Por quê: exibir resultados.

---

## 8. Banco de Dados

- [ ] SQL básico (`SELECT`, `WHERE`, `GROUP BY`)
  - Por quê: consultar dados.

- [ ] Integração com JavaScript
  - Por quê: persistir informações.

---

## 9. Avançado

- [ ] `Map` e `Set`
  - Por quê: melhorar organização e performance.

- [ ] Programação funcional
  - Por quê: escrever código mais previsível.

- [ ] Testes básicos
  - Por quê: garantir funcionamento correto.

---

## Exemplo de preenchimento (Arrays)

### O que é
Estrutura de dados que armazena uma lista de valores.

### Para que serve
Guardar e manipular conjuntos de dados.

### Como usar
```js
const lista = [1, 2, 3];
