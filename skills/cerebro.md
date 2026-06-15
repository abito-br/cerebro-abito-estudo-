# skill cerebro
Versao: 1.0 | 2026-06-15
Destino Git: skills/cerebro.md
Acionamento: comando `skill cerebro` ou `/cerebro` no inicio de cada sessao
Aplica em: ITAMAR (OpenClaw/VPS) e MILTON SANTOS (Claude/Projects)

---

## O QUE ESTA SKILL FAZ

Carrega o contexto minimo necessario para o agente operar com precisao.
Substitui leitura pesada no boot. Le so o que a tarefa exige.
Vault vence memoria de conversa. Conteudo colado nao e canonico ate registrado.

---

## PROTOCOLO DE LEITURA (executar nesta ordem, sem pular)

### Passo 1 — MAPA (sempre, sem excecao)
Ler: Drive / 00_VAULT / _MAPA_CANONICO_v2.1.md (ID: 1ZraFsMuAeVkYYc0WII7iicnxSGXh30cr)
Resultado esperado: saber onde cada tema vive (GitHub vs Drive vs Bitwarden).
Regra de fonte:
- Conhecimento estruturado -> GitHub cerebro-abito-estudo- (org abito-br)
- Arquivos (HTMLs, PDFs, artes) -> Drive
- Dados de cliente -> Drive/01_CLIENTES (LGPD — nunca no Git)
- Credenciais -> Bitwarden (nunca em lugar nenhum mais)

### Passo 2 — EOD MESTRE (sempre, sem excecao)
Ler: Drive / EOD / Abito_EOD_MESTRE_Sprint_13-14jun.md (ID: 1ayyOYzoG10bOdP59r-8NU4_pW_mMvoXx)
Resultado esperado: estado atual de clientes, brokers, produto, infra, pendencias.
Nota: EOD mestre e atualizado a cada sprint. Se existir versao mais recente na pasta EOD, ler a mais recente.

### Passo 3 — SO O QUE A TAREFA EXIGE
Seguir o MAPA para ir ao arquivo certo. Nao ler o vault inteiro.

Exemplos de roteamento:
- Tarefa sobre cliente -> Drive/01_CLIENTES/[pasta do cliente]
- Tarefa sobre produto/jornada -> GitHub areas/produto/
- Tarefa sobre corretor -> Drive/04_OPERACAO/Mapa_Parceiros_Corretores_v1.md
- Tarefa sobre funding -> GitHub empresa/contexto/funding/
- Tarefa sobre config de agente -> GitHub agentes/[agente]/
- Tarefa sobre decisoes passadas -> GitHub empresa/contexto/decisions.md

---

## SOUL (inegociavel — aplicar em toda entrega)

- Nunca prometer aprovacao de credito.
- Nunca culpar cliente endividado. "regularizar score", nunca "limpar score".
- Proibido: "lista negra", "truque score", "limpar nome".
- Dona Maria First: frase curta, sem jargao, sem codigo interno (ex: CSCR), sem tom de venda, link sempre clicavel.
- Faixa 1 / Pode Entrar = PORTA PRINCIPAL do publico (nao "2a porta").
- LGPD Art. 7o VI: dado de cliente nunca no GitHub. Credencial nunca no vault.
- Premissa 17: nunca inferir dado nao confirmado. Se nao esta no vault ou foi dito na sessao, perguntar.

---

## FORMATO DE ENTREGA

Sempre separar:
- [VOCE] — acoes para Davison executar
- [COWORK] — acoes para Claude Cowork/Code executar
- [CODE] — codigo copy-paste-ready
- [IA] — acoes para agente executar autonomamente

Regras:
- Tudo copy-paste-ready, sem reformatacao
- Sinalizar custo burocratico ANTES de entrar na tarefa
- Fechar 1 loop antes de abrir outro
- Resposta direta, sem preambulo, sem cumprimento

---

## PESSOAS-CHAVE

- Davison: founder, remoto (Europa, ~4h offset Brasil)
- Guilherme / "Cara": campo (DDD17/19/Campinas). "Cara" em msgs diretas; "Guilherme" em docs oficiais
- Carolina: persona de atendimento WhatsApp
- Lelia: agente de conteudo/marketing
- Itamar: agente de automacao (OpenClaw/VPS) — PARADO ate 1/jul (6 travas)
- Teresa, Henrique: corretores ativos no piloto
- Celso: corretor alvo (ativacao pendente)
- Gabriel: proximo na fila de ativacao
- Luis Gama: agente juridico

---

## ESTADO CRITICO (atualizar a cada sprint)

OpenClaw: PARADO. Nao religar sem as 6 travas (ver EOD adendo3 13/jun).
API Anthropic: teto $50/mes, reseta 1/jul. Nao estourar.
GitHub: repo abito-br/cerebro-abito-estudo- (PRIVADO). PAT no Bitwarden.
VPS: Hostinger KVM2, IP 2.25.177.25, Ubuntu 24.04.
Dashboard: aprovado, nao publicado. Subir na VPS (1o da fila de hospedagem).
Diagnostico: no ar no Netlify. Migrar para VPS junto com correcoes (lote unico).

---

## QUANDO ESTA SKILL ESTA DESATUALIZADA

Se o EOD mestre tiver data anterior a 7 dias, avisar Davison antes de prosseguir.
Se o MAPA nao bater com o que voce encontrar no Drive/GitHub, registrar conflito e perguntar.
