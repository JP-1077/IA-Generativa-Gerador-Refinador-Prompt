# Agente: Gerador de Prompt (Polaris AI) — Visão Geral (Overview)

## 1. Propósito do Agente
O **Gerador de Prompt (Polaris AI)** é um agente desenvolvido no **Copilot Studio** com o propósito de ajudar usuários a **criar prompts de alta qualidade** e/ou **refinar prompts existentes**, garantindo clareza, contexto adequado, estrutura e aderência a critérios de qualidade.

O agente atua como um “copiloto de engenharia de prompts”, reduzindo o esforço cognitivo do usuário e aumentando a taxa de sucesso na obtenção de respostas úteis de modelos generativos.

---

## 2. Objetivos do Agente
### Objetivo principal
- **Produzir prompts melhores** (mais claros, completos, estruturados e mensuráveis) para diversos cenários de IA generativa.

### Objetivos específicos
- Identificar **intenção do usuário**: criar prompt do zero *ou* melhorar/refinar um prompt já existente.
- Capturar e estruturar parâmetros essenciais: **objetivo**, **contexto**, **restrições**, **tom**, **formato de saída**, **público-alvo**, **exemplos**, **critérios de sucesso**.
- Entregar prompts seguindo um **contrato de saída** padronizado (com seções e marcações).
- Aplicar uma **rubrica de avaliação** para qualificar o prompt e sugerir evoluções.
- Minimizar ambiguidade com perguntas de esclarecimento quando necessário.

---

## 3. Casos de Uso Esperados
### 3.1 Criar prompt do zero (Prompt Builder)
**Exemplos de demanda:**
- “Crie um prompt para gerar um relatório executivo semanal.”
- “Quero um prompt para classificar e-mails do Outlook por prioridade.”
- “Preciso de um prompt para resumir uma ata e listar decisões e ações.”

**Saída esperada:**
- Um prompt final estruturado, com variáveis recomendadas e instruções claras.

### 3.2 Melhorar/refinar prompt (Prompt Refiner)
**Exemplos de demanda:**
- “Melhore esse prompt para ficar mais objetivo e gerar saída em JSON.”
- “Refine o prompt para reduzir alucinações e pedir fontes.”
- “Ajuste o tom para algo mais formal e corporativo.”

**Saída esperada:**
- Versão refinada do prompt + explicação do que mudou + checklist de qualidade.

### 3.3 Padronização e governança de promps (Organizational Patterns)
**Exemplos de demanda:**
- “Transforme esse prompt em um padrão reutilizável para meu time.”
- “Crie variantes do prompt por persona: analista / gestor / diretoria.”

**Saída esperada:**
- Um prompt “template” com placeholders e recomendações de uso.

### 3.4 Troubleshooting de prompt (Diagnóstico)
**Exemplos de demanda:**
- “Esse prompt gera respostas inconsistentes, como corrigir?”
- “O modelo sempre ignora a formatação pedida.”

**Saída esperada:**
- Diagnóstico do problema + versões alternativas do prompt (A/B).

---

## 4. Roadmap de Evolução do Agente

### Curto prazo (v1.x)
- Melhorar perguntas de esclarecimento (quando o input vier incompleto).
- Adicionar biblioteca de **templates padrão** (resumo, e-mail, análise, checklist, narrativa).
- Expandir rubrica de avaliação e incluir score por dimensão (clareza, contexto, formato etc.).


### Médio prazo (v2.x)
- Criar exemplos de saída para os principais formatos (JSON, tabela, bullets, markdown).
- Inserir **classificação automática do tipo de tarefa** (escrita, extração, transformação, planejamento).
- Adicionar **variações do prompt** (curto, completo, com guardrails rígidos).
- Integrar com repositório interno de prompts (catálogo) para reutilização e rastreabilidade.


---

## 5. Fora de Escopo (Não-Objetivos)
- Executar ações transacionais (ex.: criação de tickets, execução de runbooks).
- Garantir resultado perfeito do modelo final (o agente **otimiza o prompt**, mas a resposta final depende do modelo, dados e contexto).
- Substituir governança de segurança/compliance: o agente deve respeitar políticas e controles organizacionais.

---

## 6. Referências e Artefatos
- Pasta `01 - Arquitetura/`: detalhes de modos, system prompt, contratos e rubricas.
- Pasta `03 - Design/`: design conversacional, tom e padrões de interação.
- Pasta `06 - Testes/`: conjunto de testes, métricas e histórico.