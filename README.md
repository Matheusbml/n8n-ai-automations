# Automações e agentes de IA com n8n

[English version below](#english)

Coleção de workflows n8n que construí entre 2025 e 2026: agentes de IA conversacionais, pipelines de documentos com OCR e LLM, servidores MCP e automações de processos comerciais e operacionais.

Cada pasta traz:
- o JSON pronto para importar no n8n;
- um README com o problema, a arquitetura, as decisões técnicas, o status real e as limitações.

**Sobre a privacidade:** todos os workflows foram sanitizados. Chaves de API viraram variáveis de ambiente, IDs de planilhas, pastas e calendários viraram placeholders, e nomes de clientes, pessoas e telefones foram removidos. Para rodar, configure suas próprias credenciais no n8n.

## Projetos

| # | Projeto | O que demonstra | Status |
|---|---|---|---|
| 01 | [Auditoria de documentos com OCR e IA](01-auditoria-documentos-ocr-ia) | OCR com Gemini, agente com critérios vindos do banco, score determinístico, roteamento aceitar/revisar/rejeitar | Demonstração funcional |
| 02 | [Agente de pedidos para restaurante](02-agente-pedidos-restaurante) | Agente multimodal no WhatsApp, buffer de mensagens no Redis, RAG com Supabase Vector, servidor MCP com pedidos e cobrança no Asaas | Protótipo (pagamento em sandbox) |
| 03 | [Agente de agendamento com MCP](03-agente-agendamento-mcp) | Ferramentas MCP para agendar, reagendar e cancelar no Google Calendar + Supabase, lembretes 24h e 2h antes | Projeto de estudo, expandido |
| 04 | [SDR de pré-vendas com agendamento](04-sdr-agendamento-reunioes) | Agente que conduz o lead até a reunião, pausa para atendimento humano, memória Redis, regras de horário | Entregue a cliente (anonimizado) |
| 05 | [Captação de leads no LinkedIn](05-captacao-leads-linkedin) | Busca por cargo, região e setor via Serper, parsing, deduplicação e gravação no Excel | Usado em produção (2025) |
| 06 | [Agente de busca de vagas de IA](06-agente-busca-vagas) | Agente com ferramenta de busca, validação de recência, saída JSON estruturada, execução diária | Uso pessoal |
| 07 | [Pesquisa de satisfação pós-venda](07-pesquisa-satisfacao-crm) | Integração Trello + Omie (CRM/ERP) + Gmail, com movimentação de cards | Usado em produção (2025) |
| 08 | [Automação de projetos no Asana](08-automacao-asana-projetos) | Clonagem de cards e subtarefas, extração estruturada com IA para planilha, comentários formatados e enviados por WhatsApp | Entregue a cliente (anonimizado) |

## Stack

- **Orquestração:** n8n (self-hosted e cloud)
- **LLMs:** OpenAI (GPT-4.1-mini, GPT-4o-mini, Whisper) e Google Gemini 2.5 Pro
- **Dados:** Supabase (Postgres, pgvector), Redis
- **Mensageria:** Z-API, Evolution API, Uazapi
- **Integrações:** Google Drive, Sheets e Calendar; Gmail; Asana; Trello; Omie; Asaas; Serper
- **Padrões:**
  - MCP (Model Context Protocol)
  - RAG
  - *output parsers* estruturados
  - buffer de mensagens
  - *human handoff*

## Créditos

Alguns fluxos partem de estruturas ensinadas na formação **Gestor de Automações e Agentes de IA (NoCode Startup)**, como o buffer de mensagens e a quebra de respostas. Em cada README eu indico o que veio da base e o que adaptei.

## Autor

**Matheus Bastos Melo**: [portfolio.meltai.dev](https://portfolio.meltai.dev) · [LinkedIn](https://www.linkedin.com/in/matheusbml/) · mbm.meltai@gmail.com

---

<a id="english"></a>
# AI agents and automations with n8n

A collection of n8n workflows I built in 2025–2026. It covers:
- conversational AI agents;
- OCR + LLM document pipelines;
- MCP servers;
- sales and operations automations.

Each folder contains an importable JSON and a README explaining the problem, the architecture, the technical decisions, the real status and the limitations.

**Privacy:** every workflow is sanitized:
- API keys became environment variables;
- sheet, folder and calendar IDs became placeholders;
- client names, people and phone numbers were removed.

| # | Project | Highlights | Status |
|---|---|---|---|
| 01 | Document audit with OCR + AI | Gemini OCR, DB-driven criteria, deterministic score, accept/review/reject routing | Working demo |
| 02 | Restaurant ordering agent | Multimodal WhatsApp agent, Redis buffer, Supabase Vector RAG, MCP server with orders and Asaas payments | Prototype (sandbox payments) |
| 03 | Scheduling agent over MCP | Book, reschedule and cancel tools (Google Calendar + Supabase), 24h/2h reminders | Study project, extended |
| 04 | Pre-sales SDR agent | Lead-to-meeting flow, human handoff, Redis memory, time rules | Delivered to a client (anonymized) |
| 05 | LinkedIn lead sourcing | Serper search, parsing, dedup, Excel output | Used in production (2025) |
| 06 | AI job-search agent | Search tool, recency validation, structured JSON, daily schedule | Personal use |
| 07 | Post-sale satisfaction survey | Trello + Omie + Gmail | Used in production (2025) |
| 08 | Asana project automation | Card/subtask cloning, AI extraction to Sheets, formatted comments to WhatsApp | Delivered to a client (anonymized) |

Some flows build on patterns taught in the NoCode Startup "AI Agents" program, and each README states what I adapted.
