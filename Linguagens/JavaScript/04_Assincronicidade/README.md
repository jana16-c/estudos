# Fase 4: Assincronicidade e bibliotecas externas

## Objetivo
Processar arquivos sem travar a interface e integrar biblioteca de leitura de PDF.

## Conteúdo

### JavaScript assíncrono
- Conceito de Event Loop.
- `Promise` e ciclo de resolução/rejeição.
- Uso de `async/await` para fluxo legível.

### APIs de arquivo
- API `File`.
- Leitura por `ArrayBuffer` ou `FileReader`.
- Estratégias para feedback de progresso ao usuário.

### Integração com `pdf.js`
- Importação da biblioteca.
- Leitura de documento binário.
- Iteração por páginas.
- Extração da camada textual com `getTextContent()`.

## Checklist
- [ ] Ler arquivo selecionado de forma assíncrona
- [ ] Exibir estado de carregamento durante processamento
- [ ] Implementar `async/await` no fluxo principal
- [ ] Integrar `pdf.js` e carregar documento
- [ ] Extrair texto de todas as páginas
- [ ] Tratar falhas de arquivo inválido/corrompido
- [ ] Garantir que a UI permaneça responsiva

## Entregável da fase
Pipeline assíncrono funcional: arquivo de entrada -> texto extraído -> envio para o motor de dados.
