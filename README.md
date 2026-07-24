# MDG Shorts Studio

Gerador de vídeos curtos (Shorts / Reels / TikTok) com IA: a partir de um tema,
ele cria o **roteiro**, busca os **materiais de vídeo**, gera a **narração** e as
**legendas**, e monta um vídeo vertical em alta definição — tudo por uma
interface no navegador, rodando localmente na sua máquina.

Baseado no projeto open-source
[MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) (licença MIT).
A documentação original está preservada em `README-original-cn.md` e
`README-en.md`.

---

## 🚀 Rodar em 1 minuto (com um assistente de IA no terminal)

Este projeto foi pensado para ser instalado com a ajuda de um assistente de IA
(ex.: **Claude Code**). Abra o assistente na pasta onde clonou o repositório e
cole o pedido abaixo:

> Instale e rode este projeto. Passos:
> 1. Instale o `uv` (gerenciador de pacotes Python da Astral) se ainda não existir.
> 2. Na raiz do projeto, rode `uv sync` (isso baixa o Python 3.11 e todas as dependências, isolado — não afeta outros Pythons da máquina).
> 3. Suba a interface: no Windows rode `webui.bat`; no Linux/Mac rode `./webui.sh`.
> 4. Abra **http://127.0.0.1:8501** no navegador.

O assistente cuida de tudo. O FFmpeg (que monta o vídeo) já vem embutido nas
dependências — não precisa instalar nada à parte.

---

## 🛠️ Rodar manualmente (passo a passo)

**Pré-requisito:** ter o [`uv`](https://docs.astral.sh/uv/) instalado.

```bash
# 1. Instalar o uv (caso não tenha)
#    Windows (PowerShell):
#      irm https://astral.sh/uv/install.ps1 | iex
#    Linux / macOS:
#      curl -LsSf https://astral.sh/uv/install.sh | sh

# 2. Instalar Python 3.11 + dependências (isolado em .venv)
uv sync

# 3. Subir a interface
#    Windows:
webui.bat
#    Linux / macOS:
./webui.sh
```

Depois abra **http://127.0.0.1:8501** no navegador.

---

## 🔑 Configuração (só 2 chaves para começar)

Na interface, clique em **Ajustes** e preencha:

1. **Provedor de LLM** (gera o roteiro) — escolha um provedor e cole a **chave de
   API**. Opção gratuita popular: **Google Gemini**
   (<https://aistudio.google.com/app/apikey>).
2. **Pexels** (banco de vídeos) — cole a **chave de API** em *APIs de materiais*.
   Cadastro gratuito: <https://www.pexels.com/api/>.

A **narração** (Edge TTS, da Microsoft) e as **legendas** já funcionam de graça,
sem precisar de chave.

> As chaves ficam salvas em `config.toml` na sua máquina. Esse arquivo é ignorado
> pelo Git (não é enviado ao repositório) — cada pessoa usa as próprias chaves.

### Publicação automática (opcional)

Na aba **Ajustes → Publicação** dá para conectar o
[Upload-Post](https://upload-post.com/) e publicar automaticamente no TikTok,
Instagram e YouTube. É opcional — se não configurar, os vídeos ficam só para
download.

---

## 🎬 Como usar

A tela de criação tem **4 fases** (abrem uma por vez):

1. **Roteiro** — escreva o tema e o idioma do conteúdo (há opções com foco em
   públicos de CPM alto no YouTube).
2. **Vídeo** — fonte dos materiais (Pexels), formato, transições.
3. **Narração** — voz e velocidade.
4. **Legendas** — fonte, cor, posição.

Ao final, clique em **Gerar Vídeo**.

## 📁 Onde ficam os vídeos

O vídeo pronto aparece **na própria interface** (player + botão de download) e
também é salvo em disco em:

```
storage/tasks/<id-da-tarefa>/final-1.mp4
```

Sem o Upload-Post configurado, nada é publicado automaticamente — o vídeo fica
disponível para você baixar e usar.

---

## ℹ️ Notas

- **Idioma da interface:** fixado em Português.
- **Idioma do vídeo:** escolhido por vídeo, na fase *Roteiro*.
- **Fontes de legenda:** o projeto acompanha fontes com cobertura latina
  (BeVietnamPro, Charm, UTM Kabel) adequadas aos idiomas suportados.
