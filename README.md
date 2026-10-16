# Black Friday Colégio CPPEM — página de captura

Landing da live de Black Friday do **Colégio CPPEM**: **sábado, 14/11, às 19h45, ao vivo no YouTube**.
A página capta a **lista VIP** (responsável, WhatsApp, e-mail) e leva o inscrito ao grupo do WhatsApp.

Mesma base técnica da Black Friday de concursos (`../blackFridayCPPEM`), com a identidade do Colégio:
azul-noite `#061a44` / `#10307a`, dourado `#f2b01e` no FRIDAY e nos botões, Nunito + Nunito Sans,
brasão no centro do hero. Tom escolar: sem os efeitos táticos da página de concursos.

## Antes de publicar

| O quê | Onde |
|---|---|
| Canal do YouTube (hoje `@cppemconcursos`) e vídeo agendado da live | `CONFIG.youtubeCanal` / `CONFIG.youtubeLive` + links `youtube.com` no `index.html` |
| Aba da planilha (hoje `BLACK_FRIDAY_COLEGIO`, criada sozinha pelo Apps Script) | `CONFIG.sheetAba` |
| Itens dos cards "lacrados" (Matrícula, Mensalidades, Material, Surpresa) | seção `#lacrados` |
| `og:image` 1200×630 com URL absoluta | `<head>` do `index.html` |

## Comportamento

- **Abertura** (uma vez por sessão): letras do BLACK caem, FRIDAY dourado sobe com um risco de luz e o
  brasão aparece por um círculo de luz. `?abertura=0` pula, `?abertura=1` força.
- **Fases automáticas** a partir de `CONFIG.inicio`: antes / ao vivo / depois (`data-fase-so`).
- **Brasas douradas** subindo pela página (`#brasas`), em pouca quantidade.
- **Prova**: comentários reais de famílias em `assets/prova/`, convertidos em "tinta" e impressos em
  bilhetes de papel rasgado (ouro e branco). Os prints em modo claro (fundo branco) são processados
  invertidos, para a tinta sair igual aos de modo escuro.

## Deploy na Vercel

Projeto estático, sem build (`"framework": null` no `vercel.json`). As imagens ficam em `assets/`, e não
em `public/` — sem framework, a Vercel trata `public/` como pasta de saída e o `index.html` some.
No painel: Framework Preset **Other**, Build Command e Output Directory vazios.

## Medição

Lead no modo **site** (Modelo B): o `script.js` dispara via `pixel_x_app.send_event`. O id do formulário é
`bf-colegio-form`; não cadastre `bf-colegio-submit` como conversão por clique na PixelX.
