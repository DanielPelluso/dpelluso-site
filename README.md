# dpelluso-site

Site institucional **dpelluso.com.br** — hospedado no **Cloudflare Pages**.

## Estrutura

```
/                                      → institucional (DPelluso + cards Controle Pro/TimeRank)
/timerank/                              → placeholder (depois: Flutter web)
/timerank/politica-de-privacidade/      → política TimeRank
/timerank/termo-de-uso/                 → termos TimeRank
/controlepro/                          → placeholder + download do setup
/controlepro/politica-de-privacidade/  → política Controle Pro
/controlepro/termo-de-uso/             → termos Controle Pro
/downloads/ControlePro-Setup-1.0.0.exe
_redirects                             → SPA fallback p/ Flutter web futuro
```

## Deploy

```powershell
npx wrangler pages deploy . --project-name dpelluso-site --branch main
```

Token: env User `CLOUDFLARE_API_TOKEN` (nunca commitar).

## URLs oficiais (referenciar em apps/lojas)

- https://dpelluso.com.br/timerank/politica-de-privacidade
- https://dpelluso.com.br/timerank/termo-de-uso
- https://dpelluso.com.br/controlepro/politica-de-privacidade
- https://dpelluso.com.br/controlepro/termo-de-uso
