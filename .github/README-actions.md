# GitHub Actions - orchestrator

Responsabilidades:

- Atualizar submodules (`frontend`/`backend`) quando receber `repository_dispatch` do repositório de origem.
- Fazer deploy via `docker compose` em runner `self-hosted` (label `deploy`).
- Notificar no Telegram depois que o deploy do backend ou do frontend terminar, usando o GitHub SDK para validar o resultado e montar o diagnóstico.

Requisitos operacionais:

- Runners self-hosted: pelo menos um runner com labels `self-hosted` e `deploy`, com Docker instalado e capaz de executar `docker compose`.
- Secrets: `TELEGRAM_BOT_TOKEN` e `TELEGRAM_CHAT_ID` para o workflow `notify-deployment.yml`; `TEAMS_WEBHOOK_URL` segue opcional para outras notificações do deploy.

Permissões e tokens:

- Para permitir que `frontend` e `backend` chamem o orchestrator, adicione `ORCHESTRATOR_PAT` nos secrets desses repositórios (valor = token com permissão para `repo` e `repo:dispatch` no repositório `newsly-portal-orchestrator`).

Como validar localmente:

- O workflow `deploy.yml` dispara em push para `main`.
- O workflow `notify-deployment.yml` dispara automaticamente após `Deploy Backend` ou `Deploy Frontend` concluir, independentemente de sucesso ou falha.
- Os workflows `update-*-submodule.yml` reagem a `repository_dispatch` e atualizam submodules.

Commit readiness:

- Os arquivos de workflows já foram atualizados; use o script no nível do workspace `scripts/commit_github_folders.sh` para criar commits prontos em cada repo.
