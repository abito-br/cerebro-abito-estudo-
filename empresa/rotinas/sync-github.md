# sync-github.md — Rotina Diaria

Frequencia: 1x/dia 21h BRT

Comando:
cd /root/cerebro-abito && git add -A && git commit -m "sync diario $(date +%Y-%m-%d)" && git push origin main

Entrega: silencioso se nada mudou, mensagem no Telegram se houve mudancas.
