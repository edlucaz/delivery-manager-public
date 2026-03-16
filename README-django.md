# 🛵 Delivery Manager — Versão Legado (Django)

> Sistema SaaS de gestão de delivery — versão MVP inicial, desenvolvida com Django e Bootstrap.

Este repositório é uma **vitrine pública** do projeto. O código-fonte é proprietário e mantido em repositório privado.

---

### 📂 Versões disponíveis

[![Versão Atual — Next.js + FastAPI](https://img.shields.io/badge/🟢_Versão_Atual-Next.js_+_FastAPI-black?style=for-the-badge&logo=next.js)](./README.md)
[![Versão Legado — Django](https://img.shields.io/badge/🗂️_Versão_Legado-Django-092E20?style=for-the-badge&logo=django&logoColor=white)](./README-django.md)

---

[![Python](https://img.shields.io/badge/Python_3-3776AB?logo=python&logoColor=white)](https://python.org)
[![Django](https://img.shields.io/badge/Django-092E20?logo=django&logoColor=white)](https://djangoproject.com)
[![Bootstrap](https://img.shields.io/badge/Bootstrap_5-7952B3?logo=bootstrap&logoColor=white)](https://getbootstrap.com)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)](https://postgresql.org)

---

## 🖥️ Ambientes disponíveis

> ⚠️ **Todos os ambientes utilizam backend simulado com dados fictícios.** Nenhum dado real é processado ou armazenado.

| | **Versão Atual — Next.js + FastAPI** | **Versão Legado — Django** |
|---|---|---|
| **Stack** | Next.js 15 · TypeScript · FastAPI · PostgreSQL | Python 3 · Django · Bootstrap · PostgreSQL |
| **Deploy** | Vercel + Hetzner | Render |
| **Acesso** | [🔗 Abrir na Vercel](https://delivery-manager-showcase-dvbnpdhmy-edlucazs-projects.vercel.app/) | [🔗 Abrir no Render](https://delivery-manager-pbsj.onrender.com/) |
| **Documentação** | [📄 README Next.js](./README.md) | ← *você está aqui* |

> ⏳ O Render pode levar ~30s para iniciar na primeira requisição (free tier).

### 🔑 Credenciais de acesso

| Área | URL | Credenciais |
|---|---|---|
| Painel Administrativo | `/login` | Qualquer e-mail + qualquer senha |
| Portal do Cliente | `/cliente/login` | Qualquer e-mail/telefone + qualquer senha |
| Storefront | `/storefront` | ✅ Sem login — acesso público |

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

---

## 🧩 Funcionalidades

### Painel Administrativo
- Dashboard com métricas: vendas, ticket médio, pedidos por hora, top produtos
- Gestão de pedidos com pipeline de status: `pendente → confirmado → preparando → saiu para entrega → entregue`
- Cadastro de produtos com múltiplos tamanhos e preço único
- Cadastro de categorias e adicionais
- Controle de estoque com histórico de movimentações
- Relatório financeiro básico
- Configurações da loja: horário, taxas, formas de pagamento, cores, logo

### Storefront público
- Cardápio organizado por categorias com busca
- Modal de produto com seleção de tamanho e adicionais
- Carrinho persistente com edição e duplicação de itens
- Checkout com endereço, forma de pagamento e troco
- Integração PIX com QR Code ou chave
- Rastreamento de pedido em tempo real

### Portal do Cliente
- Cadastro e login por e-mail ou telefone
- Histórico de pedidos com detalhes
- Gerenciamento de endereços salvos
- Programa de fidelidade com pontos e cartão de selos
- Resgate de recompensas

---

## 🏗️ Arquitetura

```
Cliente final         Admin / Gerente        Cliente logado
     │                      │                      │
     ▼                      ▼                      ▼
 Storefront             Dashboard              Portal Cliente
     └──────────────────────┼──────────────────────┘
                            │
                    Django (Render)
                            │
                       PostgreSQL
```

### Stack técnica

**Backend**
- Python 3 + Django + Django REST Framework
- PostgreSQL
- Autenticação por sessão (Django auth)
- Polling para atualização de status de pedidos

**Frontend**
- Templates Django (server-side rendering)
- Bootstrap 5
- JavaScript vanilla + HTMX para interatividade parcial

**Deploy**
- Render (web service + PostgreSQL gerenciado — free tier)

---

## 🔄 Por que foi reescrito?

Esta versão validou o produto e as funcionalidades principais. A migração para Next.js + FastAPI foi motivada por:

| Limitação no Django | Solução na versão atual |
|---|---|
| SSR dificulta UX reativa | React com App Router e TanStack Query |
| Polling consome recursos | WebSockets nativos |
| Session auth não escala bem | JWT stateless |
| Deploy free tier instável | Hetzner + Coolify + Docker |
| Multitenancy via middleware | RLS no PostgreSQL |

---

## 💼 Sobre

Produto desenvolvido pela **[Next Change Soluções Digitais](https://nextchange.com.br)**.

Para informações comerciais, demonstração personalizada ou contato técnico:

- 📧 rocha.edllucaz@gmail.com
- 💼 [linkedin.com/in/edlucazrocha](https://linkedin.com/in/edlucazrocha)
- 🐙 [github.com/edlucaz](https://github.com/edlucaz)

---

*Código-fonte proprietário. Todos os direitos reservados. © Next Change Soluções Digitais.*
