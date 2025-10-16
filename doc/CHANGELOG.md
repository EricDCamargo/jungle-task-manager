# 🧾 Changelog — Sistema de Gestão de Tarefas

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

## [0.2.0] - 2025-10-15

### Adicionado

-   **Estrutura das Aplicações:**
    -   Criado o projeto frontend (`apps/web`) com React, Vite e TanStack Router.
    -   Criados os projetos base do backend (`apps/api-gateway`, `apps/auth-service`, `apps/tasks-service`, `apps/notifications-service`) com NestJS.
    -   Criados os documentos iniciais do projeto (`README.md`, `DEV_ROADMAP.md`).

---

## [0.1.0] - 2025-10-15

### Adicionado

-   **Inicialização do Projeto:**
    -   Configurado o monorepo com Turborepo e PNPM Workspaces.
    -   Adicionadas as dependências de desenvolvimento na raiz (`eslint`, `prettier`, `typescript`).
    -   Criados os pacotes de configuração compartilhada para `eslint-config`, `prettier-config`, e `tsconfig`.
    -   Adicionado o arquivo `docker-compose.yml` para a infraestrutura (Postgres, RabbitMQ).
    -   Configurado o arquivo `.gitignore` inicial.
    