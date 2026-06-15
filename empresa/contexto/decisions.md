# decisions.md — Decisoes Estrategicas

## 2026-06-06

Gestao de trafego: automatizar internamente — nao terceirizar
Motor VPS: claude-sonnet-4-6 + Perplexity como busca
SSH via chave ED25519 — sem senha

## 2026-06-05

Guilherme = nome nos documentos
Carolina = atendente WA
Itamar = agente orquestrador VPS

## 2026-06-03

Dona Maria nunca paga — principio canonico
Prazo reporte corretor: 30 dias do fechamento
Aceite contrato corretor: clickwrap no app

## 2026-06-13 (consolidado EODs 11-13/jun)

### Infra / Custo / Automação
- SEM Make / SEM n8n por enquanto. [repo pode dizer Make — corrigir]
- NÃO comprar chave OpenAI. memorySearch do OpenClaw DESLIGADO de vez (fora do stack: Claude=motor, Perplexity=busca).
- NÃO existe serviço systemd do Itamar. OpenClaw imprime "Restarted systemd service" mas é COSMÉTICO — sem persistência a reboot garantida. Saída de ferramenta ≠ estado real.
- OpenClaw/Itamar: PARADO (13/jun). Causa raiz dos $48: gateway em loop + heartbeat 30min sem isolamento + cache 5min reescrito + ciclo lendo "abitonotes" hora em hora. Processo morto via kill, não volta sozinho.
- Teto API Anthropic = $50/mês, reseta 1/jul. Religar Itamar SÓ com 6 travas: (1) heartbeat isolado, (2) cache 1h p/ blocos fixos, (3) cadência 6h/diário, (4) heartbeat único, (5) revisar ciclo abitonotes, (6) auditar tudo agendado. Sem data definida.

### Stack / Ferramentas
- Clientes/operação = planilha + dashboard (painel_abito.html). Supabase = futuro, quando escalar.
- Diagnóstico no ar: capta lead via Netlify Forms + UUID client-side (crypto.randomUUID). NÃO usa Supabase hoje. Lead não se perde mesmo sem clique no WhatsApp.
- HOSPEDAGEM consolidando na VPS Hostinger, FASEADO: dashboard → diagnóstico → sites institucionais. Netlify desativado ao fim.
- Gmail: resposta automática de férias estava ON disparando template de lead em ~200 e-mails de sistema desde 24/mai. DESLIGADA.

### Produto / Jornada
- CORREÇÃO IMPORTANTE (13/jun): para o público ABITO (BPC, renda mínima), FAIXA 1 via cadastro municipal (em SP = PODE ENTRAR, Lei 17.638/2021) é a PORTA PRINCIPAL, não "2ª porta". Inverter roteiros.
- BPC/LOAS dá acesso prioritário ao MCMV Faixa 1 com ISENÇÃO DE PARCELA (FAR/FDS/PNHR). Objeção "não tem renda pra parcela" não se aplica nessa modalidade.
- 3 critérios nacionais de prioridade: área de risco · mulher responsável pela família · pessoa com deficiência.
- Bloqueio 11 (idade x prazo, regra Caixa/SFH 80a6m) = oficial na taxonomia. Fonte: Luis Gama 10/jun.
- Heurística SAC/PRICE por perfil = RASCUNHO EM QUARENTENA. Nenhuma stat sem fonte nomeada em material público até validar com piloto.
- Triagem ≠ diagnóstico: nenhum veredito sem documento. Pitch = "2 entrando em análise", nunca "2 prontos".
- Mapa de Destravamento (entregue manual no piloto) = feature central da calculadora futura.

### Nomenclatura / Pessoas
- "Cara" = informal/WhatsApp. "Guilherme" = docs/oficial/terceiros.
- Carolina (publica): DORMINDO. Gatilho: 10 casos destravados OU 1 corretor pagante.
- Lélia: sem atividade; skills import aguarda estrutura do cerebro estabilizar.
- Milton Santos e Luís Gama: agentes a ativar (Milton no Claude, Luís Gama no Perplexity). NÃO criar pastas no repo até ativar.
