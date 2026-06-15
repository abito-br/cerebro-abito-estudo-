# EOD-MESTRE — Sprint 13-14/jun/2026 (2 dias)
Consolidação da thread. Fonte para o Cowork distribuir aos lugares certos (skill salvar ainda não existe).

## 1. CLIENTES (19840b — 1º caso real)
- Achado central: caminho dela é FAIXA 1 / PODE ENTRAR (SP, Lei 17.638/2021), NÃO financiamento. BPC = isenção de parcela. 2-3 critérios de prioridade (mulher chefe, PcD filho, aluguel >30%).
- Destravamento: revisar ficha cadastro.cohab.sp.gov.br (não precisa gov.br — só e-mail). Garantir prioridades registradas. Risco: 38 anos só presencial → pode estar sem prioridade na ficha ou duplicada.
- Entregues no Drive (pasta do caso): Mapa_Destravamento_19840b, PassoAPasso_Cohab_19840b, Sessao_Fazer_Junto (não usada — ela faz sozinha).
- Status: aguardando ela mexer na ficha + atualizar gov.br em paralelo.
→ DESTINO: Drive/01_CLIENTES (LGPD, fica no Drive sempre).

## 2. PRODUTO / JORNADA
- Árvore de decisão MCMV (triagem SIM/NÃO, corte verde-auto / azul-humano). Nó de renda roteia F1 vs F2+.
- Roteiro base mães + roteiro 19840b.
- CORREÇÃO v0→v1: Faixa 1 = PORTA PRINCIPAL do público Abito, não "2ª porta". Inverter roteiros.
→ DESTINO: GitHub areas/produto/ (conhecimento).

## 3. DIAGNÓSTICO (site)
- No ar (Netlify): capta lead via Netlify Forms + UUID client-side. Não perde lead. Não usa Supabase.
- Correções pendentes (lote, 1 deploy): texto CSCR "não sei ao certo" afirma pagamento falso; "analisamos na hora" = promessa; varrer 6 textos; +3 perguntas IRIS (faixa, cidade, situação inicial).
- Migração: vai pra VPS Hostinger junto com as correções (não gastar deploy no Netlify).
→ DESTINO: arquivo HTML no Drive (artefato) + decisões no GitHub.

## 4. DASHBOARD PIPELINE (painel_abito.html)
- Pronto v2: filtro por corretor, prazos no topo, semáforo, kanban com TRAVA (não passa pra Cadastro/banco sem docs da faixa — F1: CadÚnico+ficha Cohab; F2+: Registrato+renda), funil, por corretor, IRIS rodapé global.
- Coleta progressiva: objeto docs por cliente, preenche conforme entra. Trava forte Mapa→Cadastro.
- Status: aprovado, NÃO publicado. Subir na VPS Hostinger.
→ DESTINO: HTML no Drive (artefato) → hospedar VPS.

## 5. CUSTO API / OPENCLAW (resolvido)
- Causa dos $48/$50: gateway OpenClaw em loop (heartbeat 30min + cache 5min reescrito). Processo morto. Não volta sozinho.
- Religar só com 6 travas: sessões isoladas, cache 1h, cadência 6h/diário, 1 heartbeat, revisar ciclo abitonotes, auditar crons. Após 1/jul (reset).
- Estratégia custo: SIMPLIFICAR. Esperar reset jul, ver se cabe em $50. Só então Anthropic Startup Program. Créditos cloud (AWS $100/Azure $1k/Google $2k) = reserva, NÃO migrar operação.
→ DESTINO: GitHub memory/sessions + decisions.

## 6. REORGANIZAÇÃO DA BASE (executada via Code)
- Metodologia Pixel: GitHub = conhecimento (fonte), Drive = arquivos+clientes (LGPD), Obsidian = mantido (visualizador).
- PRs #1 e #2 mergeados: MAPA.md por pasta (padrão fractal), conhecimento migrado, legados removidos, PII scrubada, repo PRIVADO, PAT revogado+rotacionado.
- _MAPA_CANONICO v2.1 ativo (Drive) — corrige contradições (sem Make/n8n; Cara/Guilherme; hospedagem VPS faseada).
→ DESTINO: feito.

## 7. FUNDING / IMPACTO
- IRIS+ já ~70% embutível: uuid=uuid_familia, classificação=tipo_caso, árvore=faixa, dashboard=status. Falta 3 campos no diagnóstico.
- SDGs 1,10,11. Métricas: PI4060, PI5965, PD2541, PD6384.
- Candidaturas: email CORPORATIVO (contato@somosabito.com.br) — pessoal é motivo nº1 de rejeição. AWS Founders ($1000, verificar status), Azure ($1k, refazer c/ corp), Anthropic Startup ($10-25k, convidar email corp na org). Oracle adiado. Irlanda New Frontiers médio prazo.
- Impact Pack (Google Doc) atualizar semanal; guia IRIS (referência).
→ DESTINO: GitHub empresa/contexto/funding/ + Impact Pack fica Google Doc.

## PENDÊNCIAS PRÓXIMA SPRINT
1. skill salvar + skill cerebro (bloqueadas até OpenClaw religar / 1-jul).
2. Diagnóstico: lote de correções + 3 perguntas IRIS + migrar VPS.
3. Dashboard: hospedar VPS (nginx+senha, Davison+Guilherme).
4. Roteiros v0→v1 (Faixa 1 = porta principal).
5. Verificar AWS Founders $1000; email corp nas candidaturas.
6. Aguardar 19840b + corretores (Teresa/Henrique/Celso).
7. EODs migram p/ GitHub após scrub PII.
