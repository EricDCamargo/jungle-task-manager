# 🗺️ Plano de Desenvolvimento — Desafio Full-stack Júnior

> Este documento define o roteiro de desenvolvimento para o desafio, dividido em fases para garantir uma entrega clara e organizada.

---

## 🧱 FASE 0 — Inicialização do Projeto e Ferramentas

**Objetivo:** Estabelecer a base sólida do monorepo com as ferramentas corretas.

- [x] ✅ **FEITO:** Criar monorepo com `pnpm + Turborepo`.
- [x] ✅ **FEITO:** Inicializar repositório Git e configurar `.gitignore`.
- [x] ✅ **FEITO:** Configurar `package.json` da raiz e dependências de desenvolvimento.
- [x] ✅ **FEITO:** Configurar pacotes compartilhados de ESLint, Prettier e TypeScript.
- [x] ✅ **FEITO:** Criar o `docker-compose.yml` e iniciar a infraestrutura (Postgres + RabbitMQ).
- [x] ✅ **FEITO:** Criar os projetos base para o frontend (`web`) e todos os microserviços.

---

## 🔐 FASE 1 — Serviço de Autenticação (`auth-service`)

**Objetivo:** Construir o microserviço principal responsável pela identidade e segurança dos usuários.

- [ ] 🚧 **EM ANDAMENTO:** Configurar a conexão com o banco de dados PostgreSQL usando TypeORM.
- [ ] 🧩 **A FAZER:** Implementar a entidade `User` para representar a tabela de usuários.
- [ ] 🧩 **A FAZER:** Criar os tipos de autenticação compartilhados no pacote `@jungle/types`.
- [ ] 🧩 **A FAZER:** Implementar a lógica de registro de usuário, incluindo o hash de senha com `bcrypt`.
- [ ] 🧩 **A FAZER:** Implementar a lógica de login para gerar os tokens JWT (`accessToken` e `refreshToken`).
- [ ] 🧩 **A FAZER:** Implementar o endpoint para dar "refresh" no `accessToken` usando o `refreshToken`.
- [ ] 🧩 **A FAZER:** Criar os DTOs (Data Transfer Objects) e adicionar validação de entrada com `class-validator`.

---

## 📡 FASE 2 — API Gateway (`api-gateway`)

**Objetivo:** Criar o ponto de entrada único que protege e direciona todas as requisições.

- [ ] 🧩 **A FAZER:** Configurar o `api-gateway` para se comunicar com o `auth-service` via RabbitMQ.
- [ ] 🧩 **A FAZER:** Implementar um JWT Guard para proteger rotas que exigem autenticação.
- [ ] 🧩 **A FAZER:** Expor os endpoints de `/auth/register`, `/auth/login` e `/auth/refresh`, redirecionando as chamadas para o `auth-service`.
- [ ] 🧩 **A FAZER:** Configurar o `Swagger/OpenAPI` na rota `/api/docs`.
- [ ] 🧩 **A FAZER:** Implementar o `rate limiting` (limite de requisições por segundo).
- [ ] 🧩 **A FAZER:** Criar o WebSocket Gateway que será usado para as notificações.

---

## 📝 FASE 3 — Serviço de Tarefas (`tasks-service`)

**Objetivo:** Desenvolver o serviço que gerencia toda a lógica de negócio relacionada a tarefas, comentários e histórico.

- [ ] 🧩 **A FAZER:** Conectar o serviço ao banco de dados.
- [ ] 🧩 **A FAZER:** Implementar as entidades do TypeORM: `Task`, `Comment`, `TaskHistory`.
- [ ] 🧩 **A FAZER:** Desenvolver a lógica CRUD (Criar, Ler, Atualizar, Deletar) para tarefas.
- [ ] 🧩 **A FAZER:** Implementar a lógica para atribuir tarefas a múltiplos usuários.
- [ ] 🧩 **A FAZER:** Implementar a criação e listagem de comentários em uma tarefa.
- [ ] 🧩 **A FAZER:** Ao criar/atualizar/comentar, publicar os eventos (`task.created`, `task.updated`, `task.comment.created`) no RabbitMQ.

---

## 🔔 FASE 4 — Serviço de Notificações (`notifications-service`)

**Objetivo:** Construir o serviço que consome os eventos e envia atualizações em tempo real.

- [ ] 🧩 **A FAZER:** Conectar o serviço ao banco de dados.
- [ ] 🧩 **A FAZER:** Implementar a entidade `Notification`.
- [ ] 🧩 **A FAZER:** Criar um consumidor RabbitMQ para ouvir os eventos publicados pelo `tasks-service`.
- [ ] 🧩 **A FAZER:** Ao receber um evento, persistir a notificação no banco de dados.
- [ ] 🧩 **A FAZER:** Enviar a notificação em tempo real para o `api-gateway` via WebSocket.

---

## 🌐 FASE 5 — Interface do Usuário (`web`)

**Objetivo:** Criar uma interface moderna e funcional para os usuários interagirem com o sistema.

- [ ] 🧩 **A FAZER:** Configurar `shadcn/ui` e `Tailwind CSS`.
- [ ] 🧩 **A FAZER:** Construir as páginas/modais de Login e Registro.
- [ ] 🧩 **A FAZER:** Construir a página principal que lista as tarefas, com filtros e busca.
- [ ] 🧩 **A FAZER:** Construir a página de detalhes da tarefa, mostrando comentários e outras informações.
- [ ] 🧩 **A FAZER:** Conectar a aplicação ao WebSocket do `api-gateway` para receber notificações.
- [ ] 🧩 **A FAZER:** Gerenciar o estado de autenticação com `Zustand` ou `Context API`.
- [ ] 🧩 **A FAZER:** Implementar validação de formulários com `react-hook-form` e `zod`.
- [ ] 🧩 **A FAZER:** Adicionar feedback visual (skeleton loaders, toast notifications).

---

## 🚀 FASE 6 — Finalização e Documentação

**Objetivo:** Revisar o projeto, garantir que tudo está funcionando em conjunto e finalizar a documentação.

- [ ] 🧩 **A FAZER:** Revisar e finalizar a configuração dos `Dockerfiles` de cada serviço.
- [ ] 🧩 **A FAZER:** Testar o fluxo completo com `docker-compose up`.
- [ ] 🧩 **A FAZER:** Escrever a documentação final no `README.md`, incluindo o diagrama da arquitetura.

---

**Autor:** Eric Dellai Camargo
**Projeto:** Desafio Full-Stack Júnior @ Jungle Gaming
**Última Atualização:** 15 de Outubro de 2025
