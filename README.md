# dpelluso-site

Site institucional **dpelluso.com.br** — hospedado no **Cloudflare Pages**.

## Estrutura

```
/                                      → institucional (DPelluso + cards Controle Pro/FutRank)
/futrank/                              → placeholder (depois: Flutter web)
/futrank/politica-de-privacidade/      → política FutRank
/futrank/termo-de-uso/                 → termos FutRank
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

- https://dpelluso.com.br/futrank/politica-de-privacidade
- https://dpelluso.com.br/futrank/termo-de-uso
- https://dpelluso.com.br/controlepro/politica-de-privacidade
- https://dpelluso.com.br/controlepro/termo-de-uso
