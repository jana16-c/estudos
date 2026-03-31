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
