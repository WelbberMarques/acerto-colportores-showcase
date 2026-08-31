![platform](https://img.shields.io/badge/platform-Web-blue)
![Next.js](https://img.shields.io/badge/Next.js-15-black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178c6)
![license](https://img.shields.io/badge/license-Proprietary-lightgrey)
![status](https://img.shields.io/badge/status-Em%20produção-brightgreen)
![author](https://img.shields.io/badge/author-Welbber%20Marques-orange)

# Acerto Colportores

Sistema web de gestão financeira para equipes de colportagem (vendas porta a porta de literatura), desenvolvido para a **SELS USB**. Substitui um fluxo manual de acerto de contas por um painel único, em tempo real, com controle de permissões por papel.

> Este repositório é uma vitrine do projeto. O código-fonte é privado (sistema de produção com integrações internas e dados sensíveis de terceiros).

## O que o sistema faz

- **Acerto de contas por colportor**: concilia vendas, cartões, notas fiscais e pagamentos, gerando o fechamento financeiro de cada colportor.
- **Painel em tempo real**: dashboards e listas de pendências que atualizam sozinhos via WebSocket, sem precisar recarregar a página.
- **Controle de acesso por papel**: administradores/equipe interna têm acesso completo; assistentes de equipe veem uma versão somente leitura, escopada à própria equipe.
- **Geração de PDF**: comprovantes e relatórios de cotas exportados diretamente do navegador.
- **Sincronização com sistema legado**: integração server-to-server com um ERP legado (SQL Server) para importar vendas e saldos automaticamente.
- **PWA**: instalável em celular/desktop, com ícones e manifest próprios.

## Stack técnica

| Camada | Tecnologia |
|---|---|
| Frontend/Backend | Next.js 15 (App Router), React, TypeScript |
| Autenticação e banco em tempo real | Supabase (Auth, Postgres, Realtime, Row-Level Security) |
| Integração legado | Node.js + `mssql` (SQL Server) |
| Infraestrutura | VPS própria (Oracle Cloud), Caddy (HTTPS automático), Cloudflare (proteção DDoS) |
| Deploy | PM2, deploy manual controlado |

## Segurança

- Content-Security-Policy, HSTS, e demais headers de segurança configurados manualmente.
- Rate limiting por IP em todas as rotas de API.
- Row-Level Security no Supabase, com políticas por equipe.
- Erros sanitizados antes de chegar ao cliente (nunca vaza detalhe de infraestrutura interna).
- Tokens dedicados e isolados para cada integração servidor-a-servidor.

## Autoria

Projeto individual, desenvolvido e mantido por **Welbber Marques** — da concepção do banco de dados até a infraestrutura de produção (VPS, DNS, HTTPS, DDoS).
