# Newsly Orchestrator 📰

Este repositório é o **ponto central** do projeto **Newsly**, responsável por orquestrar os repositórios [newsly-portal-frontend](../newsly-portal-frontend) e [newsly-portal-backend](../newsly-portal-backend).  
Ele organiza a integração entre frontend e backend, além de gerenciar pipelines de **CI/CD** com GitHub Actions e outras automações.

---

## 📦 Estrutura

- `frontend/` → Submódulo do repositório de frontend (Next.js, Tailwind CSS, Typescript)  
- `backend/` → Submódulo do repositório de backend (NestJS, Prisma, Banco de Dados)  
- `.github/workflows/` → Pipelines de CI/CD e automações  

---

## 🚀 Objetivo

Fornecer um ponto único de **orquestração**, garantindo:
- Integração entre frontend e backend  
- Fluxos de **build, testes e deploy** automatizados  
- Versionamento centralizado  
- Facilidade para novos contribuidores iniciarem no projeto  

---

## 🛠️ Tecnologias

- **Next.js**, **Tailwind CSS**, **Typescript** (frontend)  
- **NestJS**, **Prisma**, **MongoDB** (backend)  
- **Docker** para containerização  
- **GitHub Actions** para CI/CD  
- **ESLint/Prettier** para padronização de código  

---

## 📚 Como usar

### Clonar com submódulos
```bash
git clone --recurse-submodules git@github.com:SEU_USUARIO/newsly-portal-orchestrator.git
cd newsly-portal-orchestrator
```

### Atualizar submódulos
```bash
git submodule update --remote --merge
```

---

## 🐳 Docker

### Desenvolvimento Local
```bash
# Build das imagens
docker compose build

# Subir containers
docker compose up

# Ou tudo junto
docker compose up --build
```

### Comandos úteis
```bash
# Acessar shell do container
docker compose exec frontend sh
docker compose exec backend sh

# Ver logs
docker compose logs frontend
docker compose logs backend

# Parar containers
docker compose down
```

---

## 🔄 CI/CD

Os workflows de CI/CD estão definidos em `.github/workflows/`.  
Eles incluem:
- Build e testes do frontend e backend  
- Deploy automatizado  
- Checks de qualidade de código  
- Integração contínua para PRs  

---

## 📖 Licença

Este projeto está sob a licença. [**CLIQUE AQUI**]()
