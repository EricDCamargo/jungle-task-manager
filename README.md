# 🚀 Sistema de Gestão de Tarefas Colaborativo

Um sistema de gestão de tarefas full-stack, desenvolvido como parte do Desafio de Desenvolvedor Full-Stack Júnior para a **Jungle Gaming**. A aplicação é construída com uma arquitetura de microserviços orientada a eventos, utilizando um monorepo para gerenciar o código de forma unificada.

O objetivo é criar uma plataforma escalável e de fácil manutenção, com autenticação segura, atualizações em tempo real via WebSockets e uma interface de usuário moderna e responsiva.

---

## 📜 Índice

- [✨ Funcionalidades Principais](#-funcionalidades-principais)
- [🛠️ Stack Tecnológica](#️-stack-tecnológica)
- [📂 Estrutura do Monorepo](#-estrutura-do-monorepo)
- [🚀 Como Começar](#-como-começar)
- [📜 Scripts Disponíveis](#-scripts-disponíveis)
- [🗺️ Roteiro de Desenvolvimento](#️-roteiro-de-desenvolvimento)
- [📄 Licença](#-licença)

---

## ✨ Funcionalidades Principais

- **🔐 Autenticação Segura:** Microserviço de autenticação centralizado com JWT (Access & Refresh Tokens) e hashing de senhas com `bcrypt`.
- **📝 Gestão de Tarefas:** CRUD completo para tarefas, com campos para prioridade, prazo, status e atribuição a múltiplos usuários.
- **💬 Comentários e Histórico:** Funcionalidade para adicionar comentários em tarefas e um log de auditoria simplificado para registrar alterações.
- **📡 Notificações em Tempo Real:** Atualizações instantâneas via WebSocket para atribuições de tarefas, novos comentários e mudanças de status.
- **🐇 Arquitetura Orientada a Eventos:** Comunicação assíncrona entre microserviços utilizando **RabbitMQ** como message broker.
- **🐳 Ambiente Containerizado:** Todo o ecossistema (aplicações, banco de dados, broker) é orquestrado com **Docker e Docker Compose**.

---

## 🛠️ Stack Tecnológica

| Categoria        | Tecnologias                                                                                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Monorepo**     | [Turborepo](https://turbo.build/repo), [pnpm](https://pnpm.io/)                                                                                            |
| **Frontend**     | [React](https://react.dev/), [TanStack Router](https://tanstack.com/router), [shadcn/ui](https://ui.shadcn.com/), [Tailwind CSS](https://tailwindcss.com/) |
| **Backend**      | [NestJS](https://nestjs.com/), [TypeORM](https://typeorm.io/), [RabbitMQ](https://www.rabbitmq.com/), [PostgreSQL](https://www.postgresql.org/)            |
| **Autenticação** | JWT, `bcrypt`                                                                                                                                              |
| **Dev Tools**    | Docker & Compose, ESLint, Prettier                                                                                                                         |
| **Documentação** | Swagger / OpenAPI                                                                                                                                          |

---

## 📂 Estrutura do Monorepo

```sh
/
├── apps/
│   ├── web/                  # Aplicação Frontend (React + Vite)
│   ├── api-gateway/          # Ponto de Entrada da API (NestJS HTTP + WebSocket)
│   ├── auth-service/         # Microserviço de Autenticação
│   ├── tasks-service/        # Microserviço de Tarefas
│   └── notifications-service/  # Microserviço de Notificações
│
├── packages/
│   ├── types/                # Tipos TypeScript compartilhados
│   ├── utils/                # Funções utilitárias compartilhadas
│   ├── eslint-config/        # Configuração compartilhada do ESLint
│   ├── prettier-config/      # Configuração compartilhada do Prettier
│   └── tsconfig/             # Configurações base do TypeScript
│
├── .gitignore
├── docker-compose.yml
├── package.json
└── turbo.json
```

---

## 🚀 Como Rodar o Projeto

### Pré-requisitos

- [Node.js](https://nodejs.org/) (v22.20+ ou superior)
- [pnpm](https://pnpm.io/) (`npm install -g pnpm`)
- [Docker](https://www.docker.com/) e [Docker Compose](https://docs.docker.com/compose/)
- [Git](https://git-scm.com/)

### Instalação e Execução

1.  **Clone o repositório:**

    ```bash
    git clone https://github.com/SEU-USUARIO/jungle-task-manager.git
    cd jungle-task-manager
    ```

2.  **Instale as dependências:**
    Este comando instalará todas as dependências de todos os projetos do monorepo.

    ```bash
    pnpm install
    ```

3.  **Configure as Variáveis de Ambiente:**
    Cada serviço na pasta `apps/` contém um arquivo `.env.example`. Crie uma cópia chamada `.env` para cada um e ajuste os valores se necessário (os valores padrão já funcionam com o `docker-compose.yml`).

    ```bash
    # Exemplo para o auth-service
    cp apps/auth-service/.env.example apps/auth-service/.env
    ```

4.  **Inicie toda a stack com Docker Compose:**
    Este comando irá construir as imagens e iniciar todos os contêineres em modo de desenvolvimento.

    ```bash
    docker-compose up --build
    ```

    - **Interface Web (Frontend)** estará disponível em `http://localhost:3000`
    - **API Gateway (Backend)** estará disponível em `http://localhost:3001`
    - **Painel do RabbitMQ** estará disponível em `http://localhost:15671`

---

## 📜 Scripts Disponíveis

Você pode executar os seguintes scripts a partir da raiz do projeto:

| Comando                | Descrição                                              |
| ---------------------- | ------------------------------------------------------ |
| `pnpm turbo run dev`   | Inicia todas as aplicações em modo de desenvolvimento. |
| `pnpm turbo run build` | Compila todas as aplicações para produção.             |
| `pnpm turbo run lint`  | Executa o ESLint em todos os pacotes e aplicações.     |
| `pnpm format`          | Formata todo o código com o Prettier.                  |

---

## 🗺️ Roteiro de Desenvolvimento

O plano detalhado de cada fase está documentado no arquivo `doc/DEV_ROADMAP.md`.

| Fase | Foco                       | Status          |
| :--- | :------------------------- | :-------------- |
| 0    | Inicialização do Projeto   | ✅ Concluído    |
| 1    | Serviço de Autenticação    | 🚧 Em Andamento |
| 2    | API Gateway                | ⏳ Planejado    |
| 3    | Serviço de Tarefas         | ⏳ Planejado    |
| 4    | Serviço de Notificações    | ⏳ Planejado    |
| 5    | Interface do Usuário (Web) | ⏳ Planejado    |
| 6    | Finalização e Documentação | ⏳ Planejado    |

---

## 📄 Licença

Este projeto é licenciado sob a Licença MIT. Veja o arquivo [`LICENSE`](https://github.com/EricDCamargo/jungle-task-manager/blob/main/LICENSE) para mais detalhes.

---

**Autor:** Eric Dellai Camargo
**Projeto:** Desafio Full-Stack Júnior @ Jungle Gaming
**Última Atualização:** 15 de Outubro de 2025
