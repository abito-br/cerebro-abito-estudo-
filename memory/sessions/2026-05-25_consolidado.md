---
tipo: eod-consolidado
projeto: ABITO
data: 2026-05-25
salvar_em: ABITO/08_OPERACAO/EOD_consolidado_2026-05-25.md
tags: [eod, consolidado, fonte-unica]
---

# EOD CONSOLIDADO — 25/05/2026
*Junção de 5 EODs espalhados (22-25/05) + sessão de hoje. A partir daqui: 1 bot, 1 EOD/dia.*

## ESTADO REAL AGORA (vivo)
- Pipeline de notas/EOD: **viva, UM bot (Abito Notes)** — captura → confirmação ✅ → EOD/Painel, tudo no mesmo bot. Workflows com `pull --rebase` + concurrency (sem colisão de push).
- Instagram @abito.br: no ar. WhatsApp Business: link direto na bio, funcionando.
- Claude in Chrome: operacional (usado pra varredura Reddit manual).
- Vault: READMEs + `_MAPA` gerados; PII de cliente anonimizada (CLI_01 + VeraCrypt); Registrato no VeraCrypt.
- Regras do board escritas. Design do Orquestrador (Opus) pronto pra testar.

## MUDOU / SUPERADO (reconciliação)
- **Miner YouTube** — EOD 23 dizia "ativo/automático". HOJE: quebrado (aspas/canais) → **PAUSADO**. Reativar só com estrutura de marketing.
- **Telegram CHAT_ID** — era 🔴 bloqueador (EOD 23 Dia 2). **RESOLVIDO** hoje.
- **EOD por thread** — superado. Tinha 5 EODs espalhados; agora é 1 bot → 1 EOD automático.
- **Manus recorrente** — segue sem entregar; confirmar desativar (ou usar só p/ texto).
- **Apify MCP / Facebook scraper** — travado em sandbox MS Store; depende de reinstalar Claude Desktop via `.exe`.
- **subtitles.py** — valores conflitantes entre threads (MARGIN 220→620 vs FONT 130/MARGIN 750). CONFIRMAR qual é o atual.

## SINAL DE CAMPO — PRIORIDADE
Leads reais identificados em **r/primeiroimovel** (fonte primária, não r/financas):
- Post "Minha renda não vai ser aprovada pela Caixa" (2 meses, 51 comentários) → **Dona Maria ★**
- Post "Financiamento Caixa — assinei com construtora e 5 dias dps..." (26 dias) → **Marcos P5 ★**
- Termo-âncora que funciona: `financiamento negado caixa`.
- Subs a monitorar: r/investimentos, r/financaspessoais (perfil C/D), r/ConversaFinanceira.
→ **Isto é a ponta. O Marcos real está falando.**

## ABERTO (deduplicado, por dono)

**Campo (prioridade):**
- `[VOCÊ]` Ler os comentários dos 2 posts r/primeiroimovel → identificar leads.
- `[IA]` Gerar abordagem WhatsApp pros leads — voz chão de fábrica, zero venda.
- `[VOCÊ]` Guilherme: contrato / papéis / fluxo de dados / leads.
- `[VOCÊ]` Inputs pendentes: Grupos FB Valinhos, YouTube Rio Preto, Correspondentes Caixa Aqui, construtoras locais.

**Produto:**
- `[CODE]` `watch_registrato.py` → apontar p/ `E:\COFRE_DIA\entrada`.
- `[CODE]` `extrair_registrato_v21.py` → testar com PDF real.

**Vault/infra (congelar — não prioridade):**
- `INDEX.md` v4.5 → v4.7 (e resolver duplicação INDEX/_MAPA/MOC).
- Obsidian mobile sync verificar.
- Escrever seção SISTEMAS no Briefing (base canônica).
- Colar as regras do board nas IAs (Cowork = desktop).

**Marketing (decisão pendente):**
- IG ↔ Facebook Meta Suite 🔴; re-ancorar datas CSV/Tracker; roteiros Dias 4-20; tracker métricas; deploy IntelDashboard no Netlify; credenciais Azure permanentes.

## DECISÃO NECESSÁRIA
Dois trilhos puxando tempo: **Sprint Social** (20 dias de conteúdo diário) vs **Campo** (Reddit + Guilherme + brokers). A fase é validação de campo; o sinal real está no Reddit. Recomendação: **congelar/reduzir o Sprint Social, ir pro campo.** Decisão do Davison.

## TAREFA DO DIA (26/05)
**Campo primeiro:** ler os comentários do post Dona Maria ★ em r/primeiroimovel e preparar 1 abordagem WhatsApp. Em paralelo: Guilherme.

---

## FLUXO A PARTIR DE HOJE (guardar)

**Abrir o dia:**
1. Chat NOVO (nunca continuar antigo).
2. Cola, nesta ordem: Briefing permanente + ESTE EOD (estado atual) + 1 frase de tarefa do dia.

**Durante o dia:**
3. Toda decisão/nota → 1 linha no **bot Abito Notes** (do celular, da fábrica). Não persegue, não junta thread.

**Fim do dia:**
4. O `eod_synth` gera o EOD automático no bot — sozinho.

**Regra de ouro:** 1 bot, 1 EOD por dia. Nunca mais EOD por thread, nunca mais juntar conversa na mão.
