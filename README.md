# 🛵 Delivery Manager

> Sistema SaaS multitenant de gestão de delivery — com storefront público, painel administrativo e portal do cliente.

Este repositório é uma **vitrine pública** do projeto. O código-fonte é proprietário e mantido em repositório privado.

[![Next.js](https://img.shields.io/badge/Next.js_15-black?logo=next.js)](https://nextjs.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Django](https://img.shields.io/badge/Django-092E20?logo=django&logoColor=white)](https://djangoproject.com)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)](https://typescriptlang.org)

---

## 🚀 Demos ao vivo

> ⚠️ **As demos utilizam backend simulado com dados fictícios.** Nenhum dado real é processado ou armazenado. O objetivo é demonstrar a interface e o fluxo de uso do sistema real.

| Versão | Stack | Status | Link |
|---|---|---|---|
| **Atual** — Next.js + FastAPI | Next.js 15 · TypeScript · TailwindCSS · shadcn/ui | ✅ Online | [🔗 Ver demo na Vercel](https://delivery-manager-showcase-dvbnpdhmy-edlucazs-projects.vercel.app/) |
| **Legado** — Django | Python 3 · Django · Bootstrap | ✅ Online | [🔗 Ver demo no Render](https://delivery-manager-pbsj.onrender.com/) |

> **Login demo (ambas as versões):** qualquer e-mail e senha funcionam no painel admin e portal do cliente.

---

## 📸 Screenshots

### Painel Administrativo

| Dashboard | Gestão de Pedidos |
|---|---|
| ![Dashboard](./screenshots/admin-dashboard.png) | ![Pedidos](./screenshots/admin-pedidos.png) |

| Cadastro de Produtos | Controle de Estoque |
|---|---|
| ![Produtos](./screenshots/admin-produtos.png) | ![Estoque](./screenshots/admin-estoque.png) |

### Storefront (cliente final)

| Cardápio | Carrinho / Checkout |
|---|---|
| ![Cardápio](./screenshots/storefront-cardapio.png) | ![Checkout](./screenshots/storefront-checkout.png) |

### Portal do Cliente

| Dashboard do cliente | Programa de Fidelidade |
|---|---|
| ![Cliente](./screenshots/cliente-dashboard.png) | ![Fidelidade](./screenshots/cliente-fidelidade.png) |

> 📌 Imagens adicionadas à pasta `screenshots/` do repositório.

---

## 🧩 Funcionalidades

### Painel Administrativo
- Dashboard com métricas em tempo real: vendas, ticket médio, pedidos por hora, top produtos
- Gestão de pedidos com pipeline de status: `pendente → confirmado → preparando → saiu para entrega → entregue`
- Cadastro de produtos com múltiplos tamanhos (300ml, 500ml, 700ml, 1L) e preço único
- Cadastro de categorias e adicionais
- Controle de estoque com histórico de movimentações
- Relatório financeiro básico
- Configurações da loja: horário, taxas, formas de pagamento, cores, logo

### Storefront público
- Cardápio organizado por categorias com busca
- Modal de produto com seleção de tamanho e adicionais
- Carrinho persistente (localStorage)
- Checkout com endereço, forma de pagamento e troco
- Rastreamento de pedido em tempo real

### Portal do Cliente
- Cadastro e login por e-mail ou telefone
- Histórico de pedidos com detalhes
- Gerenciamento de endereços salvos
- Programa de fidelidade com pontos e cartão de selos
- Resgate de recompensas

---

## 🏗️ Versão Atual — Next.js + FastAPI

### Arquitetura

```
Cliente final         Admin / Gerente        Cliente logado
     │                      │                      │
     ▼                      ▼                      ▼
 Storefront             Dashboard              Portal Cliente
     └──────────────────────┼──────────────────────┘
                            │
                     Next.js 15 (Vercel)
                            │
                     FastAPI (Hetzner)
                            │
                    PostgreSQL 16 + Redis 7
```

### Stack técnica

**Frontend**
- Next.js 15 (App Router) + TypeScript
- TailwindCSS + shadcn/ui
- Zustand (estado global) · React Hook Form + Zod (formulários) · TanStack Query (cache e fetching)

**Backend**
- FastAPI (Python 3.12) + SQLAlchemy + Alembic
- PostgreSQL 16 + Redis 7
- WebSockets para atualizações de pedidos em tempo real

**Infraestrutura**
- Vercel (frontend)
- Hetzner CX22 + Coolify + Docker (API e banco)
- Cloudflare R2 (armazenamento de imagens)
- Evolution API (notificações WhatsApp) · Resend (e-mails transacionais) · Stripe + Pagar.me (pagamentos)

### Multitenancy

Cada estabelecimento opera em subdomínio próprio (`loja.dominio.com.br`). Isolamento completo por `tenant_id` em todas as tabelas, com Row Level Security no PostgreSQL garantindo que nenhum tenant acesse dados de outro.

---

## 🗂️ Versão Legado — Django

A versão legado foi o **MVP inicial do produto**, desenvolvida em Django com templates server-side e Bootstrap. Serviu como prova de conceito e validação das funcionalidades principais antes da reescrita para a stack atual.

### Stack técnica

**Backend**
- Python 3 + Django + Django REST Framework
- PostgreSQL
- Autenticação por sessão (Django auth)

**Frontend**
- Templates Django (server-side rendering)
- Bootstrap 5
- JavaScript vanilla + HTMX para interatividade parcial

**Deploy**
- Render (web service + PostgreSQL gerenciado)

### Diferenças em relação à versão atual

| Aspecto | Legado (Django) | Atual (Next.js + FastAPI) |
|---|---|---|
| Backend | Django + DRF | FastAPI + SQLAlchemy |
| Frontend | Templates Django | Next.js 15 + React |
| Autenticação | Session-based | JWT |
| Tempo real | Polling | WebSockets |
| Deploy | Render (free tier) | Hetzner + Vercel |
| Multitenancy | Subdomínio + middleware | Subdomínio + JWT + RLS (PostgreSQL) |
| Escalabilidade | Limitada | Alta (Docker + Coolify) |

---

## 📦 Roadmap

- [x] Storefront com cardápio e checkout
- [x] Painel admin: produtos, categorias, adicionais
- [x] Painel admin: pedidos e pipeline de status
- [x] Painel admin: controle de estoque
- [x] Portal do cliente: histórico de pedidos e fidelidade
- [x] Multitenancy com subdomínio e RLS
- [ ] Notificações WhatsApp automáticas (Evolution API)
- [ ] Relatórios financeiros avançados
- [ ] Impressão de comanda (impressora térmica)
- [ ] App mobile (React Native)

---

## 💼 Sobre

Produto desenvolvido pela **[Next Change Soluções Digitais](https://nextchange.com.br)**.

Para informações comerciais, demonstração personalizada ou contato técnico:

- 📧 rocha.edllucaz@gmail.com
- 💼 [linkedin.com/in/edlucazrocha](https://linkedin.com/in/edlucazrocha)
- 🐙 [github.com/edlucaz](https://github.com/edlucaz)

---

*Código-fonte proprietário. Todos os direitos reservados. © Next Change Soluções Digitais.*
