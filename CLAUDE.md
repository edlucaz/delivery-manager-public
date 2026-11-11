# CLAUDE.md — delivery-manager-public

## O que é

Repositório **público, só de documentação**: vitrine do Delivery Manager (SaaS multitenant de delivery) com README, README do legado Django e screenshots. Não contém código-fonte; o código real é o `Web/technov-saas` (privado). A demo interativa da versão atual fica em `Web/delivery-manager-showcase-new`.

## Comandos

Não há. Edita-se só Markdown e imagens em `screenshots/`.

## Arquitetura

- `README.md` (versão atual: Next.js + FastAPI), `README-django.md` (legado) e `screenshots/`.
- Branches remotas: `main` (atual) e `legacy` (histórico da versão Django).

## Deploy

Nenhum. A página é o próprio README no GitHub. Os links dele apontam para a Vercel (showcase) e o Render (Django legado, dorme e leva ~30 s para acordar).

## O que nunca vai pro git

- **Este repo é público**: nunca colocar código proprietário, `.env*`, credenciais, URLs internas, nomes de clientes reais ou dados reais nos screenshots.

## Regras do projeto

- Docs em pt-BR. Commits: Conventional Commits em pt-BR (histórico antigo não segue).
- Conferir se os links de demo do README ainda respondem antes de divulgar.
- Padrão de todos os projetos: `/mnt/backup500gb/Projetos/_padrao/PADRAO.md` (nível leve).
