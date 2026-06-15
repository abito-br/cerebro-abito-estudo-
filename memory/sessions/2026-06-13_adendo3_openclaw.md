# Abito_EOD_2026-06-13 (adendo 3 — OpenClaw: causa raiz do gasto + religamento bloqueado)

## CAUSA RAIZ DOS $48 (teto $50 estourado, reseta 1/jul)
- Gateway OpenClaw rodando desde 12/jun na VPS (porta 18789), mesmo sem Telegram ativo.
- Heartbeat padrão 30min mandando SESSÃO PRINCIPAL COMPLETA a cada batida (sem isolamento).
- Cache configurado em janela de 5min — expira entre heartbeats (30min > 5min), então cada batida REESCREVE cache do zero (+25% custo), nunca aproveita leitura barata (10% custo).
- ADICIONAL: estava lendo mensagens do bot "abitonotes" de hora em hora E respondendo pro Davison — outro ciclo de custo não mapeado, somado ao heartbeat.
- AÇÃO TOMADA: processo 40256 morto via SSH (kill). Confirmado sem systemd reiniciando — não volta sozinho. Parado.

## PRÉ-CONDIÇÕES PARA RELIGAR (todas, antes de ligar de novo)
1. Heartbeat com sessões ISOLADAS (sessionTarget: isolated) — não manda histórico completo, só checklist pequeno (HEARTBEAT.md).
2. Cache 1h (não 5min) para blocos fixos (system prompt, AGENTS.md, instruções Abito).
3. Cadência heartbeat: 6h ou diário (não 30min) — estágio atual não precisa de tempo real.
4. UM heartbeat só, checklist pequeno — não múltiplos crons fazendo a mesma janela.
5. REVISAR o ciclo "ler abitonotes de hora em hora + responder Davison" — mapear o que é, decidir se vira item do heartbeat único ou se é descartável. NÃO religar esse ciclo como estava (separado, hora em hora).
6. `openclaw tasks audit` / `openclaw cron list` revisados — listar TUDO que está agendado antes de religar.

## QUANDO RELIGAR
Davison: NÃO decidido. Em aberto — sem data. Pré-condições 1-6 acima bloqueiam religamento até serem desenhadas e revisadas, independente do reset de 1/jul (reset de créditos não é sinal verde automático).

## ESTADO ATUAL
- Gateway parado, não volta sozinho. $5,22 de crédito restante até 1/jul.
- Esta conversa (claude.ai) não consome o spend limit de API — separado.
