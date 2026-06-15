# skill salvar
Versao: 1.0 | 2026-06-15
Destino Git: skills/salvar.md
Acionamento: comando `skill salvar` ou `/salvar` ao fim de cada sessao
Aplica em: ITAMAR (OpenClaw/VPS) e MILTON SANTOS (Claude/Projects)

---

## O QUE ESTA SKILL FAZ

Classifica tudo que foi gerado na sessao e salva no lugar certo.
Elimina arquivos caindo fora do lugar por falta de classificacao.
Base: Pixel M04 "processamento de notas" — regra de onde cada coisa vai, executada como skill.

---

## TABELA DE CLASSIFICACAO (decide tudo)

| Tipo de conteudo | Destino | Observacao |
|---|---|---|
| Decisoes, aprendizados, contexto de negocio | GitHub empresa/contexto/ | decisions.md ou lessons.md |
| Produto, jornada, roteiros base, arvore de decisao | GitHub areas/produto/ | Nunca roteiro de cliente especifico |
| Marketing, atendimento, operacoes (estruturado) | GitHub areas/ | Pasta correspondente |
| Config de agente | GitHub agentes/[agente]/ | |
| EOD / log de sessao | GitHub memory/sessions/ | Nome: YYYY-MM-DD_eod.md |
| Handoff entre agentes | Drive 05_IAs/Briefings/ | Tambem commitar em memory/sessions/ |
| Artes, PNGs, HTMLs, PDFs, ZIPs | Drive 02_CRESCIMENTO/ | Subpasta correta |
| Dashboard / painel HTML | Drive (artefato) -> VPS | Nao e conhecimento, e arquivo |
| Diagnostico HTML | Drive (artefato) -> VPS | Idem |
| Skill de agente | GitHub skills/ | Este arquivo e um exemplo |
| Dado de cliente (nome, tel, ficha, mapa) | Drive 01_CLIENTES/[cliente]/ | LGPD — NUNCA no GitHub |
| Roteiro especifico de cliente | Drive 01_CLIENTES/[cliente]/ | Idem |
| Credencial, senha, token, chave API | Bitwarden | NUNCA em nenhum arquivo |
| Prompt de abertura / embriao de skill | Drive EOD/ (staging) | Ate ter lugar definitivo no Git |

---

## PROTOCOLO DE EXECUCAO

### 1. Listar o que foi gerado na sessao
Para cada item gerado, identificar:
- Tipo (ver tabela acima)
- Destino (Drive ou GitHub, pasta especifica)
- Nome do arquivo (seguir convencao existente)

### 2. Verificar conflitos antes de salvar
- Ja existe arquivo com esse nome/conteudo? Versionar (v2, v3) ou sobrescrever?
- O conteudo tem dado de cliente? Se sim, Drive/01_CLIENTES — nao pode ir pro Git.
- O conteudo tem credencial? Nao salvar em lugar nenhum — orientar Davison a colocar no Bitwarden.

### 3. Salvar na ordem certa
1. Dados de cliente -> Drive primeiro (prioridade LGPD)
2. EOD -> GitHub memory/sessions/
3. Conhecimento estruturado -> GitHub pasta correta
4. Arquivos -> Drive pasta correta

### 4. Registrar o que foi salvo no EOD da sessao
Secao [ITAMAR] do EOD deve listar:
- O que foi salvo
- Onde foi salvo (caminho + ID se Drive)
- O que ficou pendente para Cowork/manual

---

## CONVENCAO DE NOMES

EODs: YYYY-MM-DD_eod.md
Consolidados: YYYY-MM-DD_YYYY-MM-DD_consolidado.md
Decisoes: adicionar entrada em decisions.md (nao criar arquivo novo por decisao)
Skills: skill_[nome].md (minusculo, sem acento)
Handoffs: HANDOFF_[origem]_para_[destino]_YYYY-MM-DD.md

---

## O QUE ESTA SKILL NAO FAZ

- Nao move arquivos no Drive (conector Drive nao deleta/move — fazer via Cowork ou na mao)
- Nao commita no GitHub (fazer via Cowork ou git manual)
- Nao decide o que e importante — classifica e roteia, Davison decide se descartar

---

## SAIDA ESPERADA DA SKILL

Ao fim da execucao, gerar bloco copy-paste para Davison / Cowork:

[SALVO AGORA — Drive]
- [nome do arquivo] -> [pasta Drive] (ID: xxx)

[PARA COWORK — GitHub]
- [nome do arquivo] -> [caminho Git] | conteudo: [resumo 1 linha]

[PENDENTE — manual]
- [item que nao foi possivel salvar automaticamente]
