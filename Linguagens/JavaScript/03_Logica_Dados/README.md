# Fase 3: Motor de dados (lógica e limpeza)

## Objetivo
Implementar a inteligência de extração, limpeza e estruturação dos dados textuais.

## Conteúdo

### Expressões regulares (Regex)
- Padrões para horários, datas e nomes.
- Métodos de string essenciais:
  - `.match()`
  - `.exec()`
  - `.replace()`
  - `.split()`

### Arrays, objetos e mapas
- Transformações com:
  - `.map()`
  - `.filter()`
  - `.reduce()`
  - `.slice()`
  - `.sort()`
- Uso de objetos e `Map` para lookup rápido por chave.

### Datas e horas (Date API)
- Criação com `new Date(ano, mes, dia)`.
- Extração com `.getTime()`, `.getDay()`, `.getDate()`.
- Conversão de `HH:MM` para minutos totais.
- Cálculo de intervalos e virada de dia (passagem pela meia-noite).

## Checklist
- [ ] Definir e testar regex para capturas principais
- [ ] Criar função de limpeza de linhas brutas
- [ ] Criar função para normalizar campos textuais
- [ ] Modelar saída em objetos consistentes
- [ ] Ordenar e agrupar registros por data/pessoa
- [ ] Converter horários em minutos para cálculos
- [ ] Validar cenários de virada de turno
- [ ] Gerar estrutura final pronta para renderização

## Entregável da fase
Módulo de dados capaz de transformar entrada textual bruta em estrutura limpa, previsível e reutilizável.
