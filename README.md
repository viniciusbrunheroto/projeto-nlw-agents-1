# 🧠 NLW Agents

O projeto NLW Agents é uma aplicação full-stack desenvolvida durante o evento Next Level Week (NLW) da Rocketseat. Ele demonstra a construção de um sistema que integra funcionalidades de backend e frontend, utilizando tecnologias modernas para criar uma experiência interativa e eficiente. O foco principal é a criação de "agentes" que podem interagir com modelos de linguagem, utilizando embeddings vetoriais para busca de contexto.

## 🚀 Tecnologias Utilizadas

Este projeto é dividido em duas partes principais: o Backend (servidor) e o Frontend (aplicação web).

### Backend (server)

- **Node.js**
- **TypeScript** – Tipagem estática e segura para aplicações em escala
- **Fastify** – Um framework web rápido e de baixo overhead, focado em fornecer a melhor experiência de desenvolvedor com plugins poderosos.
- **PostgreSQL** – Um poderoso sistema de banco de dados relacional de código aberto
- **pgvector** – Extensão para PostgreSQL que permite armazenar e consultar embeddings vetoriais, essencial para funcionalidades de IA
- **Drizzle ORM** – Um ORM Typescript moderno e type-safe para banco de dados relacionais
- **@google/genai** – SDK para interação com modelos de IA generativa do Google (e.g, Gemini)


### Front-end (server)
- **React 19** – Com suporte a novas features como Server Actions e use()
- **TypeScript** – Tipagem estática e segura para aplicações em escala
- **Vite** – Empacotador moderno e super rápido
- **Tailwind CSS v4** – Estilização utilitária e eficiente
- **React Router DOM** – Gerenciamento de rotas no frontend
- **TanStack React Query** – Gerenciamento assíncrono e cache de dados
- **Radix UI** – Componentes acessíveis e com foco em usabilidade
- **shadcn/ui** – Conjunto de componentes UI baseados em Tailwind + Radix
- **Lucide React** – Ícones modernos e personalizáveis

## 📦 Como rodar o projeto

### Pré-requisitos

- [Node.js](https://nodejs.org/)
- [pnpm](https://pnpm.io/) (ou npm/yarn)
- [Docker](https://www.docker.com/get-started/) e [Docker Compose](https://docs.docker.com/compose/install/) (para o banco de dados PostgreSQL)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

### Instalação

1.  **Clone o repositório:**

    ```bash
    git clone <URL_DO_SEU_REPOSITORIO>
    cd nlw-agents
    ```

2.  **Configuração do Banco de Dados (PostgreSQL com pgvector via Docker Compose):**

    Navegue até o diretório `server` e inicie o contêiner do banco de dados. O `docker-compose.yml` já está configurado para usar a imagem `pgvector/pgvector` e inicializar a extensão `vector`.

    ```bash
    cd server
    docker compose up -d
    ```

    Isso iniciará um contêiner PostgreSQL na porta `5432`. Você pode verificar se o contêiner está rodando com `docker ps`.

3.  **Configuração do Backend:**

    Ainda no diretório `server`:

    a.  **Instale as dependências:**

        ```bash
        npm install
        # ou yarn install
        ```

    b.  **Crie o arquivo de variáveis de ambiente:**

        Crie um arquivo `.env` na raiz do diretório `server` com base no `.env.example` (se existir, caso contrário, crie-o manualmente). Você precisará configurar as seguintes variáveis:

        ```env
        DATABASE_URL="postgresql://docker:docker@localhost:5432/agents"
        GOOGLE_API_KEY="SUA_CHAVE_API_DO_GOOGLE_GEMINI"
        # Outras variáveis de ambiente que seu projeto possa precisar
        ```

        *   `DATABASE_URL`: A URL de conexão com o banco de dados PostgreSQL. A URL padrão para o setup do Docker Compose é `postgresql://docker:docker@localhost:5432/agents`.
        *   `GOOGLE_API_KEY`: Sua chave de API para acessar os modelos generativos do Google (e.g., Gemini).

    c.  **Execute as migrações do banco de dados:**

        ```bash
        npm run db:migrate
        ```

        Isso aplicará as migrações do Drizzle ORM, criando as tabelas necessárias no seu banco de dados.

    d.  **Popule o banco de dados (opcional):**

        Se houver dados iniciais para o projeto, você pode executar o script de seed:

        ```bash
        npm run db:seed
        ```

    e.  **Inicie o servidor de desenvolvimento:**

        ```bash
        npm run dev
        # ou para produção: npm start
        ```

        O servidor estará disponível em `http://localhost:3333` (ou na porta configurada no seu `.env`).

4.  **Configuração do Frontend:**

    Abra um novo terminal, navegue até o diretório `web`:

    ```bash
    cd ../web
    ```

    a.  **Instale as dependências:**

        ```bash
        npm install
        # ou yarn install
        ```

    b.  **Inicie o servidor de desenvolvimento:**

        ```bash
        npm run dev
        ```

        A aplicação frontend estará disponível em `http://localhost:5173` (ou na porta indicada pelo Vite).

## Licença

Este projeto está licenciado sob a licença ISC. Consulte o arquivo `LICENSE` para mais detalhes.


