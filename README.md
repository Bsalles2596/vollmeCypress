# VollMe Cypress

Projeto monorepo de automação de testes E2E com Cypress para uma aplicação de clínica médica.

## Visão geral

Este repositório reúne três camadas principais:

- `server/` - API backend em Node.js + Express + TypeORM + TypeScript.
- `web/` - frontend React com TypeScript, MUI, Styled Components e Recharts.
- `cypress/` - suíte de testes end-to-end com Cypress e relatórios Mochawesome.

O fluxo principal de validação envolve a aplicação web (`localhost:3000`) consumindo a API backend (`localhost:8080`) e os testes Cypress executando cenários de login, cadastro e dashboard.

## Tecnologias

- Node.js
- npm
- React + TypeScript
- Express
- TypeORM
- Cypress
- Mochawesome
- MUI
- Styled Components
- Recharts

## Estrutura do repositório

- `cypress.config.js` - configuração global do Cypress.
- `cypress/e2e/` - arquivos de teste E2E.
- `cypress/results/` - relatórios gerados pelo Mochawesome.
- `server/` - backend da aplicação.
- `web/` - frontend React.
- `.github/workflows/cypress.yml` - pipeline de CI para execução dos testes.

## Pré-requisitos

- Node.js 16.x ou superior
- npm

## Instalação

No diretório raiz do projeto:

```bash
npm install
```

Em seguida, instale dependências em cada subprojeto:

```bash
cd server && npm install
cd ../web && npm install
```

## Executando localmente

### Iniciar o backend

No diretório `server/`:

```bash
cd server
npm start
```

O backend será iniciado em `http://localhost:8080`.

### Iniciar o frontend

No diretório `web/`:

```bash
cd web
npm start
```

O frontend será iniciado em `http://localhost:3000`.

### Executar testes Cypress

No diretório raiz do projeto:

- Abrir o Cypress com viewport de tablet:

```bash
npm run cy:open:tablet
```

- Executar testes em modo headless:

```bash
npx cypress run
```

- Executar testes em modo tablet:

```bash
npm run test:tablet
```

- Executar apenas no navegador Edge:

```bash
npm run test:browser:edge
```

## Configuração do Cypress

A configuração do Cypress está em `cypress.config.js`.

- `baseUrl`: `http://localhost:3000/`
- API de autenticação: `http://localhost:8080/auth/login`
- API de clínicas: `http://localhost:8080/clinica`
- API de especialistas: `http://localhost:8080/especialista`
- Timeout padrão de comandos: `60000`
- Relatórios: Mochawesome em `cypress/results`

Há também um arquivo de exemplo de variáveis de ambiente em `cypress.env.example.json`.

## Pipeline CI

O GitHub Actions definido em `.github/workflows/cypress.yml` executa:

1. Checkout do repositório.
2. Instalação de dependências do backend e frontend.
3. Inicialização do backend em `localhost:8080`.
4. Inicialização do frontend em `localhost:3000`.
5. Execução dos testes Cypress selecionados.

O workflow é disparado em pushes para a branch `testes`.

## Scripts úteis

### Raiz

- `npm run cy:open:tablet` - abre Cypress em modo interativo com viewport tablet.
- `npm run lint` - valida o código de Cypress com ESLint.
- `npm run lint:fix` - corrige automaticamente problemas detectados pelo ESLint.

### Backend (`server/`)

- `npm start` - inicia o servidor com `tsc-watch`.
- `npm run compile` - compila o TypeScript.
- `npm test` - executa testes Jest.
- `npm run test:watch` - executa Jest em modo watch.
- `npm run test:coverage` - gera relatório de cobertura.

### Frontend (`web/`)

- `npm start` - inicia a aplicação React.
- `npm run build` - cria build de produção.
- `npm test` - executa os testes do Create React App.
- `npm run api` - inicia um servidor `json-server` usando `web/db.json` na porta `8080`.

## Observações

- Para rodar a suíte E2E corretamente, o backend deve estar disponível em `localhost:8080` e o frontend em `localhost:3000`.
- O projeto privilegia validação automatizada de fluxo de clínica, login e dashboard.

---

Se precisar de ajuda para executar algum comando ou configurar o ambiente, posso detalhar qualquer etapa adicional.