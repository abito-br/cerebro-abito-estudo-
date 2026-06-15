# EOD — Abito Design System + Pipeline de Reels

**Data:** 26/mai/2026
**Status:** Design System completo · Reel P25 (Dia 4) entregue · Reel G04 (Dia 6) pronto pra rodar amanhã 12h

---

## 1. O que foi entregue no projeto

Pasta completa do design system, baseada em DNA + paleta + logo originais.

### Estrutura
```
/
├── README.md           brand, content, visual, iconografia
├── SKILL.md            entrada pra Claude Code / Agent Skills
├── colors_and_type.css tokens (cores, type, espaço, sombras, motion)
├── assets/             logo, wordmark, paleta
├── docs/               DNA.md, marketing-personas.md, identidade original
├── preview/            16 cards do Design System tab
├── ui_kits/plano-da-chave/  B2C: Landing · WhatsApp · Calculadora · Diagnóstico
└── reels/              dia04 (P25) e dia06 (G04) prontos com PNGs + roteiros
```

### Decisões aplicadas
- **CTA âmbar sem glow.** Sombra plana `0 2px 4px rgba(38,40,42,.10)`. Motivo: glow lê como propaganda; o público já foi queimado por crédito fácil.
- **Trust strip inflado removido.** Em vez de "100% / 3min / SCR", a landing mostra 3 linhas honestas:
  1. Não custa nada pra você.
  2. A gente não promete aprovação. Promete te organizar e te dizer a verdade.
  3. Você fala, a gente escuta e diz se dá. Sem compromisso.
- **Caixa-Bot reescrita.** Abre com "Oi, aqui é o time da Abito. Me conta sua situação que a gente vê, sem custo, se dá pra chegar no financiamento. Pode falar à vontade."
- **Diagnóstico reescrito.** "Hoje ainda não dá. Em uns 6 meses, dá pra tentar."
- **Teste da voz alta virou regra-mestra** no README e SKILL.md.
- **Referência de tom:** Calma e limpa como o Nubank, mas mais quente e menos tech. Clareza de gov.br com acolhimento. Sensação de cooperativa de cidade pequena.

---

## 2. Pipeline de Reels — fluxo definitivo

### Por que NÃO usamos o pipeline Python pra montar o vídeo
O `video.py` do pipeline gera fundo verde sólido + chave geométrica simples + legendas animadas. Ele IGNORA os 6 PNGs do design. **Decisão:** usar só a parte do TTS do pipeline; montar o vídeo manualmente via ffmpeg com os 6 PNGs do design.

### Estrutura narrativa dos 6 frames (padrão replicável)

| # | Beat | Fundo | Função |
|---|---|---|---|
| 1 | HOOK | creme | Para o dedo. Frase de impacto em 3 linhas. |
| 2 | DOR | verde raiz | "Se já te passou". Empatia, não pena. |
| 3 | REVELAÇÃO | carvão | A virada. Frase em âmbar destaca o insight. |
| 4 | COMPARAÇÃO | creme | **Coração do Reel.** 2 cards empilhados (verde vs carvão), círculo "vs" no meio. |
| 5 | AÇÃO | verde raiz | O que fazer agora. Caixa com número grande. |
| 6 | CTA | verde raiz | Logo grande + @abito.br + gancho de "amanhã". |

### Tempos padrão (somam 40s; áudio Azure cai em ~38-39s)
```
f1 hook      4s
f2 dor       7s
f3 revelacao 7s
f4 comparacao 9s  <- coração, mais tempo
f5 acao      6s
f6 cta       7s
```

---

## 3. Alterações no pipeline antes de rodar Dia 6

### 3.1 Trocar a voz (URGENTE)
1. Abre `tts.py` na pasta do pipeline.
2. Troca `FranciscaNeural` por `ThalitaNeural`.
3. Salva.

**Alternativas:** `pt-BR-YaraNeural`, `pt-BR-LeticiaNeural`, `pt-BR-AntonioNeural`

### 3.2 Armadilha do frames.txt no Windows (BOM)
```powershell
$c = "file 'f1.png'`nduration 4`nfile 'f2.png'`nduration 7`nfile 'f3.png'`nduration 7`nfile 'f4.png'`nduration 9`nfile 'f5.png'`nduration 6`nfile 'f6.png'`nduration 7`nfile 'f6.png'`n"
[System.IO.File]::WriteAllText("$PWD\frames.txt", $c, (New-Object System.Text.UTF8Encoding($false)))
```

---

## 4. Erros encontrados hoje

| Erro | Causa | Solução |
|---|---|---|
| `Permission denied` no frames.txt | Pasta `G:\Meu Drive\` trava arquivos pro ffmpeg | Trabalhar em pasta local tipo `C:\Users\User\Desktop\abito-p25\` |
| `-c: não é reconhecido` | Comando ffmpeg com `\` quebrando linha no PowerShell | Rodar o ffmpeg em **uma linha só** |
| `unknown keyword '﻿file'` | BOM no `frames.txt` | Criar com `WriteAllText` |
| `Invalid PNG signature` | Arquivos salvos como HTML com extensão `.png` | Exportar PNGs de verdade |
| MP3 vazio | MP3 ainda não foi gerado pelo TTS | Rodar o pipeline primeiro |

---

## 5. Sequência completa pra cada novo Reel

```powershell
# 1) Copia o Dia_XX.txt do zip pra pasta roteiros/ do pipeline
copy Dia_XX.txt <pasta_pipeline>\roteiros\

# 2) Roda o TTS via pipeline
cd <pasta_pipeline>
python pipeline.py --test Dia_XX --force

# 3) Move o MP3 pra pasta local de trabalho
copy temp\Dia_XX.mp3 C:\reels\diaXX\locucao.mp3

# 4) Vai pra pasta local
cd C:\reels\diaXX

# 5) Confere o tempo
ffprobe -i locucao.mp3 -show_entries format=duration -v quiet -of csv="p=0"

# 6) Gera o vídeo (UMA LINHA SÓ)
ffmpeg -f concat -safe 0 -i frames.txt -i locucao.mp3 -c:v libx264 -pix_fmt yuv420p -vf "scale=1080:1920,format=yuv420p" -r 30 -c:a aac -b:a 128k -movflags +faststart -shortest CODIGO.mp4
```

---

## 6. O que falta entregar (15 Reels)

| Dia | Data | Hora | Código | Status |
|---|---|---|---|---|
| 5 | Ter 27/mai | 19h | P09 | ✅ Entregue |
| 6 | Qua 28/mai | 19h | G04 | ✅ Pronto pra rodar |
| 7 a 20 | … | … | … | ⏳ |

---

## 7. Caveats
- UI kit não é réplica do produto real — derivado do DNA + board visual.
- Iconografia provisória (Lucide).
- Imagens fotográficas: não temos.
- Voz ainda é TTS. Migrar pra ElevenLabs (~US$5/mês) quando estabilizar.
