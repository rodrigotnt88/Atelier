# Configuração de pixels — Atelier Ashley Medina

A implementação suporta, com consentimento explícito:

- Meta Pixel / Facebook Pixel;
- Google Analytics 4 e eventos compatíveis com Google Ads;
- TikTok Pixel.

## Configurar os IDs

No `index.html`, preencher os três atributos do script `atelier-analytics-config`:

```html
<script id="atelier-analytics-config"
  data-meta-pixel-id="SEU_META_PIXEL_ID"
  data-ga-measurement-id="G-SEU_ID"
  data-tiktok-pixel-id="SEU_TIKTOK_PIXEL_ID"></script>
```

Os IDs são identificadores públicos de medição. Nunca colocar neste ficheiro tokens de API, passwords ou chaves privadas.

## Eventos enviados

Só depois de o visitante aceitar analytics:

| Ação | Meta | GA4 | TikTok |
|---|---|---|---|
| Entrada na página | `PageView` | `page_view` | `page` |
| Clique em WhatsApp | `Contact` | `contact` | `Contact` |
| Formulário válido enviado para WhatsApp | `Lead` | `generate_lead` | `SubmitForm` |

Os eventos não enviam nome, telefone, email, mensagem ou data. O formulário continua a enviar os dados diretamente para o WhatsApp, sem armazenamento no site.

## Consentimento

- Sem escolha, o banner é mostrado.
- `Aceitar analytics` carrega os fornecedores e grava a preferência localmente.
- `Recusar` impede o carregamento.
- Para testar de novo no browser: `window.amAnalytics.reset()` na consola.

## Validação antes do lançamento

1. Preencher os IDs.
2. Abrir o site numa janela privada.
3. Confirmar que nenhum fornecedor é carregado antes de aceitar.
4. Aceitar analytics e verificar os eventos no Meta Test Events, DebugView do GA4 e TikTok Events Manager.
5. Testar clique no WhatsApp e submissão válida do formulário.
6. Confirmar que nenhum dado pessoal aparece nos payloads de analytics.
