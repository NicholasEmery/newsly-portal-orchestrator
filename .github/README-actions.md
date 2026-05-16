# GitHub Actions - orchestrator

Responsabilidades:

- Atualizar submodules (`frontend`/`backend`) quando receber `repository_dispatch` do repositório de origem.
- Fazer deploy via `docker compose` em runner `self-hosted` (label `deploy`).

Requisitos operacionais:

- Runners self-hosted: pelo menos um runner com labels `self-hosted` e `deploy`, com Docker instalado e capaz de executar `docker compose`.
- Secrets: `TEAMS_WEBHOOK_URL` (opcional) para notificações no `deploy.yml`.

Permissões e tokens:

- Para permitir que `frontend` e `backend` chamem o orchestrator, adicione `ORCHESTRATOR_PAT` nos secrets desses repositórios (valor = token com permissão para `repo` e `repo:dispatch` no repositório `newsly-portal-orchestrator`).

Como validar localmente:

- O workflow `deploy.yml` dispara em push para `main`.
- Os workflows `update-*-submodule.yml` reagem a `repository_dispatch` e atualizam submodules.

Commit readiness:

- Os arquivos de workflows já foram atualizados; use o script no nível do workspace `scripts/commit_github_folders.sh` para criar commits prontos em cada repo.
