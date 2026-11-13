# AGENTS.md — dpelluso-site

Memória técnica permanente do site **dpelluso.com.br**. Leia este arquivo antes de qualquer alteração e atualize-o quando uma decisão importante for tomada.

---

## 1. Objetivo

Site institucional da **DPelluso** (página raiz), com seções dos apps **Controle Pro** e **TimeRank**, hospedagem das **políticas LGPD** (5 URLs oficiais — inclui a genérica do site) e **download do setup** do Controle Pro. Futuras versões web dos apps (Flutter web) vão para `/timerank` e `/controlepro`.

**URLs oficiais (usar sempre estas — sem `.html`, com barra no final servida pelo Pages):**

| Página | URL |
|---|---|
| Política genérica (site/AdSense) | `https://dpelluso.com.br/politica-de-privacidade` |
| Política TimeRank | `https://dpelluso.com.br/timerank/politica-de-privacidade` |
| Termos TimeRank | `https://dpelluso.com.br/timerank/termo-de-uso` |
| Política Controle Pro | `https://dpelluso.com.br/controlepro/politica-de-privacidade` |
| Termos Controle Pro | `https://dpelluso.com.br/controlepro/termo-de-uso` |
| Setup Controle Pro | `https://dpelluso.com.br/downloads/ControlePro-Setup-1.0.0.exe` |

## 2. Infraestrutura

- **Hospedagem:** Cloudflare Pages, projeto `dpelluso-site`, production branch `main`, deploy via `npx wrangler pages deploy .` (env User `CLOUDFLARE_API_TOKEN` — **nunca commitar**).
- **Domínio:** apex `dpelluso.com.br` (zona Cloudflare); `www` → apex (Redirect Rule 301).
- **DNS/Email Routing:** zona Cloudflare de `dpelluso.com.br` (o mesmo projeto que recebe os e-mails de `timerank@`/`controlepro@`).
- **Repo GitHub:** `DanielPelluso/dpelluso-site` (público).
- **Estilo:** HTML estático puro (sem build), visual consistente com as políticas — navy `#00235D`, fonte system-ui.
- **`_redirects`:** hoje só os **301 legados** `/futrank` → `/timerank` (prefixos diferentes, sem loop). Wildcards SPA virão com o Flutter web futuro; as 4 políticas são arquivos estáticos com precedência natural.

## 3. Pendências

- [ ] **AdMob:** usuário precisa atualizar a URL da política de privacidade dos 2 apps (Controle Pro e TimeRank) para as URLs novas acima. Até lá, `github.io/politicas-apps` continua no ar **de propósito** — **não remover/redirecionar** o repo `politicas-apps` sem combinar.
- [ ] **Play Store:** idem, campo de política de privacidade nos listings.
- [ ] **Flutter web** em `/timerank` e `/controlepro` (próxima fase; build com `base href` da seção).
- [ ] **Logo DPelluso** na página institucional (usuário vai criar; hoje é placeholder textual).
- [x] ~~Atualizar seed `app_config.privacy_policy_url` do TimeRank e `AboutLinks` para as URLs novas.~~ **FEITO (03/11/2026):** migration `20261103000001` aplicada no banco + `AboutLinks` = `dpelluso.com.br/timerank/...`.

## 4. Regras

1. **Nunca commitar** tokens (`CLOUDFLARE_API_TOKEN`, GitHub PAT, etc.) — só em env vars User/CI.
2. Conteúdo das políticas é **texto jurídico do usuário**; alterações de redação só com aprovação dele.
3. Manter URLs canônicas estáveis (AdMob/Play/`app_policies.dart`/`AboutLinks` apontam para elas).
4. Setup novo do Controle Pro: substituir em `downloads/`, atualizar tamanho no botão do `/controlepro/index.html` e versionar no nome do arquivo se o usuário pedir.
5. Deploy = commit em `main` + `wrangler pages deploy`. Conferir as 4 URLs + raiz depois de cada deploy.

## 5. Comandos

```powershell
# Deploy
npx wrangler pages deploy . --project-name dpelluso-site --branch main

# Status do projeto
npx wrangler pages project list
```

## 6. Histórico de decisões

- **2026-11-02:**-site nasce em Cloudflare Pages (não Google Sites — este não hospeda Flutter web em subpaths). Repo novo `dpelluso-site`. Políticas migradas do `politicas-apps` (GitHub Pages); termo de uso do TimeRank **criado** (não existia). Setup (18,7 MB) hospedado no próprio Pages (limite 25 MiB). `github.io` mantido vivo até atualizar AdMob/Play.
- **2026-11-03:** rename FutRank → TimeRank no site inteiro (textos, e-mails `timerank@`, pasta `futrank/` → `timerank/`) + 301 `/futrank/*` → `/timerank/*` em `_redirects` (commit `8c46b83`, deployado e validado: 3 URLs novas 200, 3 antigas 301).
- **2026-11-13:** **AdSense/verificação do domínio (decisão 141 — site):** `ads.txt` criado na raiz (`google.com, pub-2846999130163437, DIRECT, f08c47fec0942fa0` — opção 2 do painel AdSense, cobre o domínio todo) + página genérica **`/politica-de-privacidade/`** (sem citar apps; foco AdSense/cookies; e-mail `suportepelluso@gmail.com`) linkada no rodapé da home. Snippet AdSense (opção 1) já existia só em `/timerank/`. `/controlepro/` continua sem snippet — quando quiser anúncios lá, adicionar snippet + unidade nesse repo.
