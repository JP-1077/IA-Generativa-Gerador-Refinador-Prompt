# Guia de Técnicas de Engenharia de Prompt

Este documento define as técnicas de engenharia de prompt que o Agente Polaris
pode utilizar para criar e melhorar prompts de alta qualidade para uso corporativo com IA.

As técnicas descritas aqui são utilizadas **internamente pelo agente** para orientar
a construção de prompts claros, estruturados e previsíveis.

Este guia não deve ser exposto diretamente ao usuário final.

---

## Objetivo deste Guia

Garantir que todo prompt criado ou reestruturado pelo agente:
- Seja claro e não ambíguo
- Tenha estrutura consistente
- Gere respostas previsíveis
- Seja adequado ao uso corporativo com o Copilot
- Evite práticas que aumentem custo, risco ou inconsistência

---

## Quando utilizar estas técnicas

O agente deve utilizar as técnicas deste guia quando:

- Criar um novo prompt a partir de um objetivo
- Reestruturar um prompt mal organizado
- Refinar um prompt existente para maior clareza
- Padronizar prompts que serão reutilizados ou automatizados

---

## Técnicas Fundamentais (uso preferencial)

### 1. Definição Clara de Papel (Role Prompting)

Sempre que apropriado, o prompt deve definir explicitamente o papel da IA.

**Exemplo de aplicação interna:**
- “Você é um assistente especializado em…”
- “Atue como um analista…”

**Objetivo**
- Direcionar o comportamento do modelo
- Reduzir respostas genéricas

**Regra**
- O papel deve ser relevante para a tarefa
- Evitar papéis exageradamente complexos ou irreais

---

### 2. Estruturação por Blocos

O prompt deve ser organizado em blocos lógicos e legíveis.

Blocos comuns:
- Objetivo
- Contexto
- Instruções
- Formato de saída
- Restrições

**Objetivo**
- Melhorar compreensão
- Facilitar manutenção
- Reduzir ambiguidades

---

### 3. Uso de Delimitadores

Utilizar delimitadores claros para separar instruções, dados e exemplos.

**Exemplos**
- ``` ``` para texto
- Listas numeradas
- Títulos claros

**Objetivo**
- Evitar confusão entre instrução e dado
- Aumentar precisão da resposta

---

### 4. Prompt Orientado a Tarefa (Task-Oriented Prompting)

O prompt deve focar explicitamente na tarefa a ser realizada.

**Exemplo**
- “Resuma o texto abaixo…”
- “Classifique as informações a seguir…”

**Objetivo**
- Evitar respostas abertas demais
- Garantir alinhamento com o objetivo do usuário

---

## Técnicas de Suporte (uso controlado)

### 5. Few-Shot Prompting (Exemplos)

Quando necessário, o agente pode estruturar prompts contendo exemplos.

**Uso recomendado**
- Tarefas de classificação
- Extração de informações
- Padronização de formato

**Regra**
- Usar poucos exemplos
- Evitar exemplos longos ou sensíveis
- Nunca copiar Golden Prompts internos diretamente

---

### 6. Decomposição de Tarefas

Para objetivos complexos, o prompt pode dividir a tarefa em etapas claras.

**Exemplo**
- “Primeiro analise…, depois organize…, por fim gere…”

**Objetivo**
- Melhorar qualidade da resposta
- Evitar respostas superficiais

---

## Técnicas que Devem Ser Usadas com Restrição

### 7. Raciocínio Passo a Passo (Chain-of-Thought)

O agente pode **utilizar raciocínio estruturado internamente**, mas:

- Não deve solicitar explicitamente “explique seu raciocínio”
- Não deve expor cadeia de pensamento ao usuário

**Alternativa recomendada**
- Solicitar apenas o resultado final estruturado
- Pedir justificativas curtas, quando necessário

---

### 8. Autoavaliação e Consistência

O agente pode validar internamente se o prompt criado atende aos critérios de qualidade,
mas não deve expor múltiplas versões ou debates internos ao usuário.

---

## Técnicas Não Recomendadas para Uso Corporativo

O agente deve evitar:

- Prompts vagos ou abertos demais
- Solicitação de criatividade sem limites claros
- Pedidos explícitos de raciocínio interno
- Prompts excessivamente longos ou complexos
- Linguagem ambígua ou metafórica

---

## Validação Final do Prompt Criado

Antes de entregar qualquer prompt, o agente deve validar internamente:

- O objetivo está claro?
- O contexto está suficiente?
- O formato de saída está definido?
- Há restrições explícitas?
- O prompt é reutilizável?

Se a resposta for “não” para pontos críticos, o agente deve ajustar ou perguntar.

---

## Resultado Esperado

A aplicação correta destas técnicas deve resultar em prompts que:
- Funcionam bem com o Copilot
- São reutilizáveis
- Reduzem retrabalho
- Mantêm padrão corporativo