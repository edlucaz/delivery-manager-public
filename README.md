# Delivery Manager

> Sistema SaaS de gestão de delivery com storefront público, painel administrativo e portal do cliente.

**⚠️ Este repositório é apenas documentação pública.**
O código-fonte é proprietário e mantido em repositório privado.

---

## 🚀 Demonstrações ao vivo

| Versão | Stack | Link |
|---|---|---|
| **Atual** — Next.js + FastAPI | Next.js 15 · TypeScript · TailwindCSS | 🔗 [Ver demo na Vercel](https://delivery-manager-showcase-dvbnpdhmy-edlucazs-projects.vercel.app/) |
| **Legado** — Django | Python · Django · Bootstrap | 🔗 [Ver demo no Render](https://delivery-manager-pbsj.onrender.com/) |

> As demos usam backend simulado com dados fictícios. Nenhum dado real é armazenado.
>
> **Login demo:** qualquer e-mail e senha funcionam no painel admin e portal do cliente.

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

> **📌 Nota:** adicione as imagens na pasta `screenshots/` e atualize os links acima.

---

## 🧩 Funcionalidades

### Painel Administrativo
- Dashboard com métricas em tempo real: vendas, ticket médio, pedidos por hora, top produtos
- Gestão de pedidos com atualização de status (pendente → confirmado → preparando → saiu para entrega → entregue)
- Cadastro de produtos com múltiplos tamanhos (300ml, 500ml, 700ml, 1L) e preço único
- Cadastro de categorias e adicionais
- Controle de estoque com histórico de movimentações
- Relatório financeiro básico
- Configurações da loja: horário, taxas, formas de pagamento, cores, logo

### Storefront público
- Cardápio organizado por categorias
- Modal de produto com seleção de tamanho e adicionais
- Carrinho persistente
- Checkout com endereço, forma de pagamento e troco
- Rastreamento de pedido em tempo real

### Portal do Cliente
- Cadastro e login por e-mail ou telefone
- Histórico de pedidos com detalhes
- Gerenciamento de endereços salvos
- Programa de fidelidade com pontos e cartão de selos
- Resgate de recompensas

---

## 🏗️ Arquitetura (versão atual)

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
                    PostgreSQL 16 + Redis
```

### Stack técnica

**Frontend**
- Next.js 15 + TypeScript
- TailwindCSS + shadcn/ui
- Zustand · React Hook Form + Zod · TanStack Query

**Backend**
- FastAPI (Python 3.12) + SQLAlchemy + Alembic
- PostgreSQL 16 + Redis 7
- WebSockets para pedidos em tempo real

**Infra**
- Vercel (frontend)
- Hetzner CX22 + Coolify + Docker (API e banco)
- Cloudflare R2 (imagens)
- Evolution API (WhatsApp) · Resend (e-mails) · Stripe + Pagar.me (pagamentos)

### Multitenancy
Cada estabelecimento opera em subdomínio próprio (`loja.dominio.com.br`). Isolamento completo por `tenant_id` em todas as tabelas, com Row Level Security no PostgreSQL.

---

## 🗂️ Versão legado (Django)

| Aspecto | Legado (Django) | Atual (FastAPI + Next.js) |
|---|---|---|
| Backend | Django + DRF | FastAPI + SQLAlchemy |
| Frontend | Templates Django | Next.js 15 + React |
| Auth | Session | JWT |
| Realtime | Polling | WebSockets |
| Deploy | Render | Hetzner + Vercel |
| Multitenancy | Subdomínio + middleware | Subdomínio + JWT + RLS |

---

## 📦 Roadmap

- [x] Storefront com cardápio e checkout
- [x] Painel admin: produtos, categorias, adicionais
- [x] Painel admin: pedidos e status
- [x] Painel admin: estoque
- [x] Portal do cliente: pedidos e fidelidade
- [ ] Notificações WhatsApp automáticas (Evolution API)
- [ ] Relatórios financeiros avançados
- [ ] Impressão de comanda (thermal printer)
- [ ] App mobile (React Native)

---

## 💼 Sobre

Produto desenvolvido pela **Next Change Solutions**.

Para informações comerciais ou demonstração personalizada:

- 📧 seu@email.com
- 💼 [linkedin.com/in/edlucaz](https://linkedin.com/in/edlucaz)

---

*Código-fonte proprietário. Todos os direitos reservados.*
