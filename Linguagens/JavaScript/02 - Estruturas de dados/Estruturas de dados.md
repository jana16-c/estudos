## Estruturas de dados 

## Arrays

## O que são?
Arrays (ou Vetores) são listas ordenadas de dados. Imagine uma prateleira onde cada item tem um número (índice) começando sempre do **0**. No JavaScript, um array pode guardar qualquer tipo de dado, inclusive outros arrays ou objetos.

## Para que servem
Servem para agrupar múltiplos valores sob um único nome. Em vez de criar `batida1`, `batida2`, `batida3`, você cria um array `batidas`.

Os métodos especiais facilitam o trabalho:
- **map**: Transforma cada item da lista e gera uma lista nova.
- **filter**: Filtra a lista com base em uma condição.
- **find**: Procura um item específico na lista.
- **reduce**: Reduz a lista inteira a um único valor (ex: somar tudo).

## Como usar (sintaxe)
```js
const frutas = ["Maçã", "Banana", "Uva"];
console.log(frutas[0]); // "Maçã"

// Métodos comuns
frutas.push("Laranja"); // Adiciona ao fim
const temUva = frutas.find(f => f === "Uva"); 
```

## Exemplos
```js
const numeros = [10, 20, 30, 40];

// Dobrar os números (map)
const dobros = numeros.map(n => n * 2); // [20, 40, 60, 80]

// Apenas maiores que 25 (filter)
const grandes = numeros.filter(n => n > 25); // [30, 40]
```

## Onde usei no meu codigo
**1. `.map()` para aplicar intervalos:**
```js
return timeline.map(day => ({
    ...day,
    times: addMealIntervalTimes(day.times, intervalMinutes)
}));
// Transforma cada objeto "dia" dentro do array "timeline".
```

**2. `.find()` para evitar duplicados:**
```js
const existingDay = globalMap[currentName].find(d => d.data.getTime() === entryDate.getTime());
// Procura se a data já existe na lista antes de adicionar uma nova.
```

**3. `.sort()` para organizar datas:**
```js
let tl = (dataMap[name] || []).slice().sort((a, b) => a.data - b.data);
// Garante que as batidas apareçam em ordem cronológica.
```


## Objetos (acesso, modificação, destructuring)

## O que são?
Objetos são coleções de propriedades (chave e valor). Se o Array é uma lista, o Objeto é uma ficha cadastral ou um dicionário. 

## Para que servem
Servem para representar entidades do mundo real ou agrupar informações que descrevem uma coisa só (ex: um Funcionário tem nome, registro e batidas).

## Como usar (sintaxe)
```js
const usuario = {
    nome: "Lucas",
    idade: 20
};

// Acesso
console.log(usuario.nome); // Ponto
console.log(usuario["nome"]); // Colchetes

// Destructuring (Desestruturação) - Extrair valores de forma limpa
const { nome, idade } = usuario;
```

## Exemplos
```js
// Modificação
usuario.idade = 21;
usuario.cidade = "Ipatinga"; // Adiciona nova propriedade

// Spread Operator (...) - Copiar objeto mudando algo
const usuarioAtualizado = { ...usuario, idade: 22 };
```

## Onde usei no meu codigo
**1. Criação de modelos de dados:**
```js
const entry = {
    data: entryDate, 
    times: realTimes, 
    isOffDay: isOffDay
};
// Agrupa todas as informações de um dia de trabalho em uma única "ficha".
```

**2. Destructuring em Strings:**
```js
const [h, m] = t.split(':');
// O split gera um array ['08', '30'], e o destructuring joga '08' em h e '30' em m.
```

**3. Objetos como Mapas (Lookups):**
```js
const map = {};
map[globalName] = []; 
// Usa o nome do funcionário como chave para encontrar seus dados rapidamente.
```