# Agente IA Generativa: Gerador Prompts | Polaris

## Visão Geral

Este projeto visa o desenvolvimento de um **agente de IA generativa** focado em **qualidade, revisão e padronização de prompts**, utilizando o ecossistema Microsoft (Copilot Studio, Copilot e LLM do Copilot).

O agente tem como objetivo apoiar **todos os colaboradores** a:
- Criar prompts melhores desde o início
- Revisar e melhorar prompts existentes
- Detectar problemas comuns em prompts mal formulados
- Atuar como **auditor de qualidade** em campos textuais de outros agentes (ex.: Agente de Demandas)


---

## Objetivos do Projeto

### Objetivo Principal
Fornecer um agente confiável que **avalie, reestruture e sugira prompts de alta qualidade** para uso com o Copilot, garantindo clareza, contexto e previsibilidade de saída.

### Objetivos Secundários
- Padronizar a qualidade de prompts usados internamente
- Reduzir prompts ambíguos, incompletos ou inconsistentes
- Melhorar a qualidade de entradas em sistemas de demandas
- Servir como base reutilizável para integração com outros agentes de IA

---

## Escopo do Agente

### Incluído
- Revisão e reescrita de prompts existentes
- Geração de prompts a partir de objetivos e parâmetros
- Avaliação estruturada de qualidade (OK / Atenção / Ruim)
- Auditoria de campos textuais (ex.: descrição de demandas)

### Fora do Escopo
- Integrações com SharePoint, Teams ou sistemas externos
- Aprendizado automático a partir de feedback do usuário
- Criação automática de requisitos ou informações não fornecidas

---

## Funcionalidades Principais

### 1. Revisor e Reescritor de Prompts

Permite que o usuário insira um prompt existente para avaliação e melhoria.

#### Entradas
- Prompt original
- (Opcional) Contexto adicional fornecido pelo usuário

#### Saídas
Formato estruturado e previsível:

- **Diagnóstico (Resumo)**
  - Status: `OK`, `Atenção` ou `Ruim`
  - Motivos principais da classificação

- **Checklist de Qualidade**
  - Objetivo claro
  - Contexto suficiente
  - Entradas definidas
  - Formato de saída definido
  - Critérios de qualidade
  - Restrições explícitas

- **Erros Identificados**
  - Lista objetiva dos principais problemas

- **Mudanças Aplicadas**
  - Principais ajustes realizados no prompt

- **Prompt Reescrito (Melhorado)**
  - Mantém a intenção original
  - Apenas reorganiza, esclarece e melhora

#### Regras Importantes
- O agente **não inventa informações**
- Se dados críticos estiverem ausentes, o agente pergunta antes de finalizar
- A intenção original do prompt deve ser preservada

---

### 2. Sugestão de Prompts por Objetivo

Ajuda usuários que ainda não possuem um prompt estruturado.

#### Funcionamento
- Usuário define um **objetivo** (ex.: resumir, classificar, gerar e-mail)
- Usuário define parâmetros básicos (ex.: tom, formato, público)

#### Saída
- 3 versões de prompt:
  - Curta
  - Padrão
  - Robusta

Cada versão é adaptada para uso com o Copilot e já segue os critérios de qualidade definidos pelo agente.

---

### 3. Auditor de Campos (Integração com Agente de Demandas)

O agente pode atuar como **auditor de qualidade** de campos textuais preenchidos pelo usuário em outros sistemas.

#### Exemplo de Uso
- Campo: "Descrição da Demanda"
- O agente valida se:
  - O texto faz sentido
  - Está claro e completo
  - Atende ao objetivo do campo

#### Saída por Campo
- Status: `OK | Atenção | Ruim`
- Motivos da avaliação
- Erros identificados
- Texto reestruturado sugerido
- Perguntas (caso faltem informações)

#### Princípios do Auditor
- Valida somente o que foi fornecido
- Não cria novos requisitos
- Reestrutura e melhora linguagem e clareza
- Pergunta quando há lacunas críticas

---

## Critérios de Avaliação de Prompts

A avaliação é baseada em um **rubric fixo**, composto por:

1. Objetivo claro
2. Contexto suficiente
3. Entradas bem definidas
4. Formato de saída esperado
5. Critérios de qualidade explícitos
6. Restrições ou limitações

### Classificação
- **OK**: Prompt claro, completo e utilizável
- **Atenção**: Prompt utilizável, mas com riscos ou lacunas menores
- **Ruim**: Prompt incompleto, ambíguo ou potencialmente incorreto

---

## Público-Alvo

- Todos os colaboradores da organização
- Usuários técnicos e não técnicos
- Pessoas que utilizam o Copilot no dia a dia para:
  - Escrita
  - Análise
  - Planejamento
  - Automação
  - Documentação

---

## Modelo de LLM Avaliado

- O agente avalia e estrutura prompts **pensando no comportamento do Copilot**

---

## Princípios de Design do Agente

- Simples antes de complexo
- Consistência > criatividade
- Clareza > sofisticação
- Não inventar informações
- Educação curta, contextual e opcional

---

## Próximos Passos (Evolução Futura)

- Expansão para mais tipos de auditoria
- Integração com sistemas corporativos (SharePoint, Teams)
- Histórico e versionamento de prompts
- Feedback do usuário para refinamento
- Integração com múltiplos agentes especializados

---
