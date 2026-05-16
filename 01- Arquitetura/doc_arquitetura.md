# Arquitetura Geral — Agente Gerador de Prompt (Polaris AI)

## 1. Visão Geral
O agente foi construído no **Copilot Studio**, seguindo uma arquitetura lógica baseada em:
- **Roteamento por intenção** (Criar / Refinar / Diagnosticar)
- **System Prompt** como núcleo de comportamento
- **Contratos de saída** padronizados
- **Rubricas de avaliação** para qualidade e evolução contínua

---

## 2. Modos de Operação do Agente
### Modo 1 — Prompt Builder (Criar)
- Entrada: descrição da necessidade
- Função: gerar prompt completo com estrutura e placeholders
- Saída: prompt final + recomendações de uso

### Modo 2 — Prompt Refiner (Refinar)
- Entrada: prompt atual + objetivo de melhoria
- Função: diagnosticar e reescrever mantendo intenção
- Saída: prompt refinado + mudanças + checklist

### Modo 3 — Prompt Diagnostic (Diagnóstico)
- Entrada: prompt + sintomas (ex.: “resposta inconsistente”)
- Função: identificar falhas típicas (ambiguidade, falta de restrição, formato fraco)
- Saída: diagnóstico + 1–2 versões alternativas + sugestões de teste

### Modo 4 — Template/Pattern Generator (Padrões)
- Entrada: necessidade recorrente do time/área
- Função: criar prompt template reutilizável + guia de uso
- Saída: prompt parametrizável + exemplos de preenchimento

---

## 3. System Prompt (descrição)
O System Prompt define:
- Papel do agente: especialista em criação e melhoria de prompts
- Restrições: priorizar clareza, evitar ambiguidades, fornecer estrutura
- Padrões de saída: seguir contrato, oferecer checklists e iteração
- Governança: aplicar critérios mínimos de qualidade antes de entregar

> Recomenda-se manter o System Prompt versionado em arquivo dedicado
> (ex.: `01 - Arquitetura/01_System_Prompt_e_Politicas.md`) para rastreabilidade.

---

## 4. Contratos de Saída Padrão (Output Contracts)

## 4.1 Contrato — Prompt Final (padrão)
O agente entrega um bloco principal “PROMPT FINAL” com seções:

1. **Contexto**
2. **Objetivo**
3. **Instruções**
4. **Restrições / Guardrails**
5. **Formato de saída**
6. **Critérios de sucesso**
7. **Inputs esperados (placeholders)**

### Exemplo de estrutura (modelo)
- PROMPT FINAL:
  - Contexto: ...
  - Objetivo: ...
  - Instruções: ...
  - Restrições: ...
  - Saída: ...
  - Critérios: ...

## 4.2 Contrato — Melhorias (quando refino)
- Prompt original (referência)
- Prompt refinado
- Lista de mudanças (bullets)
- Checklist de qualidade aplicado
- Sugestões de variações (A/B)

---

## 5. Rubricas de Avaliação de Prompts (Prompt Scoring Rubric)
O agente aplica uma rubrica interna (explícita ou implícita) por dimensões:

1. **Clareza**: instruções inequívocas
2. **Contexto**: informações necessárias para a tarefa
3. **Restrições**: limites e “não fazer”
4. **Formato de saída**: estrutura e exigências (ex.: JSON schema)
5. **Cobertura de casos**: casos normais e limites
6. **Testabilidade**: possibilidade de avaliar se está correto
7. **Alinhamento ao objetivo**: sem desvios de escopo

Escala sugerida: 0–2 por dimensão (total 14), com interpretação:
- 12–14: Excelente (pronto para uso)
- 9–11: Bom (pequenos ajustes)
- 6–8: Regular (precisa refino)
- <=5: Fraco (reconstruir)

---

## 6. Evolução do Agente (melhoria contínua)
A evolução é guiada por:
- Resultados de testes (métricas de avaliação)
- Feedback do usuário (qualitativo)
- Análise de falhas (ex.: formato ignorado, prompt longo demais)
- Incrementos no catálogo de templates e padrões

Recomendações para governança:
- Versionar alterações relevantes (System Prompt, contratos, rubricas) com release notes
- Manter histórico de testes por versão (v1.0, v1.1...)
- Definir critérios mínimos para publicar nova versão do agente
