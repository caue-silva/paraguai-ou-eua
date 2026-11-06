# paraguaioueua.com.br

Landing page estática (HTML + CSS + JS inline, sem build). Deploy direto na Vercel.

## Arquivos

| Arquivo | Para quê |
|---|---|
| `index.html` | A página inteira (CSS e JS inline) |
| `robots.txt`, `sitemap.xml`, `llms.txt` | SEO e crawlers de IA |
| `og-image.png` | Imagem de compartilhamento 1200x630 |
| `logo.png`, `favicon.svg`, `favicon-48.png`, `apple-touch-icon.png` | Ícones e logo do publisher (schema) |
| `vercel.json` | Cabeçalhos de segurança e cache |
| `design/` | Modelos HTML usados para gerar a imagem OG e o logo (não vão para o deploy) |

## Onde editar datas, preços e IDs

Tudo fica no objeto `window.PEU_CONFIG`, no `<head>` do `index.html`:

- `blackFriday.fimISO`: fim da promoção (hoje `2026-11-28T04:59:00Z` = 27/11 às 23h59 em Orlando)
- `precos`: preços normais e de Black Friday
- `analytics.ga4Id`, `analytics.googleAdsId`, `analytics.googleAdsConversionLabel`: preencha para ativar o GA4 e a conversão do Google Ads. Vazio = nenhum script do Google carrega.

Cada clique em CTA dispara `cta_click` (GA4) e `conversion` (Google Ads). O play do vídeo dispara `video_play`.

## Testar o fim da Black Friday

Abra a página com `?simular=2026-11-28T05:00:00Z` no fim da URL. Outra opção é mudar `fimISO` para uma data passada.

## Regerar a imagem OG

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars --window-size=1200,630 --virtual-time-budget=6000 --screenshot="$PWD/og-image.png" "file://$PWD/design/og-template.html"
```
