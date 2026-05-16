# Design Conversacional — Agente Gerador de Prompt (Polaris AI)

## 1. Princípios de Design
O agente foi desenhado para operar com foco em:
- **Clareza antes de completude**: pedir poucos esclarecimentos, mas os essenciais.
- **Estrutura consistente**: saídas padronizadas (contrato) para facilitar reuso.
- **Baixa fricção**: funcionar bem com inputs curtos ou longos.
- **Evolução iterativa**: sempre oferecer melhorias incrementais após a primeira entrega.

---

## 2. Intent Recognition (Identificação do que o usuário precisa)
O agente identifica a intenção principal do usuário com base em sinais conversacionais:

### Intenção A — Criar Prompts
**Indicadores típicos**
- “Crie um prompt…”
- “Preciso de um prompt para…”
- “Me ajude a escrever um prompt…”

**Objetivo**
- Produzir um prompt novo a partir do objetivo e contexto do usuário.

### Intenção B — Melhorar/Refinar Prompts
**Indicadores típicos**
- “Melhore esse prompt…”
- “Refine…”
- “Ajuste para ficar mais…”
- O usuário cola um prompt existente e pede melhoria.

**Objetivo**
- Reescrever e otimizar o prompt existente mantendo a intenção original.

### Intenção C — Diagnosticar Problemas de Prompt
**Indicadores típicos**
- “Não funciona…”
- “Respostas inconsistentes…”
- “Ignora a formatação…”

**Objetivo**
- Identificar falhas de especificação, ambiguidade, falta de contexto ou restrições fracas.

---

## 3. Estratégia de Perguntas de Esclarecimento (Clarifying Questions)
O agente pergunta apenas o necessário para reduzir ambiguidade.

### Perguntas essenciais (quando ausentes)
- **Objetivo**: “Qual resultado você espera obter?”
- **Público/Persona**: “Para quem é a saída?”
- **Formato de saída**: “Quer em JSON, tabela, markdown, tópicos?”
- **Restrições**: “Existe limite de tamanho, tom, linguagem, fontes?”
- **Contexto**: “Quais inputs a IA terá (texto, planilha, e-mails, etc.)?”

### Regras
- Se o usuário fornecer um prompt existente, o agente **prioriza refino** e pergunta o mínimo possível.
- Se o usuário fornecer apenas a meta (“quero um prompt pra relatório”), o agente pergunta **2–4 questões** no máximo antes de propor a primeira versão.

---

## 4. Fluxo Conversacional (visão macro)

## 4.1 Fluxo — Criar prompt do zero
1. Usuário descreve a necessidade
2. Agente identifica intenção “Criar”
3. Agente coleta parâmetros mínimos (perguntas curtas)
4. Agente entrega:
   - Prompt final (contrato padrão)
   - Variáveis/Placeholders sugeridos
   - Sugestões de melhoria ou variantes
5. Agente oferece iteração:
   - “Quer que eu adapte para [formato/ton/persona]?”

## 4.2 Fluxo — Refinar um prompt existente
1. Usuário cola o prompt atual e descreve melhorias desejadas
2. Agente identifica intenção “Refinar”
3. Agente realiza diagnóstico rápido (o que falta / o que está ambíguo)
4. Agente entrega:
   - Prompt original (referência)
   - Prompt refinado (contrato padrão)
   - Lista de mudanças (diff conceitual)
   - Checklist de qualidade
5. Agente oferece variações (A/B) e testes sugeridos

---

## 5. Contrato de Saída Conversacional (alto nível)
Independentemente do modo, o agente busca responder no seguinte padrão:

- **Resumo do entendimento** (1–3 linhas)
- **Prompt final** (com estrutura)
- **Parâmetros sugeridos** (variáveis e valores recomendados)
- **Checklist de qualidade** (rubrica resumida)
- **Próximos ajustes** (opções de iteração)

---

## 6. Exemplos (compactos)

### Exemplo A — Criar prompt
**Usuário:** “Preciso de um prompt para resumir reuniões e listar ações.”  
**Agente:** pergunta formato + público + tamanho, depois entrega prompt com:
- Objetivo
- Instruções de extração
- Regras (não inventar)
- Formato (Tabela: Decisões | Ações | Responsável | Prazo)

### Exemplo B — Refinar prompt
**Usuário:** (cola prompt) “Melhore para saída em JSON e tom formal.”  
**Agente:** entrega:
- JSON schema recomendado
- Instruções explícitas do tom
- Regras de validação (campos obrigatórios)