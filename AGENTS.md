# Repository Guidelines

## Project Structure & Module Organization
- `src/` contains the application code. Use `src/main.py` as the interactive entrypoint.
- `src/classes/` holds provider-specific components (for example `YouTube.py`, `Twitter.py`, `Tts.py`, `AFM.py`, `Outreach.py`).
- Shared utilities and configuration live in modules like `src/config.py`, `src/utils.py`, `src/cache.py`, and `src/constants.py`.
- `scripts/` contains helper workflows such as setup, preflight checks, and upload helpers.
- `docs/` contains feature documentation; `assets/` and `fonts/` contain static resources.

## Build, Test, and Development Commands
- `bash scripts/setup_local.sh`: bootstrap local development (creates `venv`, installs deps, seeds `config.json`, runs preflight).
- `source venv/bin/activate && pip install -r requirements.txt`: manual dependency install/update.
- `python3 scripts/preflight_local.py`: validate local provider/config readiness before running tasks.
- `python3 src/main.py`: start the CLI app.
- `bash scripts/upload_video.sh`: run direct script-based upload flow from repo root.

## Coding Style & Naming Conventions
- Target Python 3.12 (project requirement in `README.md`).
- Use 4-space indentation and follow existing Python conventions:
  - `snake_case` for functions/variables
  - `PascalCase` for classes
  - `UPPER_SNAKE_CASE` for constants
- Keep new business logic in focused modules under `src/`; keep provider/integration code in `src/classes/`.
- Prefer small, explicit functions and preserve existing CLI-first behavior.

## Testing Guidelines
- There is currently no enforced automated test suite or coverage threshold.
- Minimum validation for changes:
  - Run `python3 scripts/preflight_local.py`
  - Smoke-test impacted flows via `python3 src/main.py`
- When adding tests, place them in a top-level `tests/` directory with names like `test_<module>.py`.

## Commit & Pull Request Guidelines
- Follow the existing commit style: imperative summaries like `Fix ...`, `Update ...`, optionally with issue refs (for example `(#128)`).
- Open PRs against `main`.
- Link each PR to an issue, keep scope to one feature/fix, and use a clear title + description.
- Mark not-ready PRs with `WIP` and remove it when ready for review.

## Security & Configuration Tips
- Treat `config.json` as environment-specific; do not commit real API keys or private profile paths.
- Start from `config.example.json` and prefer environment variables where supported (for example `GEMINI_API_KEY`).

## Referências externas para design e interação (17/11/2026)

- TasteSkill (https://www.tasteskill.dev/): método de revisão de direção visual, tipografia, espaçamento e composição autoral, nunca template a copiar.
- Transitions.dev (https://transitions.dev/): fonte de microinterações CSS quando houver interface web; `prefers-reduced-motion`, teclado, foco e contraste obrigatórios.
- React Bits (https://reactbits.dev/): NÃO APLICÁVEL ao CLI Python; só reavaliar caso seja criada uma interface React.
- RiseClub (https://riseclub.tech/): observar organização de aprendizagem/comunidade e conteúdo editorial; jamais copiar conteúdo, interface, marcas ou dados.
- Escopo local: Projeto Python/CLI de geração de mídia: preservar fluxos dos provedores e configurações; React Bits não se aplica ao núcleo Python. Para futura UI web, avaliar separadamente licenças, performance e acessibilidade.
- Adoção apenas quando resolver necessidade real: branch/PR pequeno, verificação responsiva 390/1440 (para web), motion reduzido, sem mudanças em banco, DNS, credenciais, funis ou produção decorrentes deste documento.
- Não executar instaladores/skills/scripts externos automaticamente. Preservar instruções mais específicas, licenças e testes do projeto.
