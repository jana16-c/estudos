## Promises (then, catch, finally)

## O que são
Promises (Promessas) são objetos que representam o sucesso ou a falha eventual de uma operação assíncrona. Imagine como um "vale-brinde": você não tem o item agora, mas tem a promessa de que ele chegará.

## Para que servem
Servem para gerenciar operações que levam tempo (como ler arquivos ou acessar APIs) sem travar a execução do restante do código, evitando o antigo "Callback Hell" (funções dentro de funções).

## Como usar
```js
minhaPromise
  .then(resultado => { 
    // Executado quando a Promise passa para o estado "fulfilled" (sucesso)
  })
  .catch(erro => { 
    // Executado se a Promise for "rejected" (erro/falha)
  })
  .finally(() => { 
    // Executado sempre ao final, útil para fechar 'loaders' ou limpar memória
  });
```

## Exemplos
```js
// Criando uma função que retorna uma Promise
const esperar = tempo => new Promise(resolve => {
    // resolve é uma função que marca a Promise como "sucesso"
    // setTimeout executa uma função após um determinado tempo (em milissegundos)
    setTimeout(resolve, tempo);
});

// Usando a Promise com .then() e .catch()
esperar(2000)
    .then(() => {
        // Este bloco executa quando a Promise é "fulfilled" (resolvida com sucesso)
        console.log("Passaram-se 2 segundos");
    })
    .catch((erro) => {
        // Este bloco executa se houver um erro (Promise "rejected")
        console.error("Algo deu errado:", erro);
    })
    .finally(() => {
        // Este bloco SEMPRE executa, independente de sucesso ou erro
        // Útil para limpar recursos ou fechar animações de carregamento
        console.log("Operação finalizada");
    });
```

## Onde usei no meu código
**1. Carregamento do PDF:**
```js
// Requisição assíncrona para carregar o PDF
const loadingTask = pdfjsLib.getDocument({ data: arrayBuffer });

loadingTask.promise
    .then(pdf => {
        // Quando o PDF for carregado com sucesso
        console.log('PDF carregado com sucesso');
        console.log('Total de páginas:', pdf.numPages);
        return pdf; // Retornar para usar em outro .then() se necessário
    })
    .catch(erro => {
        // Se falhar no carregamento
        console.error('Erro ao carregar PDF:', erro);
    });
// A biblioteca pdf.js utiliza Promises para lidar com o processamento binário do documento.
```


## Async/Await

## O que são
É uma sintaxe moderna (açúcar sintático) para trabalhar com Promises. Ela permite escrever código assíncrono que parece e se comporta como código síncrono.

## Para que servem
Tornar o código mais legível e facilitar o tratamento de erros usando blocos `try/catch` tradicionais, em vez de encadear múltiplos `.then()`.

## Como usar
```js
// Versão tradicional com .then() (menos legível)
function pegarDados_ComThen() {
    return fetch('https://api.exemplo.com/dados')
        .then(resposta => resposta.json())
        .then(dados => {
            console.log('Dados recebidos:', dados);
            return dados;
        });
}

// Versão moderna com async/await (mais legível e recomendada)
async function pegarDados() {
    try {
        // await pausa a execução até a Promise ser resolvida
        const resposta = await fetch('https://api.exemplo.com/dados');
        
        // Aguarda a conversão da resposta para JSON
        const dados = await resposta.json();
        
        console.log('Dados recebidos:', dados);
        return dados;
        
    } catch (e) {
        // Captura ANY erro que ocorrer no bloco try
        console.error('Erro ao buscar dados:', e);
        return null; // Retorna null em caso de erro
    }
}
```

## Exemplos
```js
// Exemplo prático com CEP (API ViaCEP)
async function buscarEndereco(cep) {
    try {
        // Faz a requisição e aguarda a resposta
        const response = await fetch(`https://viacep.com.br/ws/${cep}/json/`);
        
        // Converte a resposta para objeto JavaScript
        const endereco = await response.json();
        
        // Verifica se o CEP foi encontrado
        if (endereco.erro) {
            throw new Error('CEP não encontrado');
        }
        
        console.log('Endereço encontrado:', endereco);
        return endereco;
        
    } catch (erro) {
        console.error('Erro na busca:', erro.message);
        return null;
    }
}
```

## Onde usei no meu código
**1. Extração de texto por página:**
```js
// Função que extrai o texto completo do PDF, página por página
async function extrairTextoDoPDF(pdf) {
    const textoCompleto = [];
    
    try {
        // Itera sobre cada página do PDF
        for (let i = 1; i <= pdf.numPages; i++) {
            // await garante que a página i seja processada antes de passar para a i+1
            const page = await pdf.getPage(i);
            
            // Aguarda a extração do conteúdo de texto da página
            const content = await page.getTextContent();
            
            // Concatena o texto de cada página
            const textoPage = content.items
                .map(item => item.str)
                .join(' ');
            
            textoCompleto.push(textoPage);
            console.log(`Página ${i} processada`);
        }
        
        return textoCompleto;
        
    } catch (erro) {
        console.error('Erro ao extrair texto:', erro);
        return [];
    }
}
```


## Requisições HTTP (fetch)

## O que são
O `fetch()` é uma API nativa do navegador para fazer requisições HTTP (enviar ou receber dados de servidores).

## Para que servem
Consumir APIs externas, enviar formulários, carregar arquivos JSON ou integrar o frontend com um backend.

## Como usar
```js
// GET básico - Buscar dados
async function obterDados(url) {
    try {
        // método GET é o padrão do fetch
        const response = await fetch(url, {
            method: 'GET',
            headers: {
                'Content-Type': 'application/json'
            }
        });
        
        // Verifica se a requisição foi bem-sucedida (status 200-299)
        if (!response.ok) {
            throw new Error(`Erro HTTP: ${response.status}`);
        }
        
        const dados = await response.json();
        return dados;
        
    } catch (erro) {
        console.error('Erro ao obter dados:', erro);
    }
}

// POST - Enviar dados para o servidor
async function enviarDados(url, dados) {
    try {
        const response = await fetch(url, {
            method: 'POST', // Método POST para criar/enviar
            headers: {
                'Content-Type': 'application/json'
            },
            // JSON.stringify converte o objeto JavaScript em string JSON
            body: JSON.stringify(dados)
        });
        
        if (!response.ok) {
            throw new Error(`Erro na requisição: ${response.status}`);
        }
        
        const respostaDados = await response.json();
        return respostaDados;
        
    } catch (erro) {
        console.error('Erro ao enviar dados:', erro);
    }
}
```

## Exemplos
```js
// Exemplo prático com CEP - Preencher endereço automaticamente
async function preencherEndereecoPorCEP(cep) {
    try {
        // Requisição GET para a API ViaCEP
        const response = await fetch(
            `https://viacep.com.br/ws/${cep}/json/`
        );
        
        // Verifica erros HTTP
        if (!response.ok) {
            throw new Error('Falha na requisição');
        }
        
        const endereco = await response.json();
        
        // Verifica se o CEP é válido
        if (endereco.erro) {
            console.warn('CEP não encontrado');
            return null;
        }
        
        // Preenche os campos do formulário
        document.getElementById('rua').value = endereco.logradouro || '';
        document.getElementById('bairro').value = endereco.bairro || '';
        document.getElementById('cidade').value = endereco.localidade || '';
        document.getElementById('estado').value = endereco.uf || '';
        
        return endereco;
        
    } catch (erro) {
        console.error('Erro ao buscar endereço:', erro);
    }
}

// Chamada da função
preencherEndereecoPorCEP('01310100'); // CEP da Avenida Paulista
```

## Onde usei no meu código
*Nota: No projeto atual, o foco está na API de arquivos local (`FileReader` e `ArrayBuffer`) para processar o PDF enviado pelo usuário. No entanto, o `fetch` seria usado caso decidíssemos buscar tabelas de feriados ou configurações de uma API externa para validar os dados extraídos.*