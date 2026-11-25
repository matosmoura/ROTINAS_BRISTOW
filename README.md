# Rotina Bristow

App de checklists da rotina AW139, do início do dia até após o pouso: chegada na base, inspeções
externa e interna, Preflight, Before Start, Before Takeoff, cruzeiro, chegada, pouso e
After Landing/Shutdown, com figuras interativas (LSP/RSP), progresso e marcações salvas no aparelho.

**Link:** https://matosmoura.github.io/ROTINAS_BRISTOW/

## Instalar

- **Android** (Chrome): menu ⋮ → **Instalar app** / **Adicionar à tela inicial**
- **iPhone / iPad** (Safari): Compartilhar → **Adicionar à Tela de Início**
- **Computador** (Chrome / Edge): ícone de instalar na barra de endereço

Depois do primeiro acesso o app funciona sem internet. As marcações ficam salvas no próprio
aparelho/navegador (`localStorage`, chave `bristow_rotina_v1`).

## Estrutura

```
index.html            # app (arquivo único, figuras WebP embutidas) + tags PWA
manifest.webmanifest  # nome, ícones e cores do app instalado
sw.js                 # cache offline (rede primeiro, cópia guardada como reserva)
icons/                # ícones gerados por tools/icons.py
```

Para atualizar o conteúdo com uma nova versão do HTML, substitua `index.html` mantendo o bloco
`<!--PWA ...-->` logo após o `<title>` e o `<script>` do service worker antes do `</body>`.
Ao mudar arquivos além do `index.html`, aumente a versão em `CACHE` no `sw.js`.

Para mudar o ícone, edite `tools/icons.py` e rode `python3 tools/icons.py`.

## Publicação (GitHub Pages)

Ativação (uma vez): Settings → Pages → Build and deployment → Source: **Deploy from a branch**,
Branch: **main** / **(root)** → Save. Cada push no `main` atualiza o site em cerca de 1 minuto.
